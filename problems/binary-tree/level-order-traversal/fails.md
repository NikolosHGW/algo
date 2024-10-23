## 1:
```go
func levelOrder(root *TreeNode) [][]int {
    levels := [][]int{}    

    return preorderTraversal(root, 0, levels)
}

func preorderTraversal(node *TreeNode, level int, levels [][]int) [][]int {
    if node == nil {
        return levels
    }

    levelsLen := len(levels)

    if levelsLen <= level {
        levels[level] = []int{}
    }

    levels[level] = append(levels[level], node.Val)
    levels = preorderTraversal(node.Left, level + 1, levels)
    levels = preorderTraversal(node.Right, level + 1, levels)

    return levels
}
```
В строке levels[level] = []int{} я пытаюсь добавить в слайс размером 0 элемент. Надо же append сделать, а то я тут как в js и php добавляю.
