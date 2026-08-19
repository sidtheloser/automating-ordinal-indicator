# Converting Ordinal Indicator to C#

*Created: 8/19/2026, 12:51:49 PM*

---

**You**

```python
def ordinal_indicator(num: int) -> str:
	num = abs(num)

	tens: int = (num % 100) // 10
	
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
convert to c#

---

**Assistant**

Here's the C# equivalent:

```csharp
static string OrdinalIndicator(int num)
{
    num = Math.Abs(num);

    int tens = (num % 100) / 10;

    if (tens == 1)
        return "th";

    int ones = num % 10;

    return ones switch
    {
        1 => "st",
        2 => "nd",
        3 => "rd",
        _ => "th"
    };
}
```

The C# **switch expression** (`=>` pattern) maps directly to Python's `match`/`case` here. Everything else translates one-to-one: `Math.Abs` for `abs`, integer division with `/` (since both operands are `int`), and the `_` discard pattern as the default case.

---

