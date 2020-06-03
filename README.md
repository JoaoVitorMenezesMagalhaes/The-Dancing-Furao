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
        surface.blit(imagem, [0,0])
        pygame.display.flip()
