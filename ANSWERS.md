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

![state-machine-1 ans](/assets/state-machine-1.jpeg)
