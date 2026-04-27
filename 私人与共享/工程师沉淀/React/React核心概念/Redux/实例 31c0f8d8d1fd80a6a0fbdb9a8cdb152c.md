# 实例

在对象的 **reducers** 属性中配置 多种触发**类型** 的 **回调处理函数**，函数的**传入就是上一个状态**

```jsx
const counterSlice = createSlice({
  name: 'counter',
  initialState: { value: 0 },
  reducers: {
    increment: state => {
      state.value++
    }
  }
})
```

然后到时候 **dispatch**

```jsx
import { **useDispatch** } from 'react-redux'
import { increment } from './counterSlice'

function Counter() {
  const dispatch = **useDispatch**()

  return (
    <button onClick={() => dispatch(increment())}>
      add
    </button>
  )
}
```