# NodeJS环境IO

```tsx
const rl = require("readline").createInterface({ input: process.stdin });
var iter = rl[Symbol.asyncIterator]();
const readline = async () => (await iter.next()).value;

void async function () {
    const n = await readline()
}()
```

```jsx
const rl = require("readline").createInterface({ input: process.stdin });
var iter = rl[Symbol.asyncIterator]();
const readline = async () => (await iter.next()).value;

void async function () {
    while(line = await readline()){
        // 通过 line 拿到输入
    }
}()

```

```tsx
const readline = require('readline');

function input(prompt) {
  const rl = readline.createInterface({
    input: process.stdin,
    output: process.stdout
  });

  return new Promise(resolve => {
    rl.question(prompt, (answer) => {
      rl.close();
      resolve(answer);
    });
  });
}

(async () => {
  const name = await input("请输入内容: ");
  console.log(name);
})();
```