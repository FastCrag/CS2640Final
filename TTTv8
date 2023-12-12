#Craig Fast, Jonathan Bae, Thanh Dang, Edgar Ortiz
#Tic-Tac-Toe V8

.data
hline: .asciiz "---+---+---"
vline: .asciiz "|"
empty: .asciiz "   "
newline: .asciiz "\n"
O: .asciiz " O "
X: .asciiz " X "

#Strings for gameplay
start: .asciiz "Welcome to Tic-Tac-Toe. \nYou will be playing as X. \nBelow are the numbers for each cell on the board.\n"
row1: .asciiz " 1 | 2 | 3 \n"
row2: .asciiz " 4 | 5 | 6 \n"
row3: .asciiz " 7 | 8 | 9 \n"
choice1: .asciiz "\nPlayer 1, please enter the number of the cell you would like to play in: "
choice2: .asciiz "\nPlayer 2, please enter the number of the cell you would like to play in: "
invalid: .asciiz "\nYour input was invalid. Please enter an integer between 1-9 that has not been played."
player1_win_msg: .asciiz "\nCongratulations. PLAYER 1 WINS!"
player2_win_msg: .asciiz "\nCongratulations. PLAYER 2 WINS!"
cats_game_msg: .asciiz "\nWelp that's a cats game. No one wins!"
play_again_msg: .asciiz "\nWould you like to play again? (Answer 1 to play again. Anything else will end the game)"
goodbye: .asciiz "\nThanks for playing! Have a great day!"



.text
main:
	#set up the registers for the board
	la $t0, empty
	la $t1, empty
	la $t2, empty
	la $t3, empty
	la $t4, empty
	la $t5, empty
	la $t6, empty
	la $t7, empty
	la $t8, empty
	la $t9, empty
	#reset the turn counter to 0
	li $s7, 0
	
game_start:	
	#explain the game
	la $a0, start		#explains the rules
	li $v0, 4		#the syscode 4 is to display a string
	syscall
	
	#display the board numbers
	la $a0, row1		#displays the cell numbers for row1
	li $v0, 4		#the syscode 4 is to display a string	
	syscall
	la $a0, hline		#displays a horizontal line separator
	li $v0, 4		#the syscode 4 is to display a string	
	syscall
	la $a0, newline		#new line
	li $v0, 4 		#the syscode 4 is to display a string
	syscall 
	la $a0, row2		#displays the cell numbers for row2
	li $v0, 4		#the syscode 4 is to display a string	
	syscall
	la $a0, hline		#displays a horizontal line separator
	li $v0, 4		#the syscode 4 is to display a string	
	syscall
	la $a0, newline		#new line
	li $v0, 4 		#the syscode 4 is to display a string
	syscall 
	la $a0, row3		#displays the cell numbers for row3
	li $v0, 4		#the syscode 4 is to display a string	
	syscall

player1_turn:
	#give player 1 a choice where to play
	la $a0, choice1		#displays a message to choose a cell
	li $v0, 4		#the syscode 4 is to display a string	
	syscall
	#read the value that the player entered
	li $v0, 12		# 12 is the syscall code to read an string
	syscall
	move $s0, $v0		# move the value of $v0 to $s0
	jal set_cell_X		#set desired cell to display an X
	jal show_board		#Show the current state of the board
	jal check_win		#Check whether the player won with this move
	add $s7, $s7, 1		#Adds 1 to the turn counter
	beq $s7, 9, cats_game	#if there has been 9 moves and no winner then jump to cats game
	j player2_turn		#Go to the next players turn
	
player2_turn:
	#give player 2 a choice where to play
	la $a0, choice2		#displays a horizontal line separator
	li $v0, 4		#the syscode 4 is to display a string	
	syscall
	#read the value that the player entered
	li $v0, 12		# 12 is the syscall code to read an string
	syscall
	move $s0, $v0		# move the value of i from $v0, $s0
	jal set_cell_O		#set desired cell to display an X
	jal show_board		#Show the current state of the board
	jal check_win		#Check whether the player won with this move
	add $s7, $s7, 1		#Adds 1 to the turn counter
	beq $s7, 9, cats_game	#if there has been 9 moves and no winner then jump to cats game
	j player1_turn
			#Go to the next players turn
			
exit: 
	la $a0, goodbye	#displays the goodbye message
	li $v0, 4		#the syscode 4 is to display a string	
	syscall
	li $v0, 10		#exits the game
	syscall
	
