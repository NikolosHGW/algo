## 1:
```go
func findDifference(nums1 []int, nums2 []int) []int {
    result := make([]int, 0, len(nums1) + len(nums2))

    p1 := 0
    p2 := 0

    for p1 < len(nums1) || p2 < len(nums2) {
        if p1 >= len(nums1) && p2 < len(nums2) {
            result = append(result, nums2[p2])
            p2++
        }

        if p2 >= len(nums2) && p1 < len(nums1) {
            result = append(result, nums1[p1])
            p1++
        }

        if nums1[p1] < nums2[p2] {
            result = append(result, nums1[p1])
            p1++
        } else if nums2[p2] < nums1[p1] {
            result = append(result, nums2[p2])
            p2++
        } else {
            p1++
            p2++
        }
    }

    return result
}
```

Ошибка: # Программа выбросила исключение
Входные данные

nums1 = [1,5,7,9]; nums2 = [2,3,5,6,7,8]; 
Исключение:

Stacktrace from panic: 
goroutine 1 [running]:
runtime/debug.Stack()
	/usr/local/miniconda3/envs/go1.23.5/go/src/runtime/debug/stack.go:26 +0x5e
main.runTest_algocode.func1.1()
	/box/main.go:170 +0x2f
panic({0x4e8420?, 0xc0000187c8?})
	/usr/local/miniconda3/envs/go1.23.5/go/src/runtime/panic.go:785 +0x132
main.findDifference({0xc00010a1c0, 0x4, 0x0?}, {0xc00001c0c0, 0x6, 0xc00020dbc0?})
	/box/solution.go:20 +0x2a7
main.runTest_algocode.func1(0xc0001440f0?, {0xc00010a1c0?, 0xc000116138?, 0x1?}, {0xc00001c0c0?, 0xc00020dc18?, 0xc00020dc68?})
	/box/main.go:173 +0x83
main.runTest_algocode(0xc00021c008, 0x4fbab0, 0x1)
	/box/main.go:175 +0x516
main.runTestWrapper_algocode.func1(0x474eea?, 0x5be780?, 0x20?, {0x4f2e61, 0xf})
	/box/main.go:237 +0x65
main.runTestWrapper_algocode(0x51e348?, 0xc000116028?, {0x4f2e61, 0xf})
	/box/main.go:241 +0x7a
main.RunTests_algocode({0xc00016e500, 0x22db})
	/box/main.go:309 +0x15e
main.main()
	/box/main.go:328 +0x5d

Я использовал проверку выхода за пределы слайса так, что после этой проверки я иду и попадаю в условия, где использую эти вышедшие за пределы индексы к слайсу, от сюда и паника, поэтому я решил превратить всё в if else if, чтобы и проверки выхода за пределы тоже попали в эту цепочку условий, то бишь, чтобы только они выполнялись на итерации
