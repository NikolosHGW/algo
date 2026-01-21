## 1:
```go
func compare(s string, t string) bool {
    clearS := clear(s)
    clearT := clear(t)

    p1 := 0
    p2 := 0

    for p1 < len(clearS) && p2 < len(clearT) {
        if clearS[p1] != clearT[p2] {
            return false
        }
        p1++
        p2++
    }

    return len(clearS) == len(clearT)
}

func clear(anyString string) []rune {
    result := make([]rune, 0, len(anyString))

    for i := 0; i < len(anyString); i++ {
        if anyString[i] != '#' {
            result = append(result, anyString[i])
        } else if len(result) > 0 {
            result = result[:len(result)-1]
        }
    }

    return result
}
```
Ошибка: # command-line-arguments ./solution.go:26:37: cannot use anyString[i] (value of type byte) as rune value in argument to append

Я забыл, что, если обращаться к символам по индексу у строки, то тип символов будет байт, а не rune. Вот я не помню, как добраться до rune, может быть либо range по строке нужно делать, либо как-то кастовать

