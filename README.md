# Tic_Tac_Toe
First Repository
import random
#create board function

#This function creates the gameboard
def create_board(board):
	print('  |  |')
	print(' ' + board[1] + ' | ' + board[2] + ' | ' + board[3])
	print('_______')
	print('  |  |')
	print(' ' + board[4] + ' | ' + board[5] + ' | ' + board[6])
	print('  |  |')
	print('______')
	print('  |  |')
	print(' ' + board[7] + ' | ' + board[8] + ' | ' + board[9])
	print('  |  |')
	
#Decide wich player you want to be 
def player_selection():
	selection = ' '
	while not (selection == 'X' or selection == 'O'):
		print ('Would you like to be Player X or Player O?')
		selection = input().upper()
	if selection == 'X':
		return ['X', 'O']
	else:
		return ['O', 'X']
		
#The player will always go first.
def first_player():
	return 'You'

#Will determine the winner
def who_won(board,selection):
	#top row win
	return ((board[1] == selection and board[2] == selection and board[3] == selection)  or
	#middle row win
	(board[4] == selection and board[5] == selection and board[6] == selection) or 
	#bottom row win
	(board[7] == selection and board[8] == selection and board[9] == selection) or 
	#left side win
	(board[1] == selection and board[4] == selection and board[7] == selection) or 
	#middle win
	(board[2] == selection and board[5] == selection and board[8] == selection) or 
	#right side win
	(board[3] == selection and board[6] == selection and board[9] == selection) or 
	#diagnal win
	(board[3] == selection and board[5] == selection and board[7] == selection) or
	#diagnal win
	(board[1] == selection and board[5] == selection and board[9] == selection))

def free_spaces(board, move):
	return board[move] == ' ' 
	
def copy_board(board):
	copy = []
	
	for i in board:
		copy.append(i)
		
	return copy

#determines if gameboard is full 
def full_board(board):
	for i in range(1,10):
		if free_spaces(board, i):
			return False
	return True

def switch_player(other_player):
	other_player.reverse()
	return other_player
	
def make_move(board, selection, move):
	board[move] = selection

	
def opponent_move(board, opponent_selection):
	if opponent_selection == 'X':
		player_choice = 'O'
	else:
		player_choice ='X'
		
print('Let"s play a game 😈!')

# while True:
# Reset the board
board = [' '] * 10
player_choice, opponent_selection = player_selection()
turn = first_player()
print(turn + ' will go first.')
game_going = True
	
while game_going:
		if turn == 'player':
			create_board(board)
			move = player_move(board)
			make_move(board, player_selection, move)

			if who_won(board, player_selection):
				board(board)
				print('You win!')
				game_going = False
			else:
				if full_board(board):
					create_board(board)
					print('Tie! 😳')
					break
				else:
					turn = 'opponent'

		else:
        	  # Opponent's turn.
        	 move = opponent_move(board, opponent_selection)
        	 make_move(board, opponent_selection, move)

        	 if who_won(board, opponent_selection):
            	  create_board(board)
            	  print('You lose.')
            	  game_going = False
        	 else:
        	 	if full_board(board):
                	    create_board(board)
                	    print('The game is a tie!')
                	    break
         		else:
         			turn = 'player'
print('Game Over ! 😂')
