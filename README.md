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
        surface.blit(imagem, [0,0])
        pygame.display.flip()
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
                    surface.blit(imagem_1, [250,280])
                    pygame.display.update()
                if evento.key == pygame.K_UP:
                    try:
                        imagem_1= pygame.image.load("furao 3 resized t.png")
                    except pygame.error:
                        print('erro ao tentar ler imagem: furao 3 resized t.png')
                        sys.exit()      
                    surface.blit(imagem_1, [250,280])
                    pygame.display.update()
                if evento.key == pygame.K_LEFT:
                    try:
                        imagem_1= pygame.image.load("furao 1 resized t.png")
                    except pygame.error:
                        print('erro ao tentar ler imagem: furao 1 resized t.png')
                        sys.exit()
                    surface.blit(imagem_1, [250,280])
                    pygame.display.update()
                if evento.key == pygame.K_DOWN:
                    try:
                        imagem_1= pygame.image.load("furao 4 resized t.png")
                    except pygame.error:
                        print('erro ao tentar ler imagem: furao 4 resized t.png')
                        sys.exit()
                    surface.blit(imagem_1, [250,280])
                    pygame.display.update()
