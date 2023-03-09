<!-- HEADER -->
<div align="center">
  <h1 align="center">React Hooks</h1>
</div>

# What is hooks?
```shell
Hooks allow function components to have access to state and other React features.
```
```shell
[Rules]
1. Hooks can only be called inside React function components.
2. Hooks can only be called at the top level of a component.
3. Hooks cannot be conditional
```

# Types
1. useState
2. useEffect
3. useContext
4. useRef
5. useReducer
6. useCallback
7. useMemo
8. custom hooks

## 1. useState
> The useState hook allows us to track state in a function component.
>
> getter, setter

## 2. useEffect
> The useEffect hook allows us to perform side effects in your components.
> 
> Examples of side effects: fetching data, directly updating the DOM, and timers.
> 
> useEffect accepts two arguments. The second one is optional.
> 
> useEffect(<function>, <dependency>)

### 2.1 Examples
```shell
[No dependency passed]
useEffect(() => {
  //Runs on every render
});

[An empty array]
useEffect(() => {
  //Runs on the first render
}, []);

[Props or state values]
useEffect(() => {
  //Runs on the first render
  //And any time any dependency value changes
}, [prop, state]);
```

## 3. useContext
> React Context is a way to manage state globally.
> 
> State should be held by the highest parent component in the stack that requires access to the state.
> 
> In a nested component, we will need to pass the state as props through each nested component; prop drilling.

## 3.1 Examples
```shell
[Parent component]
import { createContext } from "react";

export const UserContext = createContext();

function Parent() {
  const [user, setUser] = useState("Alvin");
  
  return (
    <UserContext.Provider value={user}>
      <Child user={user} />
    </UserContext.Provider>
  );
}

export default Parent;
```
```shell
[Child component]
import { useContext } from "react";
import { UserContext } from "./Parent";

function Child() {
  //get a name value from parent 
  const nameValue = useContext(UserContext);
  
  return (
    //returns "Alvin"
    {nameValue}
  );
}
```

## 4. useRef
> The useRef hook allows you to persist values between renders.
> 
> It can be used to store a mutable value that does not cause Re-renders when updated.

### 4.1 Examples
```shell
import { useState, useRef, useEffect } from "react";

function App() {
  const [inputValue, setInputValue] = useState("");
  const count = useRef(0);
  
  useEffect(() => {
    //inside the useEffect, even if the state changes, it do not cause re-render
    count.current = count.current + 1;
  });
  
  return (
    <>
      <input 
        type="text"
        value={inputValue}
        onChange={(e) => {setInputValue(e.target.value)}}
      />
      <p>Render Count: count.current</p>
    </>
  );
}

export default App;
```

## 5. useReducer

## 6. useCallback

## 7. useMemo

## 8. Custom Hooks