set_cell_X:
	#Check if user wants to play in cell 1
	bne $s0, '1', check2	#if user input is not 1 then go to check 2
		bne $t1, $t0, invalid_input1	#if the cell is already taken go to invalid input
		la $t1, X	#if user input is 1 then set cell to X
		jr $ra		#end set_cell_X for this turn
	#Check if user wants to play in cell 2
	check2:
	bne $s0, '2', check3	#if user input is not 2 then go to check 3
		bne $t2, $t0, invalid_input1	#if the cell is already taken go to invalid input
		la $t2, X	#if user input is 2 then set cell to X
		jr $ra		#end set_cell_X for this turn
	#Check if user wants to play in cell 3
	check3:
	bne $s0, '3', check4	#if user input is not 3 then go to check 4
		bne $t3, $t0, invalid_input1	#if the cell is already taken go to invalid input
		la $t3, X	#if user input is 3 then set cell to X
		jr $ra		#end set_cell_X for this turn
	#Check if user wants to play in cell 4
	check4:
	bne $s0, '4', check5	#if user input is not 4 then go to check 5
		bne $t4, $t0, invalid_input1	#if the cell is already taken go to invalid input
		la $t4, X	#if user input is 4 then set cell to X
		jr $ra		#end set_cell_X for this turn
	#Check if user wants to play in cell 5
	check5:
	bne $s0, '5', check6	#if user input is not 5 then go to check 6
		bne $t5, $t0, invalid_input1	#if the cell is already taken go to invalid input
		la $t5, X	#if user input is 5 then set cell to X
		jr $ra		#end set_cell_X for this turn
	#Check if user wants to play in cell 6
	check6:
	bne $s0, '6', check7	#if user input is not 6 then go to check 7
		bne $t6, $t0, invalid_input1	#if the cell is already taken go to invalid input
		la $t6, X	#if user input is 6 then set cell to X
		jr $ra		#end set_cell_X for this turn
	#Check if user wants to play in cell 7
	check7:
	bne $s0, '7', check8	#if user input is not 7 then go to check 8
		bne $t7, $t0, invalid_input1	#if the cell is already taken go to invalid input
		la $t7, X	#if user input is 7 then set cell to X
		jr $ra		#end set_cell_X for this turn
	#Check if user wants to play in cell 8
	check8:
	bne $s0, '8', check9	#if user input is not 8 then go to check 9
		bne $t8, $t0, invalid_input1	#if the cell is already taken go to invalid input
		la $t8, X	#if user input is 8 then set cell to X
		jr $ra		#end set_cell_X for this turn
	#Check if user wants to play in cell 9
	check9:
	bne $s0, '9', invalid_input1	#if user input is not 9 then go to invalid_input1
		bne $t9, $t0, invalid_input1	#if the cell is already taken go to invalid input
		la $t9, X	#if user input is 9 then set cell to X
		jr $ra		#end set_cell_X for this turn
	invalid_input1:
	#display board
	#display invalid number message
	la $a0, invalid		#sets the value of $a0 to the address of invalid
	li $v0, 4		#the syscode 4 is to display a string	
	syscall
	#return to player1_turn
	j player1_turn
	

	
set_cell_O:
	#Check if user wants to play in cell 1
	bne $s0, '1', p2check2	#if user input is not 1 then go to check 2
		bne $t1, $t0, invalid_input2	#if the cell is already taken go to invalid input
		la $t1, O	#if user input is 1 then set cell to X
		jr $ra		#end set_cell_X for this turn
	#Check if user wants to play in cell 2
	p2check2:
	bne $s0, '2', p2check3	#if user input is not 2 then go to check 3
		bne $t2, $t0, invalid_input2	#if the cell is already taken go to invalid input
		la $t2, O	#if user input is 2 then set cell to X
		jr $ra		#end set_cell_X for this turn
	#Check if user wants to play in cell 3
	p2check3:
	bne $s0, '3', p2check4	#if user input is not 3 then go to check 4
		bne $t3, $t0, invalid_input2	#if the cell is already taken go to invalid input
		la $t3, O	#if user input is 3 then set cell to X
		jr $ra		#end set_cell_X for this turn
	#Check if user wants to play in cell 4
	p2check4:
	bne $s0, '4', p2check5	#if user input is not 4 then go to check 5
		bne $t4, $t0, invalid_input2	#if the cell is already taken go to invalid input
		la $t4, O	#if user input is 4 then set cell to X
		jr $ra		#end set_cell_X for this turn
	#Check if user wants to play in cell 5
	p2check5:
	bne $s0, '5', p2check6	#if user input is not 5 then go to check 6
		bne $t5, $t0, invalid_input2	#if the cell is already taken go to invalid input
		la $t5, O	#if user input is 5 then set cell to X
		jr $ra		#end set_cell_X for this turn
	#Check if user wants to play in cell 6
	p2check6:
	bne $s0, '6', p2check7	#if user input is not 6 then go to check 7
		bne $t6, $t0, invalid_input2	#if the cell is already taken go to invalid input
		la $t6, O	#if user input is 6 then set cell to X
		jr $ra		#end set_cell_X for this turn
	#Check if user wants to play in cell 7
	p2check7:
	bne $s0, '7', p2check8	#if user input is not 7 then go to check 8
		bne $t7, $t0, invalid_input2	#if the cell is already taken go to invalid input
		la $t7, O	#if user input is 7 then set cell to X
		jr $ra		#end set_cell_X for this turn
	#Check if user wants to play in cell 8
	p2check8:
	bne $s0, '8', p2check9	#if user input is not 8 then go to check 9
		bne $t8, $t0, invalid_input2	#if the cell is already taken go to invalid input
		la $t8, O	#if user input is 8 then set cell to X
		jr $ra		#end set_cell_X for this turn
	#Check if user wants to play in cell 6
	p2check9:
	bne $s0, '9', invalid_input2	#if user input is not 9 then go to invalid_input1
		bne $t9, $t0, invalid_input2	#if the cell is already taken go to invalid input
		la $t9, O	#if user input is 9 then set cell to X
		jr $ra		#end set_cell_X for this turn
	invalid_input2:
	#display invalid number message
	la $a0, invalid		#sets the value of $a0 to the address of invalid
	li $v0, 4		#the syscode 4 is to display a string	
	syscall
	#return to player2_turn
	j player2_turn
	
	
