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

- class components

  - class organization
  - state management

## Timeline of rendering

- js loaded
- app component created
- call apis/functions
- api/functions returns jsx
- jsx is rendered as html
- success! or error message
