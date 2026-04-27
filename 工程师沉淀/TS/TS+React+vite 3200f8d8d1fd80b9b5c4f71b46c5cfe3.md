# TS+React+vite

https://github.com/ceilf6/Lab/commit/709e2c55454dd36eb2e120518c19de0dd9e193ea

# React 相关类型

```tsx
interface ItemProps {
    todo: todoItem,
    children?: React.ReactNode, // React 中 节点类型
    style?: React.CSSProperties // React 中 CSS 类型
}
```

```tsx
    const handleSubmit = (e: React.FormEvent<HTMLFormElement>) => {
            e.preventDefault() // 阻止默认事件，否则表单提交后会导致刷新
            if(text)
                onAdd(text)
            setText('')
        }
```

# setState异步

```tsx
    const addTodo = (text: string) => {
        setLastTodo(pre => pre + 1)
        const newTodoItem: todoItem = {
            id: lastTodo,
            text,
            done: false,
        }
        setTodos([...todos, newTodoItem])
    }
```

导致用到的值是一个

## 状态同步更新

通过 新声明一个变量 然后共同使用

```jsx
    const addTodo = (text: string) => {
        const newID = lastTodoID + 1

        setLastTodoID(() => {
            // 如果 包裹了，那么就有了副作用（React会通过执行两次判断是否有副作用
            // setTodos(todos => [
            //     ...todos,
            //     { id, text, done: false }
            // ])
            return newID
        })
        setTodos([...todos, { id: newID, text, done: false }])
    }

```

```tsx
export const filters = ['全部', '已完成', '未完成'] as const
// as const 把这个值推导为最“窄”的只读字面量类型（literal type），不要进行类型拓宽
export type Filter = typeof filters[number]
```

```tsx
import React, { useState } from 'react'

interface AddItemProps {
    onAdd: (text: string) => void,
    children?: string
}

export default function AddItem(props: AddItemProps) {
    const [text,setText] = useState<string>('')
    const {onAdd, children} = props

  return (
    <>
        <input type="text" 
            onChange={(e: React.ChangeEvent<HTMLInputElement>) => {
                setText(e.target.value)
            }}
            value={text} // 受控组件
        />
        <button onClick={() => {
            onAdd(text)
            setText('')
        }}>
            {children}
        </button>
    </>
  )
}

```

```tsx
export interface todoItem {
    id: number,
    text: string,
    done: boolean
}
```

```tsx
import { useState } from "react";
import type { todoItem } from "../types/todos";
// 别忘记 type // “todoItem”是一种类型，必须在启用 "verbatimModuleSyntax" 时使用仅类型导入进行导入。

export function useTodoData() {
    const [todos, setTodos] = useState<todoItem[]>([
        { id: 1, text: 'learn TS', done: true }
    ])
    const [lastTodo, setLastTodo] = useState<number>(1)

    // useEffect(() => {
    //     // const res = fetch()
    //     setTodos(res)
    // }, [])

    const addTodo = (text: string) => {
        setLastTodo(pre => ++pre)
        const newTodoItem: todoItem = {
            id: lastTodo,
            text,
            done: false,
        }
        setTodos([...todos, newTodoItem])
    }

    const deleteTodo = (id: number) => {
        setTodos(todos.filter(item => item.id !== id))
    }

    const toggleTodo = (id: number) => {
        setTodos(todos.map(todoItem => {
            if (todoItem.id === id) {
                todoItem.done = !todoItem.done
            }
            return todoItem
        }))
    }

    return {
        todos,
        // setTodos,
        addTodo,
        deleteTodo,
        toggleTodo
    }
}
```

```tsx
import { useTodoData } from '../hooks/useTodoData'
import ItemList from '../components/ItemList'
import AddItem from '../components/AddItem'
import FilterItem from '../components/FilterItem'

export default function TodoView() {
    const {
        todos,
        deleteTodo,
        toggleTodo,
        addTodo
    } = useTodoData()

  return (
    <div>
      <h1>TodoView</h1>
      <AddItem onAdd={addTodo}>添加事项</AddItem>
      <ItemList todos={todos} onDel={deleteTodo} onToggle={toggleTodo}>
        <h2>代办列表</h2>
      </ItemList>
      <FilterItem></FilterItem>
    </div>
  )
}

```