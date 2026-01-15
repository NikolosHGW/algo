## 1:
```go
func maxArea(height []int) int {
    r := 0

    p1 := 0
    p2 := len(height) - 1

    for p1 < p2 {
        h1 := height[p1]
        h2 := height[p2]
        
        area := minHeight(h1, h2) * (p2 - p1)

        if area > r {
            r := area
        }

        if h1 < h2 {
            p1++
        } else {
            p2--
        }
    }

    return r
}

func minHeight(n1, n2 int) int {
    if n1 < n2 {
        return n1
    }

    return n2
}
```

Ошибка: # command-line-arguments ./solution.go:16:13: declared and not used: r

В самом начале я инициализировал переменную r, а затем при её обновлении внутри цикла вместо обновления опять инициализирую с помощью двоеточия, от сюда и ошибка про неиспользуемую переменную, так как я декларировал две r и ни одну не использую.
