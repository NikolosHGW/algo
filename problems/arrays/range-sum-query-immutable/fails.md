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
