## Решение:
```go
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
func preorderTraversal(root *TreeNode) []int {
    result := []int{}
    travers(root, &result)

    return result
}

func travers(node *TreeNode, result *[]int) {
    if node == nil {
        return
    }
    
    *result = append(*result, node.Val)
    travers(node.Left, result)
    travers(node.Right, result)
}
```
## Оценка по времени:
O(n), где n - кол-во узлов в дереве

Объяснения: мы должны обойти каждый узел дерева и записать его в результирующий слайс.



## Оценка по памяти:
O(n), где n - кол-во узлов дереве

Объяснения: так как нам в результате нужен слайс из переставленных узлов дерева, то мы, обходя всё дерево, записываем каждый узел в результирующий слайс, то есть мы должны создать столько же узлов, сколько в бинарном дереве.



## Описание решения:

Создаём слайс через литерал, так как заранее нам неизвестно какая может быть ёмкость, в котором будем хранить все отсортированные узлы. Дальше вызываем рекурсивную функцию, которая делает обход по узлам в такой последовательности: сначала записываем текущую ноду, затем совершаем обход влево, вызывая опять рекурсивную функцию, после возвращаемся и совершаем обход справа, также вызывая рекурсивную функцию.

В моём подходе используется передача слайса result в рекурсивную функцию через указатель, но можно лучше передавать по значению, так как слайс - это структура с указателем на первый элемент в массиве и с полями длины и ёмкостью. То бишь копируется только структура, а сам массив под капотом остаётся всё тот же:

```go
func preorderTraversal(root *TreeNode) []int {
    result := []int{}
    travers(root, result)

    return result
}

func travers(node *TreeNode, result []int) []int {
    if node == nil {
        return result
    }

    result = append(result, node.Val)
    result = travers(node.Left, result)
    result = travers(node.Right, result)
    return result
}
```
