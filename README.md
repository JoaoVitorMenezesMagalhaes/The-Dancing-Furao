# The-Dancing-Furao
#Um furão dançando no ritmo do ragatanga
#Luca Oshiro, João Vitor Magalhães, Mariana Cezar

    import pygame
    import os
    import sys

    pygame.init()

    surface = pygame.display.set_mode([750, 600])

    arquivo = os.path.join('imagem', 'background gam.png')

    try:
        fundo = pygame.image.load('background gam.png')
    except pygame.error:
        print('erro ao tentar ler imagem: background gam.png')
        sys.exit()

    try:
        imagem_1 = pygame.image.load('furao 3 resized t.png')
    except pygame.error:
        print('erro ao tentar ler imagem: background gam.png')
        sys.exit()

    try:
        seta_baixo = pygame.image.load('seta1.png')
    except pygame.error:
        print('erro ao tentar ler imagem: seta1.png')
        sys.exit()

    try:
        seta_cima = pygame.image.load('seta2.png')
    except pygame.error:
        print('erro ao tentar ler imagem: seta2.png')
        sys.exit()

    try:
        seta_direita = pygame.image.load('seta3.png')
    except pygame.error:
        print('erro ao tentar ler imagem: seta3.png')
        sys.exit()

    try:
        seta_esquerda = pygame.image.load('seta4.png')
    except pygame.error:
        print('erro ao tentar ler imagem: seta4.png')
        sys.exit()

    while True:
        eventos=pygame.event.get()
        for evento in eventos:
            if evento.type == pygame.QUIT:
                pygame.quit()
                sys.exit()
            if evento.type == pygame.KEYDOWN:
                if evento.key == pygame.K_RIGHT:
                    try:
                        imagem_1= pygame.image.load("furao 2 resized t.png")
                    except pygame.error:
                        print('erro ao tentar ler imagem: furao 2 resized t.png')
                        sys.exit()
                if evento.key == pygame.K_UP:
                    try:
                        imagem_1= pygame.image.load("furao 3 resized t.png")
                    except pygame.error:
                        print('erro ao tentar ler imagem: furao 3 resized t.png')
                        sys.exit()      
                if evento.key == pygame.K_LEFT:
                    try:
                        imagem_1= pygame.image.load("furao 1 resized t.png")
                    except pygame.error:
                        print('erro ao tentar ler imagem: furao 1 resized t.png')
                        sys.exit()
                if evento.key == pygame.K_DOWN:
                    try:
                        imagem_1= pygame.image.load("furao 4 resized t.png")
                    except pygame.error:
                        print('erro ao tentar ler imagem: furao 4 resized t.png')
                        sys.exit()
        surface.blit(fundo, [0,0])
        surface.blit(imagem_1, [250, 280])
        surface.blit(seta_baixo, [150,200])
        surface.blit(seta_cima, [250,200])
        surface.blit(seta_direita, [350,200])
        surface.blit(seta_esquerda, [450,200])
        pygame.display.flip()
