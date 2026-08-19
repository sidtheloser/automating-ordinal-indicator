# Automating Ordinal Indicator

A guide on how to make a function for getting the ordinal indicator for integers ranging from -N to +N (where N is infinity).

> I used Kagi AI for this project. Chat data can be found in `AI Chats/` directory.

Well, let's look at an example/pattern first:

```
1st
2nd
3rd
4th
...
11th
12th
13th
...
21st
22nd
23rd
24th
...
31st
32nd
33rd
34th
...
111th
112th
113th
114th
...
```

It's easy to automate things once we notice a pattern in the problem we are trying to solve. In this case, I wanna make a Python or Go or C# function(s) that helps me add ordinal indicators in my high speed needs like debug messages or warning messages or race placements, all during runtime. So, let's come up with an algorithm that can handle things like this.

From the pattern/example I showed above, it's easy to spot that the numbers with 1 in the 10's position is always going to have "th" as it's ordinal indicator. 

The rest of the occurrences can be handled as follows:

- If word in 1's position is:
	- 1, then "st"
	- 2, then "nd"
	- 3, then "rd"
	- 0 or 4-9, then "th"

# First Implementation

The algorithm could look something like this:

## Python

Written entirely by me.

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

## Go

Written entirely by AI, and tested!

```go
func OrdianlIndicator(num int) string {
	num = Abs(num)
	
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

func Abs(n int) int {
	if n < 0 {
		return -n
	}
	return n
}
```

# C\#

Written entirely by AI, and **untested**!

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
