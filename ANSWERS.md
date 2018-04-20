# Answers

## Theory

* Single regex that matches either of these:

  antelope rocks out

  antelopes rock out

  (1) `/(antelopes rock out|antelope rocks out)/g`

  (2) `/(?=antelopes)antelopes rock out|antelope rocks out/g`

* Regex that matches either of:

  goat
  moat

  but not:

  boat

  (1) `\b[gm]oat\b`

* Regex that matches dates in YYYY-MM-DD format. (Year can be 1-4 digits, and
  month and day can each be 1-2 digits). This does not need to verify the date
  is correct (e.g 33333-33-33 can match).

  (1) `\b[0-9]{1,4}-[0-9]{1,2}-[0-9]{1,2}\b`

* Draw a state machine that corresponds to the following regex:

      ab*c+d?[ef]

  ![state-machine-1](/assets/state-machine-1.jpeg)

* A lion can be sleeping, eating, hunting, or preening. Draw a state
  machine diagram for the lion and label the transition events that
  cause state transitions.

  ![state-machine-2](/assets/state-machine-2.png)

* The VT-100 terminal (console) outputs text to the screen as it
  receives it over the wire. One exception is that when it receives an
  ESC character (ASCII 27), it goes into a special mode where it looks
  for commands to change its behavior. For example:

      ESC[12;45f

  moves the cursor to line 12, column 45.

      ESC[1m

  changes the font to bold.

  * Come up with regexes for the two above sequences. The one to set the
    cursor position should accept any digits for the row and column. The
    bold sequence need only accept `1` (and is a trivial regex). (ESC is
    a single character which can be represented with `\e` in the regex.)

    (1) `/(\e\[[0-9][0-9];[0-9][0-9]f)/g`

    (2) `(\e\[1m)/g`

  * Draw a state machine diagram for a VT-100 that can consume regular
    character sequences as well as the two above ESC sequences.

  ![state-machine-3](/assets/state-machine-3.jpeg)

## Algorithms

#### Exercise I

a) `O(n)` = `O(n**3 / n**2)`

b) unknown. all elements of `array` might be greater than `x` -> runs forever (stuck at `i = 0` and `array[0] > x`)

c) `O(n**0.5 / 2)`

d) `O(n log n)` = `O((1 / (2**n) * n))` note: `1 / (2**n)` = `log n / log 2` but constants are ignored in `O(n)`

e) `O(n**3)`

f) `O(n)`

g) `O(n)`

#### Exercise II

a)

```
int find_max_difference(int arr[], int n)
{
  int max, min = arr[0];

  for (int i = 1; i < n; i++)
  {
    int num = arr[i];

    if (num > max)
    {
      max = num;
    }
    else if (num < min)
    {
      min = num;
    }
  }

  return max - min;
}
```

b) Start at floor `n/2`. This is the `current floor`. If the egg breaks, remember `high = current floor`, then go to `low + (current floor - low) / 2`. If the egg doesn't break, remember `low = current floow` and go to `current floor + (high - current floor) / 2`. Keep doing this until `low + 1 = current floor && high - 1 = current floor`. Then drop the egg. If it breaks, this is floor `f` where an egg will break if thrown off `f` or higher. If the egg doesn't break, then floor `f` is your `current floor + 1`.

`n` = 50

(1) start at floor 25 and drop egg.

`current floor = 25`

egg breaks.

`high = current floor = 25`

`current floor = low + (current floor - low) / 2 = 0 + (25 - 0) / 2 = 13` (round up)

(2) go to floor 13 (`current floor`) and drop egg.

egg breaks.

`high = current floor = 13`

`current floor = low + (current floor - low) / 2 = 0 + (13 - 0) / 2 = 7` (round up)

(3) go to floor 7 (`current floor`) and drop egg.

egg doesn't break.

`low = 13`

go to `current floor + (high - current floor) / 2 = 7 + (13 - 7) / 2 = 7 + 6/2 = 10`

`current floor = 10`

(4) go to floor 10 (`current floor`) and drop egg.

egg doesn't break.

`low = 10`

go to `current floor + (high - current floor) / 2 = 10 + (13 - 10) / 2 = 10 + 3/2 = 12`

`current floor = 12`

(5) go to floor 12 and drop egg.

egg breaks.

`high = current floor = 12`

`current floor = low + (current floor - low) / 2 = 10 + (12 - 10) / 2 = 11`

(6) `low = 10`, `low + 1 = current floor = high - 1`, `high = 12` drop the egg from floor 11.

egg doesn't break.

this means that floor `f` is `current + 1 = 12`. Thus, `f = 12`

#### Exercise III

a) Because `for each x in array` is specified, the runtime for this algorithm with a sorted array will still be `O(n)`.

b) Because `for each x in array` is specified, the runtime for this algorithm even with the median pivot will still be `O(n)`.
