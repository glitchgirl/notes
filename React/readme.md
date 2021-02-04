# React

## Definitions

- JSX - Javascript XML, allows HTML in react or another component

## Three Tenets of Components

1- Component nesting - Components can be shown inside of each other
2- Component Reusability - Easily recycled
3- Component Configuration - Can be configured after creation

- React components only re-render when there are changes to the props or state. Don't use force update function.

## Function components vs class components

- Classes use lifecycle methods

- functional components

  - good for simple content
  - don't work when we are waiting for info
  - without hooks you can't change state

- class components

  - class organization
  - state management
  - must extend React.component
  - must define a render method that returns some amount of JSX
  - updating state on a component causes it to re-render

## Timeline of rendering

- js loaded
- app component created
- call apis/functions
- api/functions returns jsx
- jsx is rendered as html
- success! or error message

## Rules of State

- Only usable with class components
- props DO NOT equal state
- state is an object that contains data relevant to a component.
- state must be initialized when a component is created.
- state can only be updated using the function set.state

## Higher order components

- Fetch data and propagate to children
