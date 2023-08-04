import random

CHOICE = ['Rock', 'Paper', 'Scissors'] 

def players(num_players): 
  names = list(input('Enter names of players: ').split()) 
  while num_players != len(names): 
    print(f'Must enter {num_players} names, try again ', end='') 
    names = list(input().split()) 
    print() 
    for i in range(len(names)): 
      print(names[i], end=' ')# format the name spacing print('\n============================================================') 
      return names

def number_of_players(): 
  num_players = input('Enter numbers of players: ') 
  while num_players.isnumeric() == False or int(num_players) < 3: 
    if num_players.isnumeric() == False: 
      num_players = input('Must be a number, try again: ') 
    elif int(num_players) < 3: 
      num_players = input('Must be at least 3, try again: ') 
      num_players = int(num_players) 
      return num_players

def draw_round_one(scores): 
  for i in range(len(scores)): 
    if (scores[i] != 'X'): 
      scores[i] = CHOICE[random.randint(0, 1)] 
      #fix print statments # rock being printed here 
  for i in range(len(scores)): 
    print(scores[i], end = ' ') 
    if i >= len(scores)- 1: print() #print(scores) 
    return scores

def calculate_round_one(scores): 
  if scores.count('Rock') > scores.count('Paper'): 
    for i in range(len(scores)): 
      if scores[i] == 'Paper': scores[i] = 'X' 
  else: 
    for i in range(len(scores)): 
      if scores[i] == 'Rock': scores[i] = 'X' 
  return scores

def round_one(number_of_players1, names, scores): 
  while scores.count('X') != (number_of_players1 - 2): 
    scores = draw_round_one(scores) 
    if scores.count('Rock') != scores.count('Paper'): 
      scores = calculate_round_one(scores) 
      return scores

def draw_round_two(scores): 
  for i in range(len(scores)): 
    if (scores[i] != 'X'): scores[i] = CHOICE[random.randint(0, 2)] #fix print statments 
    for i in range(len(scores)): 
      print(scores[i], end = ' ')#rock being printed here 
      if i >= len(scores)- 1: print() #rint(scores) martha abigail dolley rachel hannah test names return scores

def calculate_round_two(scores): 
  if scores.count('Rock') == 1 and scores.count('Paper') == 1: 
    for i in range(len(scores)): 
      if (scores[i] == 'Rock'): 
        scores[i] = 'X' 
      elif scores.count('Rock') == 1 and scores.count('Scissors') == 1: 
        for i in range(len(scores)): 
          if (scores[i] == 'Scissors'): 
            scores[i] = 'X' 
          if scores.count('Paper') == 1 and scores.count('Scissors') == 1: 
            for i in range(len(scores)): 
              if (scores[i] == 'Paper'): 
                scores[i] = 'X' 
        return scores

def round_two(number_of_players1, names, scores): 
  scores = draw_round_two(scores) 
  while scores.count('Rock') == 2 or scores.count('Paper') == 2 or scores.count('Scissors') == 2: 
    scores = draw_round_two(scores)

  scores = calculate_round_two(scores)

  return scores
def main(): # Get seed from user. 
  seed = int(input('Enter a seed: '))

# Set seed for random number generator.
  random.seed(seed)
  number_of_players1 = number_of_players()
  names = players(number_of_players1)
  scores = [''] * number_of_players1
  scores = round_one(number_of_players1, names, scores)
  scores = round_two(number_of_players1, names, scores)

#print('============================================================')
  for i in range(len(scores)):
    if (scores[i] != 'X'):
      print("winner is: ", names[i])


#players_choice = [''] * num_players





  
