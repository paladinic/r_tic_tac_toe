# Tic-Tac-Toe in R (ttt)
### A simple interface to tic-tac-toe
#### Installation:
`devtools::install_github("paladinic/r_tic_tac_toe")`
#### Example:
```
R> ttt::start()

it's x's turn
__________________

  c1 c2 c3
1  #  #  #
2  #  #  #
3  #  #  #
```
```
R> row: 2
R> col: 3

it's o's turn
__________________

  c1 c2 c3
1  #  #  #
2  #  #  x
3  #  #  #
```
```
R> row: 2
R> col: 1

it's x's turn
__________________

  c1 c2 c3
1  #  #  #
2  o  #  x
3  #  #  #

```
...
#### Game end:
```
player  x  won
  c1 c2 c3
1  x  o  x
2  o  o  x
3  #  #  x
GAME OVER
```
