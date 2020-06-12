# The-Dancing-Furao
#Um furão dançando no ritmo do ragatanga
#Luca Oshiro, João Vitor Magalhães, Mariana Cezar

    import pygame
    import os
    import sys
    from random import randint



    pygame.init()



    #cores
    branco = (255,255,255)
    vermelho = (255, 0, 0)
    preto = (0,0,0)
    verde = (0,255,0)
    azul = (0,0,255)

    #dimensões da tela 
    largura = 750
    altura = 600



    surface = pygame.display.set_mode([largura, altura])



    arquivo = os.path.join('The-Dancing-Furao', 'background gam.png')



    fonte = pygame.font.SysFont(None, 40)
    fonte2 = pygame.font.SysFont(None, 30)



    menu = True 
    def texto (text, fonte, cor, surf, x, y):
        textobj = fonte.render (text, 1, cor)
        textorect = textobj.get_rect()
        textorect.topleft = (x,y)
        surf.blit (textobj, textorect)

    def ragatanga():

        #fundo
        try: 
            fundo = pygame.image.load(arquivo) 
        except pygame.error:
            print('erro ao tentar ler imagem: fundo')
            sys.exit()

        #imagem do furão inicial 
        try:
            imagem_1 = pygame.image.load('furao 3 resized t.png')
        except pygame.error:
            print('erro ao tentar ler imagem: furao')
            sys.exit()
        #musica    
        try:
            musica = os.path.join('The-Dancing-Furao', 'Rouge - Ragatanga (Vídeo Clipe Oficial) HD.mp3')
            pygame.mixer.music.load(musica)
            pygame.mixer.music.set_volume(0.2)
            pygame.mixer.music.play(1)
        except pygame.error:
            print('erro ao tentar ler musica')
            sys.exit()




        #imagens das setas
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
        mov = 15
        #posições da setas nos eixos x, y
        yfixo = 200

        xb = 150
        xc = 250
        xd = 350
        xe = 450

        yb = randint(700,1500)
        yc = randint(700,1500)
        yd = randint(700,1500)
        ye = randint(700,1500)



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
            surface.blit(seta_baixo, [xb, yb])
            surface.blit(seta_cima, [xc, yc])
            surface.blit(seta_direita, [xd, yd])
            surface.blit(seta_esquerda, [xe, ye])
            surface.blit(imagem_1, [250, 280])
            surface.blit(seta_baixo, [xb, yfixo])
            surface.blit(seta_cima, [xc, yfixo])
            surface.blit(seta_direita, [xd, yfixo])
            surface.blit(seta_esquerda, [xe, yfixo])
            pygame.display.flip()#atualiza a tela
    '''     
    def me_adota():

    def madagascar():
    '''  

    clicar = False
    while menu:
        surface.fill(branco)
        texto('The Dancing Furão', fonte, vermelho, surface, 245, 100)
        px, py = pygame.mouse.get_pos()




        botao1 = pygame.Rect(300, 200, 150, 50)
        botao2 = pygame.Rect(300, 300, 150, 50)
        botao3 = pygame.Rect(300, 400, 150, 50)
        if botao1.collidepoint((px,py)):
            if clicar:
                ragatanga()
        if botao2.collidepoint((px,py)):
            if clicar:
                #me_adota()
                pass
        if botao3.collidepoint((px,py)):
            if clicar:
                #madagascar()
                pass

        pygame.draw.rect(surface, (azul), botao1)
        pygame.draw.rect(surface, (azul), botao2)
        pygame.draw.rect(surface, (azul), botao3)
        texto('Ragatanga', fonte2, branco, surface, 321, 217)
        texto('Me adota', fonte2, branco, surface, 330, 317)
        texto('Madagascar', fonte2, branco, surface, 315, 417)

        clicar = False
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                pygame.quit()
                sys.exit()
            elif event.type == pygame.MOUSEBUTTONDOWN:
                if event.button == 1 :
                    clicar = True

        pygame.display.update()       

