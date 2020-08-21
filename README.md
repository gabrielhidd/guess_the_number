# guess_the_number
This is my first code in Python 3. It is a game that you have to guess a number between 1 and 100.

import random
#aqui importamos a biblioteca do random
#a função random usa um número entre 0.0 e 1.0 random.random()
#mas nós queremos um número entre 1 e 100
#mas 100 é exclusivo nessa função, o valor máximo é 99
#A função random.randrange(i,  N+1) nos gera um número inteiro entre i e N, faz mais sentido para nós
#Na dúvida, visite as bibliotecas do Python

def jogar():

    print("*********************************")
    print("Bem vindo ao jogo de adivinhação!")
    print("*********************************")

    #aqui estão as nossas variáveis
    numero_secreto = random.randrange(1, 101)
    #Essa função nos gerará um número aleatório de 1 a 100
    total_de_tentativas = 0
    pontos = 1000

    #Vamos agora definir o nível de dificuldade do nosso jogo
    print("Qual é o nível de dificuldade deseja?")
    print("(1) Fácil, (2) Médio e (3) Difícil")
    nivel = input("Defina o nível de dificuldade: ")
    nivel_int = int(nivel)

    #aqui definimos as rodadas da dificuldade, só com comando que já vimos
    #mas fiz uns paranauês a mais do q o professor
    if (nivel_int == 1):
        total_de_tentativas = 20
        print("Você esolhou o nível Fácil, terá {} tentativas para acertar o número.".format(total_de_tentativas))
    if (nivel_int == 2):
        total_de_tentativas = 10
        print("Você esolhou o nível Médio, terá {} tentativas para acertar o número.".format(total_de_tentativas))
    elif (nivel_int == 3):
        total_de_tentativas = 5
        print("Você esolhou o nível Difícil, terá {} tentativas para acertar o número.".format(total_de_tentativas))

    #Vamos ao jogo em si
    for rodada in range(1, total_de_tentativas + 1):
        #atenção no loop com o for, o valor final é exclusivo (igual no random)
        #Por isso adicionamos 1 unidade
        print("Tentativa {} de {}".format(rodada, total_de_tentativas))
        #Essa função format é muito boa e quebra muito galho
        #usa-se as {} e os argumentos q vc deseja colocar
        chute_str = input("Digite o seu número entre 1 e 100: ")
        chute_int = int(chute_str)
        print("Você digitou", chute_int)

        if (chute_int < 1 or chute_int > 100):
            print("Você deve digitar um número entre 1 e 100.")
            continue
            #o segmento 'continue' nos diz para prosseguirmos no loop, independentemente do dele estando certo

        acertou = numero_secreto == chute_int
        maior   = numero_secreto < chute_int
        menor   = numero_secreto > chute_int

        if (acertou):
            print("Parabéns, você acertou")
            break
            #o segmento 'break' interrompe o loop e segue para a parte seguinte

        else:
            if (maior):
                print("Você errou, o seu chute foi maior do que o número secreto.")
            elif (menor):
                print("Você errou, o seu chute foi menor do que o número secreto.")
            pontos_perdidos = abs(numero_secreto - chute_int)
            #aqui usamos a função 'abs' (absoluto para colocar em módulo os nossos número negativos)
            pontos = pontos - pontos_perdidos

        rodada = rodada + 1

    print("Você fez {} pontos.".format(pontos))
    print("Fim de jogo")
    print("O número secreto era {}".format(numero_secreto))

if (__name__ == "__main__"):
    jogar()
#esse comando q colocamos é muito interessante
#ele faz com q a função só seja executada se for chamada nominalmente
#fique de olho nisso pois será de grande ajuda
