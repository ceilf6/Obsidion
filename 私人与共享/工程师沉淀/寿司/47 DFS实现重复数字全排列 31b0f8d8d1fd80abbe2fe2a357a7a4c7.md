# 47 DFS实现重复数字全排列

DFS 本质就是树，从树中选出符合要求的路径

![image.png](47%20DFS%E5%AE%9E%E7%8E%B0%E9%87%8D%E5%A4%8D%E6%95%B0%E5%AD%97%E5%85%A8%E6%8E%92%E5%88%97/image.png)

通过 vis 确保如果相邻两个相同情况下，只有前者用了才能用后者，从而确保不会重复

cur 记录当前组合的状态

```jsx
/**
 * @param {number[]} nums
 * @return {number[][]}
 */
var permuteUnique = function(nums) {
    nums.sort((a,b) => a-b)
    const LN = nums.length
    const vis = new Array(LN).fill(false)
    const cur = new Array(LN)
    const ans = []
    function dfs(step){
        if(step===LN){
            ans.push([...cur]) // 得展开，不然推入的就是引用地址了
            return
        }
        for(let i=0;i<LN;i++){
            if(
                !vis[i] &&
                (
                    i===0 ||
                    nums[i]!==nums[i-1] ||
                    vis[i-1]
                )
            ){
                vis[i]=true
                cur[step]=nums[i]
                dfs(step+1)
                vis[i]=false
            }
        }
    }
    dfs(0)
    return ans
};
```