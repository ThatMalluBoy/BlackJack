import random
from colorama import Fore, Back, Style

def validateInput(prompt, choices):

  haveChoice = False
  choice = ""

  while (haveChoice == False):
    # ask for input
    choice = input(prompt)
    choice = choice.upper()

    # if input is valid, stop looping
    for x in choices:
      if choice == x:
        haveChoice = True

  return choice  

def instructions(tellInstruct):
  print("Welcome to the Card Game!")
  print("")
  print("Objective: The goal of the game is to get the closest to 21 (<21) or at 21")
  print("1. the deck is automatically shuffled by the computer")
  print("2. Each player recieves two cards at the beginning of the game")
  print("3. Each player takes turns playing, you can hit (take a card as many times as you want) or stay (skip your turn)")
  print("4. Player who is closest or at 21 wins (if a player goes over 21 you loose)")
  print("")
  print("================================================================")

def pickRandomCard(deck):
  # Generate a random index
  index = random.randrange(0, len(deck))
  # Remove and return the card at the random index
  return deck.pop(index)

def playerappend(numCards, playerDeck, shuffledDeck):
  newCard = ""
  for x in range(numCards):
    newCard = shuffledDeck.pop(0)
    playerDeck.append(newCard)

def calcTotal(playerDeck):
  deckAdd = 0
  for split in playerDeck:
    
    split = split[:-1]
    if split == 'K' or split == 'J' or split == 'Q':
      deckAdd += 10
    elif split == 'A':
      deckAdd += 1
    else:
      deckAdd += int(split)

  return deckAdd

def shuffle(cards):
  s = []
  while len(cards) > 0:
    card = pickRandomCard(deck)
    s.append(card)
  return s

def gameWinner(final1, final2):
  winner = 0
  if ((final1) > final2 and final1 <= 21) or (final2 > 21):
    winner = final1
    print('Congrats Player1! You won the game! ')
  elif ((final2) > final1 and int(final2) <= 21) or (final1 > 21):
    winner = final2
    print('Congrats Player2 you won the game! ')
  elif final1 > 21 and final2 > 21:
    print('That game was a tie! ')
  return winner  

  
# MAIN CODE

# Create a sample list of values (a deck of cards)
deck = ["2♥", "3♥", "4♥", "5♥", "6♥", "7♥", "8♥", "9♥", "10♥", "J♥", "Q♥", "K♥",
"A♥", "2♦", "3♦", "4♦", "5♦", "6♦", "7♦", "8♦", "9♦", "10♦", "J♦", "Q♦",
"K♦", "A♦", "2♣", "3♣", "4♣", "5♣", "6♣", "7♣", "8♣", "9♣", "10♣", "J♣",
"Q♣", "K♣", "A♣", "2♠", "3♠", "4♠", "5♠", "6♠", "7♠", "8♠", "9♠", "10♠",
"J♠", "Q♠", "K♠", "A♠"]

  
shuffled = shuffle(deck)
#userChoice = True
winPoint1 = 0
winPoint2 = 0
contPlaying = True

while contPlaying == True:

  instructPeople = ""
  instructions(instructPeople)

  #Initialize P1 hand to an empty list
  P1 = []
  #Initialize P2 hand to an empty list
  P2 = []


  #Deal two cards to P1 from the top of the shuffled deck
  playerappend(2, P1, shuffled)
  print("Player 1's Deck: " + str(P1))
  
  #Deal two cards to P2 from the top of the shuffled deck
  playerappend(2, P2, shuffled)
  print("Player 2's Deck: " + str(P2))

  print("========================================")

  print()
  
  deckVal1 = 0
  deckVal2 = 0
    
  #P1 turn
  print('Player 1s turn: ')
  
  # hand cards to P1
  contPicking = True
  while contPicking:
    choice = validateInput("Do you want to HIT or STAY:? ", ['HIT', 'STAY'])
    if (choice == 'HIT'):
      playerappend(1, P1, shuffled)
      print("This is now your deck: " + Fore.RED + str(P1))
      print(Style.RESET_ALL)
      deckVal1 += calcTotal(P1)
  
    else:
      contPicking = False
      deckVal1 += calcTotal(P1)
  #P2 turn
  print('Player 2s turn: ')
  
  # hand cards to P2
  contPicking = True
  while contPicking:
    choice = validateInput("Do you want to HIT or STAY:? ", ['HIT', 'STAY'])
    if (choice == 'HIT'):
      playerappend(1, P2, shuffled)
      print("This is now your deck: " + Fore.BLUE + str(P2))
      print(Style.RESET_ALL)
    
      deckVal2 += calcTotal(P1)
    else:
      contPicking = False
      deckVal2 += calcTotal(P1)

  print("========================================")
  
  print()
  
  winner = gameWinner(deckVal1, deckVal2)

  if winner == deckVal1:
    winPoint1 += 1
    print('Player 1 has ' + Fore.RED + str(winPoint1) + ' points')
    print(Style.RESET_ALL)
    print('Player 2 has ' + Fore.BLUE + str(winPoint2) + ' points')
    print(Style.RESET_ALL)
  elif winner == deckVal2:
    winPoint2 += 1
    print('Player 1 has ' + Fore.RED + str(winPoint1) + ' points')
    print(Style.RESET_ALL)
    print('Player 2 has ' + Fore.BLUE + str(winPoint2) + ' points')
    print(Style.RESET_ALL)
    
  contDesicion = input('Do you want to play again? (yes/no) ')
  if contDesicion == 'yes':
    contPlaying = True
  else:
    contPlaying = False
  print('Hope you Enjoyed!')
