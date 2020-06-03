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
        imagem = pygame.image.load('background gam.png')
    except pygame.error:
        print('erro ao tentar ler imagem: background gam.png')
        sys.exit()

    while True:
        eventos=pygame.event.get()
        for evento in eventos:
            if evento.type == pygame.QUIT:
                pygame.quit()
                sys.exit()
                    if evento.type == pygame.KEYDOWN:
            if evento.key == pygame.K_LEFT:
                try:
                    imagem_1= pygame.image.load("furao 1 gambiarra.jpeg")
            surface.blit(imagem_1, [400,320])
            if evento.type == pygame.KEYDOWN:
                if evento.key == pygame.K_RIGHT:
                    try:
                        imagem_2= pygame.image.load("furao 2.jpeg")
            surface.blit(imagem_1, [400,320])
            if evento.type == pygame.KEYDOWN:
                if evento.key == pygame.K_DOWN:
                    try:
                        imagem_3= pygame.image.load("furao 3.jpeg")
            surface.blit(imagem_1, [400,320])
    surface.blit(imagem, [0,0])
        surface.blit(imagem, [0,0])
        pygame.display.flip()
