## Решение:
```go
func sortedSquares(nums []int) []int {
    numsLen := len(nums)

    result := make([]int, numsLen)

    p1 := 0
    p2 := numsLen - 1

    iter := p2

    for p1 <= p2 {
        p1Sqr := nums[p1] * nums[p1]
        p2Sqr := nums[p2] * nums[p2]

        if p1Sqr > p2Sqr {
            result[iter] = p1Sqr
            p1++
        } else {
            result[iter] = p2Sqr
            p2--
        }
        iter--
    }

    return result
}
```

## Оценка по времени:
O(n) - где n - размер входного массива.

Объяснение: с помощью двумя указателями я всегда прохожусь по всем элементам массива, пока указатели не начнут указывать друг на друга

## Оценка по памяти:
O(n) - где n - размер входного массива.

Объяснение: так как я прохожу каждый элемент массива, я должен на каждый элемент создать его аналог, но только в квадрате. То бишь я аллоцирую память под n новыйх элементов.

## Описание решения:
Я создаю слайс с размером входного массива, создаю итератор с размером последнего индекса, чтобы по этому итератору вставлять элементы в конец слайса, чтобы сразу заполнить слайс от большего к меньшему. Также создаю два указателя, один на первый элемент, второй на последний элемент. Дальше вызываю цикл с условием его работы, пока два указателя не встретятся в одном месте (p1 <= p2). В цикле я проверяю, что если квадрат элемента, на который указывает первый указатель больше, чем квадрат элемента, на который указывает второй указатель, то я вставляю в слайс по индексу итератора квадрат первого элемента и итерирую первый указатель, если нет, то я вставляю в слайс по итератору квадрат второго элемента и итерирую в минус второй указатель. Также в этом цикле в самом конце итерации цикла я итерирую в минус итератор, по которому вставляю в слайс значения.