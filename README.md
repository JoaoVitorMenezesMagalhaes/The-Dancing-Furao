# The-Dancing-Furao
#Um furão dançando no ritmo do ragatanga
#Luca Oshiro, João Vitor Magalhães, Mariana Cezar

    import pygame
    import os
    import sys
    from random import randint

    pygame.init()

    surface = pygame.display.set_mode([750, 600])

    arquivo = os.path.join('The-Dancing-Furao', 'background gam.png')

    branco = (255,255,255)
    vermelho = (255, 0, 0)
    preto = (0,0,0)
    verde = (0,255,0)
    largura = 750
    altura = 600 

    #fundo2 = pygame.display.set_mode(largura, altura)
    #fonte = pygame.font.SysFont(None, 20)

    #def texto (msg, cor):
    #    texto1 = fonte.render(msg, True, cor)
    #    fundo2.blit(texto1, [largura/2, altura/2])

    #fimdejogo = False

    #while fimdejogo:
    #    fundo2.fill(branco)
    #    texto('Fim de jogo. Para jogar mais tecle A, para sair tecle S', vermelho)
    #    pygame.display.update()

    mov = 6

    xb = 150
    xc = 250
    xd = 350
    xe = 450

    yb = randint(700,1500)
    yc = randint(700,1500)
    yd = randint(700,1500)
    ye = randint(700,1500)

    fonte = pygame.font.SysFont(None, 40)

    menu = True 
    def texto (text, fonte, cor, surf, x, y):
        textobj = fonte.render (text, 1, cor)
        textorect = textobj.get_rect()
        textorect.topleft = (x,y)
        surf.blit (textobj, textorect)

    clicar = False
    while menu:
        surface.fill(branco)
        texto('The Dancing Furão', fonte, vermelho, surface, 240, 100)
        px, py = pygame.mouse.get_pos()

        botao1 = pygame.Rect(280, 200, 150, 50)
        botao2 = pygame.Rect(280, 300, 150, 50)
        botao3 = pygame.Rect(280, 400, 150, 50)
        if botao1.collidepoint((px,py)):
            if clicar:
                pass
        if botao2.collidepoint((px,py)):
            if clicar:
                pass
        if botao3.collidepoint((px,py)):
            if clicar:
                pass
        pygame.draw.rect(surface, (preto), botao1)
        pygame.draw.rect(surface, (vermelho), botao2)
        pygame.draw.rect(surface, (verde), botao3)

        clicar = False
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                pygame.quit()
                sys.exit()
            elif event.type == pygame.MOUSEBUTTONDOWN:
                if event.button == 1 :
                    menu = False

        pygame.display.update()        

    #imagem de fundo
    try:
        fundo = pygame.image.load(arquivo)    
        musica = os.path.join('The-Dancing-Furao', 'Rouge - Ragatanga (Vídeo Clipe Oficial) HD.mp3')
        pygame.mixer.music.load(musica)
        pygame.mixer.music.set_volume(0.2)
        pygame.mixer.music.play(1)
    except pygame.error:
        print('erro ao tentar ler imagem: background gam.png')
        sys.exit()

    #imagens das setas e do furão inicial 
    try:
        imagem_1 = pygame.image.load('furao 3 resized t.png')
    except pygame.error:
        print('erro ao tentar ler imagem: furao')
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
