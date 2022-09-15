# Hooks

## useState

Returns a stateful value, and a function to update it.

```typescript
const [value, setValue] = useState<string>("Default Value");
```

## useEffect

Used to handle side effects in functional components.

```typescript
useEffect(() => {
  const timer = setTimeout(() => {
    // Some functionality
  }, 1000);

  // return cleansup the useEffect
  // helps prevent memory leaks
  // React 18 in development mode helps show this more
  return () => clearTimeout(timer);
}, [dependencyArray]);
```

## useContext

## useReducer

## useCallback

## useMemo

## useRef

## useImperativeHandle

## useLayoutEffect

## useDebugValue

## useDeferredValue

## useTransition

## useId
