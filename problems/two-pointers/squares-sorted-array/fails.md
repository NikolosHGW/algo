## 1:
```go
func sortedSquares(nums []int) []int {
    numsLen := len(nums)

    result := make([]int, numsLen)

    p1 := 0
    p2 := numsLen - 1

    for p1 <= p2 {
        p1Sqr := nums[p1] * nums[p1]
        p2Sqr := nums[p2] * nums[p2]

        if p1Sqr > p2Sqr {
            result[p1] = p1Sqr
            p1++
        } else {
            result[p2] = p2Sqr
            p2++
        }
    }

    return result
}
```
Ошибка: panic: runtime error: index out of range [5] with length 5

Я инкрементировал второй указатель, который как раз начинается с последнего индекса, от чего вышел за пределы слайса. И плюс я вставляю результаты квадратов по указателям, что, как по мне, может повести себя не предсказуемо. Надо бы лучше написать цикл через for с счётчиком и по счётчику с убыванием ставить элементы, то бишь начинать с конца массива.
