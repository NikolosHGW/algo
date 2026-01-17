## 1:
```go
func fuzzyMatch(s string, t string) bool {
    p1 := 0
    p2 := 0

    for p1 < len(s) && p2 < len(t) {
        if s[p1] == t[p2] {
            p1++
            p2++
        } else {
            p2++
        }

        if p1 == len(s) - 1 {
            return true
        }
    }

    return false
}
```
Ошибка: Неправильный ответ
Входные данные: t = cartwheel; s = lw; 
Ожидаемый результат: false
Результат исполнения: true

Я указал условие, которое возвращает тру
```go
if p1 == len(s) - 1 {
    return true
}
```
после того, как инкрементировал указатель p1, и алгоритм решил, что это true, хотя чары совершенно неравны
