# Hooks

- Can only be used in functional components.
- Can't be called conditionally.
- Don't use "use" for any function name because react will thinks its a hook
- useDispatch()
  - dispatches functions from the redux store

## Primitive hooks

- default hooks
- useEffect

1. [] - run only the first time
2. _nothing_ - run the first time AND when it re-renders
3. [stuff] - run the first time AND ONLY when it re-renders with data (stuff) changes

- case 2 is rare
- can't be async

If you need useEffect to be async, put an async function inside and call it 
