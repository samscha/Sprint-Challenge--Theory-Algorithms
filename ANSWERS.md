# Answers

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

  ![state-machine-1](/Sprint-Challenge--Theory-Algorithms/assets/state-machine-1.jpeg)

* A lion can be sleeping, eating, hunting, or preening. Draw a state
  machine diagram for the lion and label the transition events that
  cause state transitions.

  ![state-machine-2](/Sprint-Challenge--Theory-Algorithms/assets/state-machine-2.png)

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

  ![state-machine-3](/Sprint-Challenge--Theory-Algorithms/assets/state-machine-3.jpeg)
