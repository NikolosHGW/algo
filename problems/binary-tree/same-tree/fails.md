## 1:
```go
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
func isSameTree(p *TreeNode, q *TreeNode) bool {
    if p == nil || q == nil {
        return p == nil
    }
    
    if p.Val != q.Val {
        return false
    }

    return isSameTree(p.Left, q.Left) && isSameTree(p.Right, q.Right)
}
```
Не пройден тест кейс
```
input: p = [], q = [0]
```
```
output: true
```
```
expected: false
```

Я перепутал и поставил проверку p == nil, а надо было p == q
