# useDebounce

注意 钩子 必须在 自定义钩子或函数组件的**顶层**

和一般防抖一样，利用的是 debounce外层函数的闭包

```tsx
import { useRef, useCallback } from "react";

export default function useDebounce(fn, time) {
  const timer = useRef(null);

  const debounceFn = useCallback((...args) => {
    if (timer.current) {
      clearTimeout(timer.current);
    }
    timer.current = setTimeout(() => {
      fn.apply(this, args);
    }, time);
  }, [fn, time]);

  return debounceFn;
}
```

## preStudy

```jsx
import { useRef } from "react";

export default function useDebounce(fn, time) {
    return function (...args) {
        let timer = useRef(null) // Hook必须在顶层
        // timer 放在返回函数内部，每次执行都会拿到一个新的 timer 容器
        if (timer.current) {
            clearTimeout(timer.current)
        }
        timer.current = setTimeout(() => {
            fn.apply(this, args) // apply 传的是一个参数数组
        }, time)
    }
}
```