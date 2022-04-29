---
layout: default
title: React HOC and Render Props
parent: 2020
nav_order: 50
---

# Intro

HOCs (Higher Order Components) and Render Props are both techniques in React for handle cross-cutting concerns and making components more reusable. While Hooks from React v16.8+ largely replaced these patterns as they generally provide better reusability and allow easier sharing of data across many levels of the component tree when combined with the Context API, it is still useful to know these patterns because:

1. Many third-party libraries expose their functionality via HOCs and Render Props
2. You might still want to combine these patterns with Context or Hooks in some cases

## Contrived Example

Suppose you want to display the current date and time in ISO format on your React application and you have built a component like this:

```tsx
export function CurrentDateTime(): JSX.Element {
  return <span>{new Date().toISOString()}</span>;
}
```

Let's imagine some scenarios where you now have some new requirements for the app such as:

1. Other components need to fetch the current date and time, to display it in different format or use for some other computing purpose
2. You want to display ISO string of _any_ date and time, not just the current date

In the first scenario, fetching current date and time has now become somewhat of a cross-cutting concern and you probably don't want to slather `new Date()` all over your app.

In the second scenario, you probably want to create a new component that takes in a date time as a prop and deals only with rendering it on the UI.

In either cases, what you might want to do is separate the logic of 'fetching the current date' and 'rendering date and time in ISO string' that are currently both handled from the `CurrentDateTime` component.

Let's first re-write the component to only deal with the rendering of some date time to the UI:

```tsx
export function DateTime({ dateTime }: { dateTime: Date }): JSX.Element {
  return <span>{dateTime.toISOString()}</span>;
}
```

Let's now dive into how we could handle the cross-cutting concern of 'fetching the current date time', in HOC or Render Props pattern.

## HOCs (Higher Order Components)

HOC is just a function that takes in a React component as a parameter, and returns a new component with some additional data 'injected'.

```tsx
interface WithTime {
  dateTime: Date;
}

export function withCurrentDateTime<T extends WithTime>(
  Component: React.ComponentType<T>
) {
  return function (props: Omit<T, "dateTime">) {
    return <Component {...(props as T)} dateTime={new Date()} />;
  };
}
```

Now you can create a component that displays the current date and time by passing in the `DateTime` component to the `withCurrentDateTime` function:

```tsx
export const CurrentDateTime = withCurrentDateTime(DateTime);
```

```tsx
function App() {
  return (
    <>
      <CurrentDateTime />
    </>
  );
}
```

## Render Props

In Render Props pattern, you create a React Component that takes in another component as a prop and render it with some data.

```tsx
export function RenderWithCurrentTime({
  render,
}: {
  render: (props: { dateTime: Date }) => JSX.Element;
}) {
  return render({ dateTime: new Date() });
}
```

Now you can pass in the function to render `DateTime` as the `render` prop.

```tsx
function App() {
  return (
    <>
      <RenderWithCurrentTime
        render={({ dateTime }) => <DateTime dateTime={dateTime} />}
      ></RenderWithCurrentTime>
    </>
  );
}
```

We've named the prop `render` in the example above, but `children` is used most commonly because the JSX syntax considers what is put inside a component element to be the `children` prop.

```tsx
export function RenderWithCurrentTime({
  children,
}: {
  children: (props: { dateTime: Date }) => JSX.Element;
}) {
  return children({ dateTime: new Date() });
}
```

in which case the call site would look like:

```tsx
function App() {
  return (
    <>
      <RenderWithCurrentTime>
        {({ dateTime }) => <DateTime dateTime={dateTime} />}
      </RenderWithCurrentTime>
    </>
  );
}
```
