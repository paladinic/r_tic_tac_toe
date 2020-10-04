library(dplyr)

indexes = list(
  diag(T, 3, 3),
  diag(T, 3, 3)[, 3:1],
  matrix(data = c(T, F, F,
                  T, F, F,
                  T, F, F),
         nrow = 3),
  matrix(data = c(F, T, F,
                  F, T, F,
                  F, T, F),
         nrow = 3),
  matrix(data = c(F, F, T,
                  F, F, T,
                  F, F, T),
         nrow = 3),
  matrix(data = c(F, F, F,
                  F, F, F,
                  T, T, T),
         nrow = 3),
  matrix(data = c(F, F, F,
                  T, T, T,
                  F, F, F),
         nrow = 3),
  matrix(data = c(T, T, T,
                  F, F, F,
                  F, F, F),
         nrow = 3)
)
move = function(board,cell,player){
  cat(player,"\n")


  if(any(is.na(c(cell$row,cell$col)))){
    return(list(board = board,
                player = player,
                message = "either row or col are missing",
                game_over = F))
  }

  # if move out of bounds
  if(any(c(cell$row,cell$col)>3)){
    return(list(board = board,
         player = player,
         message = "move out of 3x3 bounds",
         game_over = F))
  }

  # get current value
  current_cell = board[cell$row,cell$col]

  # get next player
  if(player == "x"){
    next_player = "o"
  }else{
    next_player = "x"
  }

  # if cell empty
  if(current_cell == "#"){
    board[cell$row,cell$col] = player
    print(board)
  }

  else if(current_cell %in% c("x","o")){
    return(list(board = board,
                player = player,
                message = "move already made",
                game_over = F))
  }

  # look for victory
  for (i in indexes){
    if(all(board[i]==player)){
      return(list(board = board,
                  player = next_player,
                  message = c("GAME OVER"),
                  game_over = T))
    }
  }

  # look for tie
  if(all(board != "#")){
    return(list(board = board,
                player = next_player,
                message = c("GAME OVER - TIE"),
                game_over = T))
  }

  # if game not over
  return(list(board = board,
              player = next_player,
              message = "",
              game_over = F))
}
start = function(){
  cat("\014")
  player = "x"
  game_is_not_over = T
  board = data.frame(
    c1 = rep("#",3),
    c2 = rep("#",3),
    c3 = rep("#",3)
  )
  message = ""

  while(game_is_not_over){
    cat("\014")
    cat(message,"\n")
    cat("it's ",player,"'s turn\n\n",sep = "")
    cat("__________________\n\n\n")
    print(board)

    row = as.numeric(readline(prompt = "row: "))
    col = as.numeric(readline(prompt = "col: "))

    cell = list(row = row,
                col = col)

    move_result = move(board,cell,player)
    board = move_result$board
    message = move_result$message

    if(move_result$game_over){
      game_is_not_over = F
      cat("\014")
      cat("player ",player," won\n")
      print(board)
      cat(message)
    }

    player = move_result$player

  }
}
