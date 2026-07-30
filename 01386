# Reactivity API 响应式

Vue2 的数据响应式都是内部实现的

Vue3 通过 JS 函数、代理实现了一个独立的响应式系统

ref, computed, watchEffect

> reactivity api: [https://v3.vuejs.org/api/reactivity-api](https://v3.vuejs.org/api/reactivity-api)
> 

# 获取响应式数据

- reactive ⇒ proxy实例
- readonly ⇒ 返回了新的 proxy 实例，set 和 deleteProperty 做了特殊处理
    
    ![image.png](548a4485-5e9f-405c-a83d-58f4964267ab.png)
    
    readonly 代理 proxy 实例时
    
    ```jsx
    const state = reactive({ a: 1, b: 2 }) // 返回 Proxy 实例
    const roState = readonly(state) // set 和 deleteProperty 做了特殊处理
    roState 是代理的 state，当 state 改变时，roState 内部的委托人也改变了，因为他们是一个
    ```
    

Proxy 第一个参数只能是对象，那么原始数据怎么办？

- ref 可以代理任何数据类型，封装到一个对象 value 属性上
    1. 原始数据类型 ⇒ ES6的 get value() 和 set value() 本质就是 Object.defineProperty 存取器属性
        
        对象用 Proxy 是为了动态的无感监听，但是原始数据类型直接用一个 对象 包裹后只需要管理一个属性 value 即可，不需要动态代理所有属性
        
    2. 对象 ⇒ 使用 reactive 后放入到 ref Object 的 value 中
    3. proxy实例 ⇒ 直接用该代理放入到 ref Object 的 value 中
- computed 在监听对象改变后第一次、且用到计算属性时会触发计算函数，后面都是用的缓存
    
    ```jsx
    const org = reactive({ a: 100, b: 250 })
    const sum = computed(() => {
        console.log("触发了 computed 函数")
        return org.a + org.b
    })
    console.log(sum.value) // "触发了 computed 函数"
    console.log(sum.value) // 缓存
    console.log(sum.value) // 缓存
    org.a = 250
    console.log(sum.value) // "触发了 computed 函数"
    console.log(sum.value) // 缓存
    ```
    

在 Vue3 中只有两种对象代理格式

1. ref Object（存取器属性对象）
2. proxy

reactive 拿到的是 proxy 不需要取 .value
ref Object才需要

[降低心智负担](Reactivity%20API%20%E5%93%8D%E5%BA%94%E5%BC%8F%203050f8d8d1fd807989b1e59b5a560fb8.md) 

开发纪律：最好所有 composition func 都返回的是 ref Obj

| API | 传入 | 返回 | 备注 |
| --- | --- | --- | --- |
| `reactive` | `plain-object` 普通对象 | `对象代理` Proxy | 深度代理对象中的所有成员 |
| `readonly` | `plain-object` or `proxy` | `对象代理` 只有 get 的Proxy | 只能读取代理对象中的成员，不可修改 |
| `ref` | `any` | `{ value: ... }` | 对value的访问是响应式的
如果给value的值是一个对象，
则会通过`reactive`函数进行代理
如果已经是代理，则直接使用代理 |
| `computed` | `function` | `{ value: ... }` | 当读取value值时，
会**根据情况**决定是否要运行函数 |

应用：

- 如果想要让一个**对象**变为响应式数据，可以使用`reactive`或`ref`
- 如果想要让一个对象的所有属性**只读**，使用`readonly`
- 如果想要让一个**非对象数据**变为响应式数据，使用`ref`
- 如果想要根据**已知的响应式数据得到一个新的响应式数据**，使用`computed`

笔试题1：下面的代码输出结果是什么？

```jsx
import { reactive, readonly, ref, computed } from "vue";

const state = reactive({
  firstName: "Xu Ming",
  lastName: "Deng",
});
const fullName = computed(() => {
  console.log("changed");
  return `${state.lastName}, ${state.firstName}`;
});
console.log("state ready");
console.log("fullname is", fullName.value);
console.log("fullname is", fullName.value);
const imState = readonly(state);
console.log(imState === state);

const stateRef = ref(state);
console.log(stateRef.value === state);

state.firstName = "Cheng";
state.lastName = "Ji";

console.log(imState.firstName, imState.lastName);
console.log("fullname is", fullName.value);
console.log("fullname is", fullName.value);

const imState2 = readonly(stateRef);
console.log(imState2.value === stateRef.value);
```

笔试题2：按照下面的要求完成函数

```jsx
function useUser(){
  // 在这里补全函数
  return {
    user, // 这是一个只读的用户对象，响应式数据，默认为一个空对象
    setUserName, // 这是一个函数，传入用户姓名，用于修改用户的名称
    setUserAge, // 这是一个函数，传入用户年龄，用户修改用户的年龄
  }
}
```

```jsx
// 对外暴露的 readOnlyUser 只读，其内部是一个可以在函数内部管理的响应数据
// readOnlyUser -> originUser
// 类似于 vuex 不允许外部直接更改数据，得调用暴露的API上报
export default function useUser() {
    const userOrigin = reactive({})
    const user = readonly(userOrigin)
    const setUserName = (name) => {
        userOrigin.name = name
    }
    const setUserAge = (age) => {
        userOrigin.age = age
    }
    return {
        user, // 这是一个只读的用户对象，响应式数据，默认为一个空对象
        setUserName, // 这是一个函数，传入用户姓名，用于修改用户的名称
        setUserAge, // 这是一个函数，传入用户年龄，用户修改用户的年龄
    }
}
```

笔试题3：按照下面的要求完成函数

```jsx
function useDebounce(obj, duration){
  // 在这里补全函数
  return {
    value, // 这里是一个只读对象，响应式数据，默认值为参数值
    setValue // 这里是一个函数，传入一个新的对象，需要把新对象中的属性混合到原始对象中，混合操作需要在duration的时间中防抖
  }
}
```

# 监听数据变化

**watchEffect**

```jsx
const stop = watchEffect(() => {
  // 该函数会立即执行，内部会通过 get 收集依赖-函数中用到的响应式数据，响应式数据变化后会再次执行
})

// 通过调用返回的 stop 函数，会停止监听
stop(); // 停止监听
```

**watch**

// 第一个参数得是表达式函数，用于声明依赖

```jsx
// 等效于vue2的$watch

// 监听单个数据的变化
const state = reactive({ count: 0 })

watch(() => state.count, (newValue, oldValue) => {
  // ...
}, options)

const countRef = ref(0);
watch(countRef, (newValue, oldValue) => {
  // ...
}, options)

// 监听多个数据的变化
watch([() => state.count, countRef], ([new1, new2], [old1, old2]) => {
  // ...
});
```

**注意：无论是`watchEffect`还是`watch`，当依赖项变化时，回调函数的运行都是异步的（微队列）**

```jsx
import { reactive, ref, watchEffect } from "vue";

const state = reactive({ a: 1, b: 2 });
const count = ref(0);

const stop = watchEffect(() => {
    console.log(state.a, count.value); // 内部会通过 get 收集依赖
});

// 第一次会立即执行 => 1 0 

state.b++
// 无事发生，因为 b 不是依赖

state.a++;
state.a++;
count.value++;
count.value++;
// 响应数据变化后是加入到微任务队列的、异步的，所以是一起处理、只会输出一次

stop(); // 返回的函数是用于停止监听的
state.a++;
// 无事发生

/*
但是由于 stop 是同步执行的，就不会触发回调了
也就是说只有一次输出
1 0 
*/
```

```jsx
没有stop时
/*
1 0 
4 2 异步，等所有微任务执行完再回调
*/
```

```jsx
setTimeout(() => {
    stop(); // 返回的函数是用于停止监听的
    state.a = 100; // 无事发生
}, 1000)

state.a++; // 属于同步代码，仍会进入到微任务队列中

/*
输出：
1 0 
4 2 

因为我将 stop 放到了宏任务中，stop不会影响之前的微任务执行

执行流程：
1. 同步代码阶段：
   → watchEffect 立即执行 => 输出 1 0
   → 修改 state.a, count.value（触发依赖更新，watchEffect 回调加入微任务队列）
   → 调用 setTimeout（同步执行，注册定时器，1000ms 后将回调加入宏任务队列）
   → state.a++（继续触发更新，合并到微任务队列）

2. 微任务队列执行：
   → watchEffect 回调执行 => 输出 4 2

3. 1000ms 后，宏任务执行：
   → setTimeout 的回调执行：stop() + state.a = 100（已停止，无输出）
*/
```

应用：除非遇到下面的场景，否则均建议选择`watchEffect`

- **不希望回调函数一开始就执行**
- 数据改变时，需要**参考旧值**
- 需要**监控一些回调函数中不会用到的数据**

笔试题: 下面的代码输出结果是什么？

```jsx
import { reactive, watchEffect, watch } from "vue";
const state = reactive({
  count: 0,
});
watchEffect(() => {
  console.log("watchEffect", state.count);
});
watch(
  () => state.count,
  (count, oldCount) => {
    console.log("watch", count, oldCount);
  }
);
console.log("start");
setTimeout(() => {
  console.log("time out");
  state.count++;
  state.count++;
});
state.count++;
state.count++;

console.log("end");
```

# 判断

| API | 含义 |
| --- | --- |
| `isProxy` | 判断某个数据是否是由`reactive`或`readonly` |
| `isReactive` | 判断某个数据是否是通过`reactive`创建的<br />详细:[https://v3.vuejs.org/api/basic-reactivity.html#isreactive](https://v3.vuejs.org/api/basic-reactivity.html#isreactive) |
| `isReadonly` | 判断某个数据是否是通过`readonly`创建的 |
| `isRef` | 判断某个数据是否是一个`ref`对象 |

# 转换

**unref**

解构

等同于：**`isRef(val) ? val.value : val`**

应用：

```jsx
function useNewTodo(todos){
  todos = unref(todos);
  // ...
}
```

**toRef**

得到一个响应式对象某个属性的ref格式

```jsx
const state = reactive({
  foo: 1,
  bar: 2
})

const fooRef = toRef(state, 'foo'); // fooRef: {value: ...}

fooRef.value++
console.log(state.foo) // 2

state.foo++
console.log(fooRef.value) // 3
```

**toRefs**

把一个响应式对象的所有属性转换为ref格式，然后包装到一个`plain-object`中返回

```jsx
const state = reactive({
  foo: 1,
  bar: 2
})

const stateAsRefs = toRefs(state)
/*
stateAsRefs: not a proxy
{
  foo: { value: ... },
  bar: { value: ... }
}
*/
```

应用：

**展开运算后变成 lost reactivity 失去了响应式**

得例如在 setup 返回时 **…toRefs**(state)

```jsx
setup(){
  const state1 = reactive({a:1, b:2});
  const state2 = reactive({c:3, d:4});
  return {
    ...state1, // lost reactivity
    ...state2 // lost reactivity
  }
}

setup(){
  const state1 = reactive({a:1, b:2});
  const state2 = reactive({c:3, d:4});
  return {
    ...toRefs(state1), // reactivity
    ...toRefs(state2) // reactivity
  }
}
// composition function
function usePos(){
  const pos = reactive({x:0, y:0});
  return pos;
}

setup(){
  const {x, y} = usePos(); // lost reactivity
  const {x, y} = toRefs(usePos()); // reactivity
}
```

# 降低心智负担

通过开发纪律

**所有的`composition function`均以`ref`的结果返回，以保证`setup`函数的返回结果中不包含`reactive`或`readonly`直接产生的数据**

```jsx
function usePos(){
  const pos = reactive({ x:0, y:0 });
  return toRefs(pos); //  {x: refObj, y: refObj}
}
function useBooks(){
  const books = ref([]);
  return {
    books // books is refObj
  }
}
function useLoginUser(){
  const user = readonly({
    isLogin: false,
    loginId: null
  });
  return toRefs(user); // { isLogin: refObj, loginId: refObj }  all ref is readonly
}

setup(){
  // 在setup函数中，尽量保证解构、展开出来的所有响应式数据均是ref
  return {
    ...usePos(),
    ...useBooks(),
    ...useLoginUser()
  }
}
```