## 1:
```go
type NumArray struct {
    result []int
}


func Constructor(nums []int) NumArray {
    result := make([]int, len(nums) + 1)
    result = append(result, 0)

    for _, num := range nums {
        result = append(result, result[-1] + num)
    }
    
    return NumArray{result: result}
}


func (this *NumArray) SumRange(left int, right int) int {
    return this.result[right + 1] - this.result[left]
}


/**
 * Your NumArray object will be instantiated and called as such:
 * obj := Constructor(nums);
 * param_1 := obj.SumRange(left,right);
 */
```

В Go нельзя взять последний элемент слайса с помощью отрицательного индекса.

## 2:
```go
type NumArray struct {
    result []int
}


func Constructor(nums []int) NumArray {
    result := make([]int, len(nums) + 1)
    result = append(result, 0)

    for _, num := range nums {
        result = append(result, result[len(result) - 1:] + num)
    }
    
    return NumArray{result: result}
}


func (this *NumArray) SumRange(left int, right int) int {
    return this.result[right + 1] - this.result[left]
}


/**
 * Your NumArray object will be instantiated and called as such:
 * obj := Constructor(nums);
 * param_1 := obj.SumRange(left,right);
 */
```

Я сделала взятие слайса из слайса, а хотел последний элемент слайса достать.

## 3:
```go
type NumArray struct {
    result []int
}


func Constructor(nums []int) NumArray {
    result := make([]int, len(nums) + 1)
    result = append(result, 0)

    for _, num := range nums {
        result = append(result, result[len(result) - 1:][0] + num)
    }
    
    return NumArray{result: result}
}


func (this *NumArray) SumRange(left int, right int) int {
    return this.result[right + 1] - this.result[left]
}


/**
 * Your NumArray object will be instantiated and called as such:
 * obj := Constructor(nums);
 * param_1 := obj.SumRange(left,right);
 */
```

Ошибка на самом первом кейсе, где исходный массив:
```
[-2,0,3,-5,2,-1]
```
а следующие элементы:
```
[0,2],[2,5],[0,5]
```
В итоге везде получаю 0, 0, 0

