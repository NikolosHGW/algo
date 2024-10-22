## 1:
```
func preorderTraversal(root *TreeNode) []int {
    result := []int{}
    travers(root, result)

    return result
}
```

```
func travers(node *TreeNode, result []int) {
    if node == nil {
        return
    }
    
    result = append(result, node.Val)
    travers(node.Left, result)
    travers(node.Right, result)
}
```

Не разобрался с работой передачи переменных в функции. Модификация слайса result происходит в локальной переменной функции traver, от чего с оригинальным result ничего не происходит.
