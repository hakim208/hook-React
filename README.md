
# 📘 README: Хукҳо дар React

Дар React, **хукиҳо (Hooks)** ба шумо имкон медиҳанд, ки ҳолат (state) ва дигар хусусиятҳои React-ро дар компонентҳои функсионалӣ истифода баред. Ин ҷо мо хукҳои асосиро дида мебароем: `useState`, `useEffect`, `useLayoutEffect`, `useRef` ва `useContext` бо мисолҳо ва расмҳои фаҳмонда.

---

## 🔹 useState

`useState` барои нигоҳ доштани маълумот (state) дар дохили компонент истифода мешавад.

### 📌 Мисол:

```jsx
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Шумора: {count}</p>
      <button onClick={() => setCount(count + 1)}>Илова кардан</button>
    </div>
  );
}
```


---

## 🔹 useEffect

`useEffect` барои иҷрои код баъди рендер (render) истифода мешавад, масалан, гирифтани маълумот аз API.

### 📌 Мисол:

```jsx
import React, { useEffect, useState } from 'react';

function Example() {
  const [data, setData] = useState([]);

  useEffect(() => {
    fetch('https://jsonplaceholder.typicode.com/posts')
      .then(response => response.json())
      .then(json => setData(json));
  }, []);

  return (
    <ul>
      {data.map(item => (
        <li key={item.id}>{item.title}</li>
      ))}
    </ul>
  );
}
```


---

## 🔹 useLayoutEffect

`useLayoutEffect` мисли `useEffect` аст, аммо пеш аз намоиш додани DOM иҷро мешавад.

### 📌 Мисол:

```jsx
import React, { useLayoutEffect, useRef } from 'react';

function LayoutEffectExample() {
  const divRef = useRef();

  useLayoutEffect(() => {
    console.log(divRef.current.getBoundingClientRect());
  }, []);

  return <div ref={divRef}>Салом!</div>;
}
```


---

## 🔹 useRef

`useRef` барои нигоҳ доштани элементҳои DOM ё арзишҳое, ки бе ререндер тағйир меёбанд, истифода мешавад.

### 📌 Мисол:

```jsx
import React, { useRef } from 'react';

function FocusInput() {
  const inputRef = useRef(null);

  const focusInput = () => {
    inputRef.current.focus();
  };

  return (
    <div>
      <input ref={inputRef} type="text" />
      <button onClick={focusInput}>Фокус кардан</button>
    </div>
  );
}
```


---

## 🔹 useContext

`useContext` барои дастрасӣ ба маълумот аз Context Provider истифода мешавад.

### 📌 Мисол:

```jsx
import React, { useContext, createContext } from 'react';

const MyContext = createContext();

function Child() {
  const value = useContext(MyContext);
  return <p>Маълумот аз контекст: {value}</p>;
}

function App() {
  return (
    <MyContext.Provider value="Салом аз контекст!">
      <Child />
    </MyContext.Provider>
  );
}
```


---

## 📚 Хулоса

| Хук               | Барои чӣ лозим аст?              |
| ----------------- | -------------------------------- |
| `useState`        | Нигоҳ доштани маълумот           |
| `useEffect`       | Иҷрои амалҳо баъди render        |
| `useLayoutEffect` | Иҷрои амалҳо пеш аз намоиши DOM |
| `useRef`          | Дастрасӣ ба DOM ё арзиши собит   |
| `useContext`      | Гирифтани маълумот аз контекст   |

---
