# useMemoizedFn

https://github.com/ceilf6/hooks/commit/f077ec8b9ff57cf0e5466875536116c4d75d747a

useCallback 依赖变化时引用会变，使用时需要注意依赖

而 useMemoizedFn 引用永远稳定、无需设置依赖，且始终调用最新函数

本质就是通过 useRef 创建了 稳定的壳函数memoizedFn ，在调用时通过 fnRef.current 拿到最新值

```tsx
import { useMemo, useRef } from 'react';
import { isFunction } from '../utils';
import isDev from '../utils/isDev';

type noop = (this: any, ...args: any[]) => any;

type PickFunction<T extends noop> = (
  this: ThisParameterType<T>,
  ...args: Parameters<T>
) => ReturnType<T>;

const useMemoizedFn = <T extends noop>(fn: T) => {
  if (isDev) {
    if (!isFunction(fn)) {
      console.error(`useMemoizedFn expected parameter is a function, got ${typeof fn}`);
    }
  }

  const fnRef = useRef<T>(fn);

  // why not write `fnRef.current = fn`?
  // https://github.com/alibaba/hooks/issues/728
  fnRef.current = useMemo<T>(() => fn, [fn]); // 每次渲染更新 fnRef 为最新函数

  const memoizedFn = useRef<PickFunction<T>>(undefined);
  // 只创建一次，是一个 稳定的壳函数 ，调用时转发给 fnRef.current

  if (!memoizedFn.current) {
    memoizedFn.current = function (this, ...args) {
      return fnRef.current.apply(this, args); // 调用时通过 ref 的 .current 拿到最新值
    };
  }

  return memoizedFn.current; // 永远返回同一个引用
};

export default useMemoizedFn;

```