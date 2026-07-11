# Diva包快速下线技巧

Source: [KM 2758980875](https://km.sankuai.com/collabpage/2758980875)

### 背景

由于 “Diva上包过多” 导致在锁包时失败（因为 pull 时会拉下所有包）

所以需要下线

### 问题

但是 Diva 不支持一键下线，所以得一个个点击 “查看” a标签后跳转下线，问题是这个跳转不是 blank 而是覆盖的，导致下线多个时需要不断回退，并且回退后默认分页在第 1 页而不是目标下线的、也就是最后的包页，所以现在目标是让他用 blank 的方式跳转

```
// 代码块
document.addEventListener('click', function (e) {
  const a = e.target.closest('a[href]');
  if (!a) return;

  const href = a.getAttribute('href');
  if (!href || href.startsWith('#') || href.startsWith('javascript:')) return;

  e.preventDefault();
  e.stopPropagation();
  e.stopImmediatePropagation();
  window.open(a.href, '_blank', 'noopener,noreferrer');
}, true);
```