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

Accepts a context object (the value returned from React.createContext) and returns the current context value for that context. The current context value is determined by the value prop of the nearest <MyContext.Provider> above the calling component in the tree.

```typescript
const context = useContext(Context);
```

## useReducer

Alernative to useState. Accepts a reducer of type **(state, action) => new State** and returns the current state paired with a **dispatch** method.

```typescript
const initialState = { count: 0 };
function reducer(state, action) {
  switch (action.type) {
    case "increment":
      return { count: state.count + 1 };
    case "decrement":
      return { count: state.count - 1 };
    default:
      throw new Error();
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, initialState);
  return (
    <>
      Count: {state.count}
      <button onClick={() => dispatch({ type: "decrement" })}>-</button>
      <button onClick={() => dispatch({ type: "increment" })}>+</button>
    </>
  );
}
```

## useCallback

**Returns a memoized callback** that only changes if one of the dependencies has changed.

```typescript
const memoizedCallback = useCallback(() => {
  doSomething(a, b);
}, [a, b]);
```

## useMemo

**Returns a memoized value.**

```typescript
const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
```

## useRef

useRef returns a mutable ref object whose **.current** property is initialized to the passed argument. Changing refs does not trigger rerender.

```typescript
function RefExample() {
  const inputEl = useRef<HTMLInput>(null);

  return (
    <>
      <input ref={inputEl} type="text" />
      <button
        onClick={() => {
          inputEl.current?.focus();
        }}
      >
        Focus the input
      </button>
    </>
  );
}
```

## useImperativeHandle

```typescript
useImperativeHandle(ref, createHandle, [deps]);
```

useImperativeHandle

```typescript
function FancyInput(props, ref) {
  const inputRef = useRef();
  useImperativeHandle(ref, () => ({
    focus: () => {
      inputRef.current.focus();
    }
  }));
  return <input ref={inputRef} ... />;
}
FancyInput = forwardRef(FancyInput);
```

## useLayoutEffect

## useDebugValue

## useDeferredValue

## useTransition

## useId
