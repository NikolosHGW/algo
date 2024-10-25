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
func isSymmetric(root *TreeNode) bool {
    return check(root.Left, root.Right)
}

func check(l *TreeNode, r *TreeNode) bool {
    if l == nil || r == nil {
        return l == r
    }

    return check(l.Left, r.Right) && check(l.Right, r.Left)
}
```

Не пройдент кейс
```
input: [1,2,3]
```
```
output: true
```
```
expected: false
```
Я забыл указать самую главную проверку для значений узла. То бишь, в данном выше решении я лишь проверяю на nil (на окончание листов), а надо ещё проверять значения.