check_win:
	#Check row1 (1,2,3)	
	row1_check_win:
		beq $t1, $t0, row2_check_win		#check if the cells are not empty
		bne $t1, $t2, row2_check_win		#if they are not equal then check next possibility
		bne $t2, $t3, row2_check_win		#if they are not equal then check next possibility
		move $s1, $t1				#set $s1 to whatever symbol won
		j winner				#if all are equal then jump to winner
	#Check row2 (4,5,6)
	row2_check_win:
		beq $t4, $t0, row3_check_win		#check if the cells are not empty
		bne $t4, $t5, row3_check_win		#if they are not equal then check next possibility
		bne $t5, $t6, row3_check_win		#if they are not equal then check next possibility
		move $s1, $t4				#set $s1 to whatever symbol won
		j winner				#if all are equal then jump to winner
	#Check row3 (7,8,9)
	row3_check_win:
		beq $t7, $t0, column1_check_win		#check if the cells are not empty
		bne $t7, $t8, column1_check_win		#if they are not equal then check next possibility
		bne $t8, $t9, column1_check_win		#if they are not equal then check next possibility
		move $s1, $t7				#set $s1 to whatever symbol won
		j winner				#if all are equal then jump to winner
	
	#Check column1(1,4,7)
	column1_check_win:
		beq $t1, $t0, column2_check_win		#check if the cells are not empty
		bne $t1, $t4, column2_check_win		#if they are not equal then check next possibility
		bne $t4, $t7, column2_check_win		#if they are not equal then check next possibility
		move $s1, $t1				#set $s1 to whatever symbol won
		j winner				#if all are equal then jump to winner
	
	#Check column2(2,5,8)
	column2_check_win:
		beq $t2, $t0, column3_check_win		#check if the cells are not empty
		bne $t2, $t5, column3_check_win		#if they are not equal then check next possibility
		bne $t5, $t8, column3_check_win		#if they are not equal then check next possibility
		move $s1, $t2				#set $s1 to whatever symbol won
		j winner				#if all are equal then jump to winner
	
	#Check column3(3,6,9)
	column3_check_win:
		beq $t3, $t0, diagonal1_check_win	#check if the cells are not empty
		bne $t3, $t6, diagonal1_check_win	#if they are not equal then check next possibility
		bne $t6, $t9, diagonal1_check_win	#if they are not equal then check next possibility
		move $s1, $t3				#set $s1 to whatever symbol won
		j winner				#if all are equal then jump to winner
	
	#Check diagonal1(1,5,9)
	diagonal1_check_win:
		beq $t1, $t0, diagonal2_check_win	#check if the cells are not empty
		bne $t1, $t5, diagonal2_check_win	#if they are not equal then check next possibility
		bne $t5, $t9, diagonal2_check_win	#if they are not equal then check next possibility
		move $s1, $t1				#set $s1 to whatever symbol won
		j winner				#if all are equal then jump to winner
	
	#Check diagonal2(3,5,7)
	diagonal2_check_win:
		beq $t3, $t0, no_winner			#check if the cells are not empty
		bne $t3, $t5, no_winner			#if they are not equal then return to players turn
		bne $t5, $t7, no_winner			#if they are not equal then return to players turn
		move $s1, $t3				#set $s1 to whatever symbol won
		j winner				#if all are equal then jump to winner
		
	no_winner:
		jr $ra					#return to the player's turn
	winner:
		la $s2, X				#set $s2 to the X value
		bne $s1, $s2, player2_wins		#if $s1 is not equal to X then player2 wins
	player1_wins:					#if $s1 is equal to X then player 1 wins
		la $a0, player1_win_msg			#displays the winning message for player 1
		li $v0, 4				#the syscode 4 is to display a string	
		syscall
		j play_again
	player2_wins:
		la $a0, player2_win_msg			#displays the winning message for player 2
		li $v0, 4				#the syscode 4 is to display a string	
		syscall
		j play_again
