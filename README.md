#Rock-Paper-Scissor Game

import random as r

game_inventory = ['rock', 'paper', 'scissor']
applicable_choice = ['1', '2', '3']
user_points = 0
computer_points = 0

#creating a random choice for computer
comp_choice = r.randint(1, 3)

#message variables
choose_rock = "'1' for Rock"
choose_paper = "'2' for Paper"
choose_scissor = "'3' for Scissor"
game_rule = f"\nEnter:\n{choose_rock}\n{choose_paper}\n{choose_scissor}"

#code to decide who won an individual round
def gameCode(choice1, choice2):
  if choice1 == choice2:
    return("draw")
  elif choice1 == 1 and choice2 == 3:
    return('user')
  elif choice1 == 3 and choice2 == 1:
    return('computer')
  elif choice1 > choice2:
    return('user')
  else:
    return('computer')


while True:
  print("Let's play Rock-Paper-Scissor")
  user_name = input("\nPlease enter your name: ")
  #user can play for 5 rounds at one time
  i = 1
  while i in range(4):
    print(game_rule)
    #list of options to validate choices
    user_choice = input("\nEnter your choice: ") #Asking the user to enter his choice
    if user_choice not in applicable_choice: #if user choice is invalid
      print("\nInvalid input! Please try again")
      continue
    else:
      print(f"\nRound {i}")                   #if user choice is valid
      user_choice = int(user_choice)         #type casting input 'str' to 'int'
      computer_choice = comp_choice
      result = gameCode(user_choice, computer_choice)
      if result == 'draw':
        print(f"\n{user_name.title()} chose: {game_inventory[user_choice - 1].title()}")
        print(f"Computer chose: {game_inventory[computer_choice - 1].title()}")
        print("\nIt's a Draw!")
      elif result == 'user':
        print(f"\n{user_name.title()} chose: {game_inventory[user_choice - 1].title()}")
        print(f"Computer chose: {game_inventory[computer_choice - 1].title()}")
        print(f"\n{user_name.title()} gets a point")
        user_points += 1
        print(f"{user_name.title()} points:{user_points}")
        print(f"Computer points:{computer_points}")
      else:
        print(f"\n{user_name.title()} chose: {game_inventory[user_choice - 1].title()}")
        print(f"Computer chose: {game_inventory[computer_choice - 1].title()}")
        print(f"\nComputer gets a point")
        computer_points += 1
        print(f"{user_name.title()} points:{user_points}")
        print(f"Computer points:{computer_points}")
      i += 1
  #After 5 rounds declare the winner
  if user_points > computer_points:
    print(f"\n{user_name.title()}'s point: is {user_points}")
    print(f"Computer's point: is {computer_points}")
    print(f"{user_name.title()} Wins!")
  elif user_points == computer_points:
    print(f"\n{user_name.title()}'s point: is {user_points}")
    print(f"Computer's point: is {computer_points}")
    print(f"It's a tie between {user_name.title()} and Computer!")
  else:
    print(f"\n{user_name.title()}'s point: is {user_points}")
    print(f"Computer's point: is {computer_points}")
    print(f"Computer wins!")
  #Ask user if he wants to play again?
  play_again = input("\nWould you like to play again? (Y/N): ")
  if play_again == "Y" or play_again == "y":
    continue
  elif play_again == "N" or play_again == "n":
    break
  else: #If user enteres an invalid input
    print("\nInvalid input! Please try again")

