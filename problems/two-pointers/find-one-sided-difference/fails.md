## 1:
```go
func findDifference(nums1, nums2 []int) []int {
    result := make([]int, 0, len(nums1))

    p1 := 0
    p2 := 0

    for p1 < len(nums1) {
        if p2 >= len(nums2) {
            result = append(result, nums1[p1])
            p1++
            continue
        }

        if nums1[p1] < nums2[p2] {
            result = append(result, nums1[p1])
            p1++
        } else if nums1[p1] > nums2[p2] {
            result = append(result, nums[p1])
            p1++
            p2++
        } else nums1[p1] == nums2[p2] {
            p1++
            p2++
        }
    }

    return result
}
```

Ошибка: # command-line-arguments ./solution.go:23:16: syntax error: else must be followed by if or statement block ./solution.go:29:5: syntax error: non-declaration statement outside function body

Я нарушил синтаксис else, написав после else условие nums1[p1] == nums2[p2] без if. Надо либо добавить if, но лучше просто убрать условие, оставить одно else, так как после двух условий nums1[p1] < nums2[p2] и nums1[p1] > nums2[p2] остаётся как раз только равенство.

## 2:
```go
func findDifference(nums1, nums2 []int) []int {
    result := make([]int, 0, len(nums1))

    p1 := 0
    p2 := 0

    for p1 < len(nums1) {
        if p2 >= len(nums2) {
            result = append(result, nums1[p1])
            p1++
            continue
        }

        if nums1[p1] < nums2[p2] {
            result = append(result, nums1[p1])
            p1++
        } else if nums1[p1] > nums2[p2] {
            result = append(result, nums[p1])
            p1++
            p2++
        } else {
            p1++
            p2++
        }
    }

    return result
}
```

Ошибка: # command-line-arguments ./solution.go:20:37: undefined: nums

Где-то забыл правильно указать имя массива, так как часто очень во время написания кода забывал к названию массива добавить цифру (nums, а надо nums1 или nums2)

## 3:
```go
func findDifference(nums1, nums2 []int) []int {
    result := make([]int, 0, len(nums1))

    p1 := 0
    p2 := 0

    for p1 < len(nums1) {
        if p2 >= len(nums2) {
            result = append(result, nums1[p1])
            p1++
            continue
        }

        if nums1[p1] < nums2[p2] {
            result = append(result, nums1[p1])
            p1++
        } else if nums1[p1] > nums2[p2] {
            result = append(result, nums1[p1])
            p1++
            p2++
        } else {
            p1++
            p2++
        }
    }

    return result
}
```

Ошибка: Неправильный ответ
Входные данные

nums2 = [0,0,0,3]; nums1 = [1,2,2,3,3,4]; 
Ожидаемый результат

[1,2,2,4]
Результат исполнения

[1,2,2,3,4]

Я зря двигал два указателя, когда значение по первому указателю было больше, чем значение по второму указателю, из-за этого, я мог записать в результатирующий массив те значения, которые в итоге потом встретятся во втором массиве, а это по условия задачи ошибка (пример: nums1 = [1,2,2,3,3,4], nums2 = [0,0,0,2]). Также тут основная проблема в том, что мой алгоритм после выхода за пределы массива nums2 может записать в результатирующий массив дубликат, если в первом массиве дублируются числа именно в тот момент, где выходит за пределы второй массив.

## 4:
```go
func findDifference(nums1, nums2 []int) []int {
    result := make([]int, 0, len(nums1))

    p1 := 0
    p2 := 0

    nums2LastVal := nums2[len(nums2) - 1]

    for p1 < len(nums1) {
        if p2 >= len(nums2) && nums2LastVal == nums1[p1] {
            p1++
            continue
        }

        if p2 >= len(nums2) {
            result = append(result, nums1[p1])
            p1++
            continue
        }

        if nums1[p1] < nums2[p2] {
            result = append(result, nums1[p1])
            p1++
        } else if nums1[p1] > nums2[p2] {
            p2++
        } else {
            p1++
            p2++
        }
    }

    return result
}
```

Ошибка: Программа выбросила исключение
Входные данные

nums1 = [100,169]; nums2 = []; 

Если вдруг nums2 окажется пустым, то моя программа упадёт на строке nums2LastVal := nums2[len(nums2) - 1], поэтому надо бы попробовать перед этой строкой сделать проверку на пустой nums2 и если он пустой, то просто вернуть nums1

## 5:
```go
func findDifference(nums1, nums2 []int) []int {
    result := make([]int, 0, len(nums1))

    p1 := 0
    p2 := 0

    if len(nums2) == 0 {
        return nums1
    }

    nums2LastVal := nums2[len(nums2) - 1]

    for p1 < len(nums1) {
        if p2 >= len(nums2) && nums2LastVal == nums1[p1] {
            p1++
            continue
        }

        if p2 >= len(nums2) {
            result = append(result, nums1[p1])
            p1++
            continue
        }

        if nums1[p1] < nums2[p2] {
            result = append(result, nums1[p1])
            p1++
        } else if nums1[p1] > nums2[p2] {
            p2++
        } else {
            p1++
            p2++
        }
    }

    return result
}
```

Ошибка: Неправильный ответ

Входные данные

nums1 = [-3,-2,-2,-2,-1,-1,-1]; nums2 = [-3,-2,-1]; 
Ожидаемый результат

[]
Результат исполнения

[-2,-2]

Тут остановился...
