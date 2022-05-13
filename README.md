# HANGMAN
# JetBrains Academy project

import random

print('H A N G M A N')
option = ''
res = []
while option != 'exit':
    option = input('Type "play" to play the game, "results" to show the scoreboard, and "exit" to quit: ')

    if option == 'play':
        print(' ')

        words = ['python', 'java', 'swift', 'javascript']

        sug = random.choice(words)
        print('-' * len(sug))

        att = 0
        letters = []
        wrong = []
        alp = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm',
               'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z']

        while len(letters) < len(sug) and att < 8:
            answer = input('Input a letter: ')

            if len(answer) > 1 or len(answer) == 0:
                print('Please, input a single letter.\n')
                for i in sug:

                    if i == answer:
                        if i not in letters:
                            letters.append(i)
                        print(i, end='')
                    elif i in letters:
                        print(i, end='')
                    else:
                        print('-', end='')
                print('')

            else:

                if answer in alp:

                    if answer in letters or answer in wrong:
                        print("You've already guessed this letter.\n")
                        for i in sug:

                            if i == answer:
                                if i not in letters:
                                    letters.append(i)
                                print(i, end='')
                            elif i in letters:
                                print(i, end='')
                            else:
                                print('-', end='')
                        print('')

                    else:
                        if answer in sug:

                            if len(letters) - len(set(sug)) == -1:
                                print(f'You guessed the word {sug}! \nYou survived!')
                                res.append('w')
                                letters.clear()
                                wrong.clear()
                                break

                            else:

                                print('')
                                for i in sug:

                                    if i == answer:
                                        if i not in letters:
                                            letters.append(i)
                                        print(i, end='')
                                    elif i in letters:
                                        print(i, end='')
                                    else:
                                        print('-', end='')
                                print('')

                        else:
                            print("That letter doesn't appear in the word.\n")
                            wrong.append(answer)

                            if att == 7:
                                print('You lost!')
                                res.append('l')
                                letters.clear()
                                wrong.clear()
                                break

                            else:
                                for i in sug:
                                    if i in letters:
                                        print(i, end='')
                                    else:
                                        print('-', end='')
                                att += 1
                            print('')

                else:
                    print('Please, enter a lowercase letter from the English alphabet.\n')
                    for i in sug:

                        if i == answer:
                            if i not in letters:
                                letters.append(i)
                            print(i, end='')
                        elif i in letters:
                            print(i, end='')
                        else:
                            print('-', end='')
                    print('')

    elif option == 'results':
        print(f"You won: {res.count('w')} times.\nYou lost: {res.count('l')} times.")
