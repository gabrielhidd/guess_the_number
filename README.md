# guess_the_number
This is my first code in Python 3. It is a game that you have to guess a number between 1 and 100.

import random

def jogar():

    print("*********************************")
    print("Bem vindo ao jogo de adivinhação!")
    print("*********************************")

    numero_secreto = random.randrange(1, 101)
    total_de_tentativas = 0
    pontos = 1000

    print("Qual é o nível de dificuldade deseja?")
    print("(1) Fácil, (2) Médio e (3) Difícil")
    nivel = input("Defina o nível de dificuldade: ")
    nivel_int = int(nivel)

    if (nivel_int == 1):
        total_de_tentativas = 20
        print("Você esolhou o nível Fácil, terá {} tentativas para acertar o número.".format(total_de_tentativas))
    if (nivel_int == 2):
        total_de_tentativas = 10
        print("Você esolhou o nível Médio, terá {} tentativas para acertar o número.".format(total_de_tentativas))
    elif (nivel_int == 3):
        total_de_tentativas = 5
        print("Você esolhou o nível Difícil, terá {} tentativas para acertar o número.".format(total_de_tentativas))

    for rodada in range(1, total_de_tentativas + 1):
        print("Tentativa {} de {}".format(rodada, total_de_tentativas))
        chute_str = input("Digite o seu número entre 1 e 100: ")
        chute_int = int(chute_str)
        print("Você digitou", chute_int)

        if (chute_int < 1 or chute_int > 100):
            print("Você deve digitar um número entre 1 e 100.")
            continue

        acertou = numero_secreto == chute_int
        maior   = numero_secreto < chute_int
        menor   = numero_secreto > chute_int

        if (acertou):
            print("Parabéns, você acertou")
            break

        else:
            if (maior):
                print("Você errou, o seu chute foi maior do que o número secreto.")
            elif (menor):
                print("Você errou, o seu chute foi menor do que o número secreto.")
            pontos_perdidos = abs(numero_secreto - chute_int)
            pontos = pontos - pontos_perdidos

        rodada = rodada + 1

    print("Você fez {} pontos.".format(pontos))
    print("Fim de jogo")
    print("O número secreto era {}".format(numero_secreto))

if (__name__ == "__main__"):
    jogar()
