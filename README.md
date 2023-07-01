# Mini Max with alpha beta pruning

## Min Max without Alpha Beta

```python
function MINIMAX-SEARCH(game, state) returns an action
  player <- game.TO-MOVE(state)
  value, move <- MAX-VALUE(game, state)
  return move

function MAX-VALUE(game, state) returns a (utility, move) pair
	if game.IS-TERMINAL(state) then return (game.UTILITY(state, player), null)
	v, move <- (-∞, null)
	for each a in game. ACTIONS(state) do
    v2, a2 <- MIN-VALUE(game, game.RESULT(state, a))
    if v2 > v then
      v, move <- (v2, a)
  return v, move

function MIN-VALUE(game, state) returns a (utility, move) pair
	if game.IS-TERMINAL(state) then return (game.UTILITY(state, player), null)
	v, move <- (+∞, null)
	for each a in game. ACTIONS(state) do
    v2, a2 <- MAX-VALUE(game, game.RESULT(state, a))
    if v2 < v then
      v, move <- (v2, a)
  return v, move
```

## Min Max with Alpha Beta

```python
function APHA-BETA-SEARCH(game, state) returns an action
  player <- game.TO-MOVE(state)
  value, move <- MAX-VALUE(game, state, -∞, +∞)
  return move

function MAX-VALUE(game, state, α, β) returns a (utility, move) pair
	if game.IS-TERMINAL(state) then return (game.UTILITY(state, player), null)
	v <- -∞
	for each a in game. ACTIONS(state) do
    v2, a2 <- MIN-VALUE(game, game.RESULT(state, a), α, β)
    if v2 > v then
      v, move <- (v2, a)
      α <- MAX(α, v)
    if v >= to β then return (v, move)
  return v, move

function MIN-VALUE(game, state, α, β) returns a (utility, move) pair
	if game.IS-TERMINAL(state) then return (game.UTILITY(state, player), null)
	v <- +∞
	for each a in game. ACTIONS(state) do
    v2, a2 <- MIN-VALUE(game, game.RESULT(state, a), α, β)
    if v2 < v then
      v, move <- (v2, a)
      β <- MIN(β, v)
    if v <= α then return (v, move)
  return v, move
```
