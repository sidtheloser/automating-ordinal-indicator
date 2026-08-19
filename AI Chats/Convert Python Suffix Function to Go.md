# Convert Python Suffix Function to Go

*Created: 8/19/2026, 2:43:49 AM*

---

**You**

```python
def oi(num: int) -> str:
	num = abs(num)

	tens: int = num % 100 // 10
	
	if tens == 1:
		return "th"
	
	ones: int = num % 10
	
	match ones:
		case 1:
			return "st"
		case 2:
			return "nd"
		case 3:
			return "rd"
		case _:
			return "th"
```
convert to go

---

**Assistant**

Here's the Go conversion:

```go
func oi(num int) string {
	num = abs(num)

	tens := (num % 100) / 10

	if tens == 1 {
		return "th"
	}

	ones := num % 10

	switch ones {
	case 1:
		return "st"
	case 2:
		return "nd"
	case 3:
		return "rd"
	default:
		return "th"
	}
}
```

This is the classic ordinal-suffix function (e.g. `1st`, `2nd`, `3rd`, `11th`, `21st`).

**Notes on the conversion:**

- **`abs()`** — Go's standard library provides `math.Abs` for floats, but for integers you need a small helper. The simplest is:
  ```go
  func abs(n int) int {
  	if n < 0 {
  		return -n
  	}
  	return n
  }
  ```
  Or use the bit hack `n * (((n >> 31) << 1) + 1)` if you want it inline (works on 32-bit ints). Note `math.Abs` requires a float64, so it's not a drop-in.

- **`match`/`case`** → Go's `switch`/`case` with `default` (Go doesn't have pattern matching; `switch` on a value is the equivalent here).

- **Type annotations** like `tens: int` become `:=` (short variable declaration), which infers the type automatically.

- **`//` integer division** — Go's `/` already does integer division when both operands are integers, so no special operator is needed. The parentheses around `num % 100` are just for clarity; Go follows standard precedence (`%` and `/` have the same precedence and are left-associative), so `num % 100 / 10` works identically.

---

