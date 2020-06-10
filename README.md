# The-Dancing-Furao
#Um furão dançando no ritmo do ragatanga
#Luca Oshiro, João Vitor Magalhães, Mariana Cezar

    import pygame
    import os
    import sys
    from random import randint

    pygame.init()

    surface = pygame.display.set_mode([750, 600])

    arquivo = os.path.join('imagem', 'background gam.png')

    mov = 10

    xb = 150
    xc = 250
    xd = 350
    xe = 450

    yb = randint(700,1500)
    yc = randint(700,1500)
    yd = randint(700,1500)
    ye = randint(700,1500)

    #imagem de fundo
    try:
        fundo = pygame.image.load('background gam.png')
    except pygame.error:
        print('erro ao tentar ler imagem: background gam.png')
        sys.exit()

    #imagens das setas e do furão inicial 
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

    #setas que se movem
    try:
        seta_baixo_m = pygame.image.load('seta1.png')
    except pygame.error:
        print('erro ao tentar ler imagem: seta1.png')
        sys.exit()

    try:
        seta_cima_m = pygame.image.load('seta2.png')
    except pygame.error:
        print('erro ao tentar ler imagem: seta2.png')
        sys.exit()

    try:
        seta_direita_m = pygame.image.load('seta3.png')
    except pygame.error:
        print('erro ao tentar ler imagem: seta3.png')
        sys.exit()

    try:
        seta_esquerda_m = pygame.image.load('seta4.png')
    except pygame.error:
        print('erro ao tentar ler imagem: seta4.png')
        sys.exit()


    #loop
    while True:
        eventos=pygame.event.get()
        for evento in eventos:
            if evento.type == pygame.QUIT:
                pygame.quit()
                sys.exit()
            if evento.type == pygame.KEYDOWN:
                if evento.key == pygame.K_RIGHT: #seta para direita
                    try:
                        imagem_1= pygame.image.load("furao 2 resized t.png")
                    except pygame.error:
                        print('erro ao tentar ler imagem: furao 2 resized t.png')
                        sys.exit()
                if evento.key == pygame.K_UP: #seta para cima
                    try:
                        imagem_1= pygame.image.load("furao 3 resized t.png")
                    except pygame.error:
                        print('erro ao tentar ler imagem: furao 3 resized t.png')
                        sys.exit()      
                if evento.key == pygame.K_LEFT: #seta para a esquerda
                    try:
                        imagem_1= pygame.image.load("furao 1 resized t.png")
                    except pygame.error:
                        print('erro ao tentar ler imagem: furao 1 resized t.png')
                        sys.exit()
                if evento.key == pygame.K_DOWN: #seta para baixo
                    try:
                        imagem_1= pygame.image.load("furao 4 resized t.png")
                    except pygame.error:
                        print('erro ao tentar ler imagem: furao 4 resized t.png')
                        sys.exit()
                    
    if (yb <= -180):
        yb = randint(700,1500)
    if (yc <=-180):
        yc = randint(700,1500)
    if (yd <=-180):
        yd = randint(700,1500)
    if (ye <= -180):
        ye = randint(700,1500)
        
    yb -= mov        
    yc -= mov
    yd -= mov
    ye -= mov
    
    surface.blit(fundo, [0,0])#insere a imagem de fundo
    surface.blit(seta_baixo_m, [xb, yb])
    surface.blit(seta_cima_m, [xc, yc])
    surface.blit(seta_direita_m, [xd, yd])
    surface.blit(seta_esquerda_m, [xe, ye])
    surface.blit(imagem_1, [250, 280])
    surface.blit(seta_baixo, [150,200])
    surface.blit(seta_cima, [250,200])
    surface.blit(seta_direita, [350,200])
    surface.blit(seta_esquerda, [450,200])
    pygame.display.flip()#atualiza a tela
