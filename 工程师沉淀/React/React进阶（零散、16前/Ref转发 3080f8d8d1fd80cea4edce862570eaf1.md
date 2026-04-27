# Ref转发

从函数组件中拿到目标的 ref

forwardRef方法：

1. 参数，传递的是**函数组件A**，不能是类组件，并且，函数组件需要有第二个参数来得到ref
    
    类中想使用的话，1. 可以通过属性传入，因为 ref 本质就是一个对象
    
    2. 直接用函数包装一下，然后通过属性接续传递
    
2. 返回值，**返回一个新的组件newA**

（HOC高阶组件）

拿到新组件后，在使用时声明了 ref ，那么就会作为第二个参数传入到forwardRef的入参函数组件A中

https://github.com/ceilf6/Lab/commit/7f9cd2d5e1b1ed187617cec8d5f9c92d8a0a6983

![image.png](工程师沉淀/React/React进阶（零散、16前/Ref转发/image.png)

```jsx
import React from "react";

function A(props, ref) {
    // 作为参数传入
    return (
        <h1 ref={ref}>
            组件A
            <br />
            <span>{props.words}</span>
        </h1>
    );
}

//传递函数组件A，得到一个新组件NewA
const NewA = React.forwardRef(A);

export default class App extends React.Component {
    ARef = React.createRef();

    componentDidMount() {
        console.log(this.ARef);
    }

    render() {
        return (
            <div>
                <NewA ref={this.ARef} words="ceilf6" />
                {/* 传入 */}
            </div>
        );
    }
}

```

# 通过 ref 转发解决 HOC 导致的 ref 错误

https://github.com/ceilf6/Lab/commit/fd93e66e2e5da7b5a776d388d78326a81d473ad1

如果不加处理，外层 ref 会在 HOC 的包装层上，如果想用最内层的方法需要在 HOC 中间层转发

```jsx
// 用于登录控制的HOC

import React from "react";

export default function withLogin(Comp, modifier) {
    function LoginWrapper(props) {
        if (props.isLogin) {
            const { forwardRef, ...rest } = props
            return (
                <>
                    <h1>{modifier}</h1>
                    {/* 还能额外修饰等等、玩法很多 */}
                    <Comp {...rest} ref={forwardRef} />
                </>
            )
        }
        return null;
    }

    return React.forwardRef((props, ref) => {
        return <LoginWrapper {...props} forwardRef={ref} />
    })
}
```