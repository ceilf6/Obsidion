# 传给 ElementIf 的 JSX 参数会先求值，所以只要 props.filterStructs[0] 这一行在构造元素时跑到，就还是会炸

对，主要就是这个原因，而且还有一层更细的坑。

`ElementIf` 只是个函数调用。像你这段：

```tsx
ElementIf(
  props.filterStructs?.length > 0,
  <View>
    {ElementIf(
      props.filterStructs[0]?.barImage,
      <Image source={{ uri: props.filterStructs[0].barImage }} />
    )}
  </View>
)
```

JS 会先把参数都算出来，再调用 `ElementIf(...)`。也就是更接近：

```tsx
const child = (
  <View>
    {ElementIf(
      props.filterStructs[0]?.barImage,
      <Image source={{ uri: props.filterStructs[0].barImage }} />
    )}
  </View>
);

ElementIf(props.filterStructs?.length > 0, child);
```

所以外层“前置判断”并不能阻止内层 JSX 里的 `props.filterStructs[0]` 被访问。

另外你这里还有第二个问题：

```tsx
props.filterStructs[0]?.barImage
```

这并不完全安全。`?.` 只保护了 `.barImage`，没保护 `filterStructs[0]` 这一步。

如果 `props.filterStructs` 本身是 `undefined`，会先在 `[0]` 这里炸。

真正安全的写法要么是：

```tsx
props.filterStructs?.[0]?.barImage
```

要么先拿出来：

```tsx
const firstFilter = props.filterStructs?.[0];
```

然后统一用：

```tsx
firstFilter?.barImage
firstFilter?.barTitle
```

所以结论是：是的，`ElementIf` 参数先求值是核心原因；同时你当前的可选链位置也不对，导致 `[0]` 这一步仍然是裸访问。