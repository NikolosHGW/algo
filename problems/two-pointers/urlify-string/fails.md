## 1:
```go
func urlify(s []rune, k int) []rune {
    p1 := len(s) - 1
    p2 := k - 1

    for p2 < k {
        if s[p2] == ' ' {
            s[p1] = '0'
            p1--
            s[p1] = '2'
            p1--
            s[p1] = '%'
            p1--
        } else {
            s[p1], s[p2] = s[p2], s[p1]
            p1--
        }

        p2--
    }

    return s
}
```
Ошибка: Программа выбросила исключение
Входные данные

k = 11; s = ['h', 'e', 'l', 'l', 'o', ' ', 'w', 'o', 'r', 'l', 'd', '#', '#']; 
Исключение:

Stacktrace from panic: 
goroutine 1 [running]:
runtime/debug.Stack()
	/usr/local/miniconda3/envs/go1.23.5/go/src/runtime/debug/stack.go:26 +0x5e
main.runTest_algocode.func1.1()
	/box/main.go:204 +0x2f
panic({0x4e7420?, 0xc0001d82e8?})
	/usr/local/miniconda3/envs/go1.23.5/go/src/runtime/panic.go:785 +0x132
main.urlify({0xc0001e80c0?, 0x4ec2a0?, 0xc0001a9040?}, 0xc0001cdbc8?)
	/box/solution.go:8 +0xbb
main.runTest_algocode.func1(0xc0001aa0f0?, {0xc0001e80c0?, 0xc00019e130?, 0x1?}, 0x1?)
	/box/main.go:207 +0x75
main.runTest_algocode(0xc0001e6008, 0x4faaa0, 0x1)
	/box/main.go:209 +0x4dd
main.runTestWrapper_algocode.func1(0x47474a?, 0x5bd740?, 0x20?, {0x4f1e58, 0xf})
	/box/main.go:271 +0x65
main.runTestWrapper_algocode(0x51d268?, 0xc00019e020?, {0x4f1e58, 0xf})
	/box/main.go:275 +0x7a
main.RunTests_algocode({0xc0001c2000, 0x90a})
	/box/main.go:343 +0x15e
main.main()
	/box/main.go:362 +0x5d

По привычке поставил условие для цикла как для ситуаций, когда мы ставим начальные указатели в начало и двигаемся до конца, но в этом алгоритме я же ведь поставил указатели в конец, поэтому надо не забывать ставить условие по которому двигаемся к началу, то есть, я поставил условие, что пока быстрый указатель меньше, чем длина массива, то пусть цикл работает, а это значит, что раз я быстрый указатель на каждой итерации всегда уменьшаю, то и условие (p2 < len(s)) будет соблюдаться всегда, а от сюда бесконечный цикл. Надо ставить p2 >= 0