#if there has been 9 moves and no winner then its a cats game
cats_game:
	la $a0, cats_game_msg				#displays the cats game message
	li $v0, 4					#the syscode 4 is to display a string	
	syscall
	j play_again
#Asks the user if they would like to play again
play_again:
	la $a0, play_again_msg				#displays the play again question
	li $v0, 4					#the syscode 4 is to display a string	
	syscall
	#read user input
	li $v0, 12					#12 is the syscall code to read an string
	syscall
	bne $v0, '1', exit				#if the user does not input 1, exit the game
	j main						#restart the game if user inputs 1
	
		
#Shows the current state of the board
show_board:
	#add next line spacing
	la $a0, newline
	li $v0, 4
	syscall
	#1
	la $a0, ($t1)		#load the address of $t1 into the register
	li $v0, 4 		#the syscode 4 is to display a string
	syscall 
	la $a0, vline		#load the address of the output msg into the register $a0
	li $v0, 4 		#the syscode 4 is to display a string
	syscall 
	#2
	la $a0, ($t2)		#load the address of $t2 into the register
	li $v0, 4 		#the syscode 4 is to display a string
	syscall 
	la $a0, vline		#load the address of the output msg into the register $a0
	li $v0, 4		#the syscode 4 is to display a string
	syscall 
	#3
	la $a0, ($t3)		#load the address of $t3 into the register
	li $v0, 4		#the syscode 4 is to display a string
	syscall 
	# new line
	la $a0, newline		#new line
	li $v0, 4 		#the syscode 4 is to display a string
	syscall 
	#Create horizontal line
	la $a0, hline		#horizontal line
	li $v0, 4 		#the syscode 4 is to display a string
	#call syscall to create line across display field
	syscall 
	# new line
	la $a0, newline		#new line
	li $v0, 4 		#the syscode 4 is to display a string
	syscall 
	#4
	la $a0, ($t4)		#load the address of $t4 into the register
	li $v0, 4 		#the syscode 4 is to display a string
	syscall 
	la $a0, vline		#load the address of the output msg into the register $a0
	li $v0, 4 		#the syscode 4 is to display a string
	syscall 
	#5
	la $a0, ($t5)		#load the address of $t5 into the register
	li $v0, 4		 #the syscode 4 is to display a string
	syscall 
	la $a0, vline		#load the address of the output msg into the register $a0
	li $v0, 4 		#the syscode 4 is to display a string
	syscall 
	#6
	la $a0, ($t6)		#load the address of $t6 into the register
	li $v0, 4 		#the syscode 4 is to display a string
	syscall 
	# new line
	la $a0, newline		#new line
	li $v0, 4 		#the syscode 4 is to display a string
	syscall 
	#Create horizontal line
	la $a0, hline		#horizontal line
	li $v0, 4 		#the syscode 4 is to display a string
	#call syscall to create line across display field
	syscall 
	# new line
	la $a0, newline		#new line
	li $v0, 4 		#the syscode 4 is to display a string
	syscall 
	#7
	la $a0, ($t7)		#load the address of $t7 into the register
	li $v0, 4 		#the syscode 4 is to display a string
	syscall 
	la $a0, vline		#load the address of the output msg into the register $a0
	li $v0, 4 		#the syscode 4 is to display a string
	syscall 
	#8
	la $a0, ($t8)		#load the address of $t8 into the register
	li $v0, 4 		#the syscode 4 is to display a string
	syscall 
	la $a0, vline		#load the address of the output msg into the register $a0
	li $v0, 4 		#the syscode 4 is to display a string
	syscall 
	#9
	la $a0, ($t9)		#load the address of $t9 into the register
	li $v0, 4 		#the syscode 4 is to display a string
	syscall 
	
	jr $ra
	
	

	
