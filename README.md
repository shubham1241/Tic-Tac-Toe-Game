# Tic-Tac-Toe-Game
## it is just a tic-tac-toe game created using python which includes 2-users at one time 



def display_board(board):
    x=0
    for num in range(0,3):
        print('      |            |           ')
        print(f'{board[x]}     |      {board[x+1]}     |   {board[x+2]}')
        print('      |            |          ')
        if num ==2:
            break
        else:
            print('---------------------------')
        x+=3
p1="X"
p2="O"
def welcome(p1,p2):
    p1=input('PLAYER1- Enter your choice symbol? X or O -> \n')
    if not (p1.upper()=='X' or p1.upper()=='O'):
        print ('You entered a wrong choice please re-enter the symbol')
        welcome(p1,p2)
    else:
        if p1.upper()=='X':
            p2='O'
        else:
            p2='X'
    return (p1.upper(),p2.upper())
a=False
def check(a,board,r):
        if board[0]==board[1]==board[2]==r:
            a=True
        elif board[3]==board[4]==board[5]==r:
            a=True
        elif board[6]==board[7]==board[8]==r:
            a=True
        elif board[0]==board[3]==board[6]==r:
            a=True
        elif board[1]==board[4]==board[7]==r:
            a=True
        elif board[2]==board[5]==board[8]==r:
            a=True
        elif board[0]==board[4]==board[8]==r:
            a=True
        elif board[2]==board[4]==board[6]==r:
            a=True
        else:
            a=False
        return (a,board,r)
def insert_to_board(board,a):
    print(f'{a} symbol chance')
    x1=int(input("Enter the number to place your marker: 1-9 \n"))
    while x1<10:
        if board[x1-1].upper()=='X':
            pass
        elif board[x1-1].upper()=='O':
            pass
        else:
            board[x1-1]=a
        return board
import random
def randomise():
    if random.randint(1,2)==1:
        return p1
    else:
        return p2    
def check_full_board(board):
    if " " in board:
        return True
    else:
        print("The match has been tied")
        return False
def noreplay():
    from IPython.display import clear_output
    clear_output()
    print("\n\nThank you for playing game----Author-Shubham singh\n\n")
x7=False
def replay(board,x7):
        a12=input("Do you want to play game again ")
        if(a12.upper()=="YES"):
            board=[' ',' ',' ',' ',' ',' ',' ',' ',' ']
            x7=True
        return (board,x7)
print("Welcome to Tic-Tac-Toe")
p1='X'
p2='O'
r=randomise()
if r=="O":
    r1="X"
else:
    r1="O"           
def game():
    board=[' ',' ',' ',' ',' ',' ',' ',' ',' ']
    welcome(p1,p2)
    print(f'The player with this symbol {r} go first\n')
    x=input("Are you ready to play:- Reply Yes or No-> \n\n")
    if x.upper()=='YES':
            while check_full_board(board):
                print("\n\n\n\n\n\n")
                display_board(board)
                print("\n\n\n\n")
                insert_to_board(board,r)
                print("\n\n\n\n")
                display_board(board)
                from IPython.display import clear_output
                clear_output()
                x4=check(a,board,r)[0]
                if x4==True:
                    print(f"The player with this symbol {check(a,board,r)[2]} won the game")
                    a5=replay(board,x7)
                    if a5[1]==True:
                        board=a5[0]
                        game()
                    else:
                        noreplay()
                        break
                    break     
                display_board(board)
                insert_to_board(board,r1)
                from IPython.display import clear_output
                clear_output()
                x4=check(a,board,r1)[0]
                if x4==True:
                    print(f"The player with this symbol {check(a,board,r)[2]} won the game")
                    a5=replay(board,x7)
                    if a5[1]==True:
                        board=a5[0]
                        game()
                    else:
                        noreplay()
                        break
                    break
                if check_full_board(board)=='The match has been tied':
                    replay()
    else:
        noreplay()
game()   
   
      

    
