# The-Dancing-Furao
#Um furão dançando no ritmo do ragatanga
#Luca Oshiro, João Vitor Magalhães, Mariana Cezar

    import pygame
    import os
    import sys

    pygame.init()

    surface = pygame.display.set_mode([400, 600])

    arquivo = os.path.join('imagem', 'background.jpg')

    try:
        imagem = pygame.image.load('background.jpg')
    except pygame.error:
        print('erro ao tentar ler imagem: background')
        sys.exit()
