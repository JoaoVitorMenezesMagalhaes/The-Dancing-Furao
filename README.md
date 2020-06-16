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

    #dimensões da tela 
    largura = 750
    altura = 600

    #tela
    surface = pygame.display.set_mode([largura, altura])

    arquivo = os.path.join('The-Dancing-Furao', 'background gam.png')

    #fonte dos textos
    fonte = pygame.font.SysFont(None, 50)
    fonte2 = pygame.font.SysFont(None, 30)
    #condições da tela inicial
    menu = True 
    def texto (text, fonte,     cor, surf, x, y):
        textobj = fonte.render (text, 1, cor)
        textorect = textobj.get_rect()
        textorect.topleft = (x,y)
        surf.blit (textobj, textorect)

    #tela final
    def tela_final():
        clicar = False
        tela_final1 = True
        while tela_final1:
            try: 
                fundo = pygame.image.load('background gam.png')  
            except pygame.error:
                print('erro ao tentar ler imagem: fundo')
                sys.exit()
            surface.blit(fundo,[0,0])
            texto('Fim de jogo', fonte, vermelho,surface, 290, 100)
            ax, ay = pygame.mouse.get_pos()

            botao4 = pygame.Rect(300, 200, 150, 50)
            botao5 = pygame.Rect(300, 300, 150, 50)

            if botao4.collidepoint((ax,ay)):
                if clicar:
                    return
            if botao5.collidepoint((ax,ay)):
                if clicar:
                    pygame.quit()
                    sys.exit()

            pygame.draw.rect(surface, (branco), botao4)
            pygame.draw.rect(surface, (branco), botao5)
            texto('Voltar ao menu', fonte2, preto, surface, 303, 217)
            texto('Sair do jogo', fonte2, preto, surface, 315, 317)

            clicar = False
            for event in pygame.event.get():
                if event.type == pygame.QUIT:
                    pygame.quit()
                    sys.exit()
                elif event.type == pygame.MOUSEBUTTONDOWN:
                    if event.button == 1 :
                        clicar = True
            pygame.display.update()

    #loop do ragatanga
    def ragatanga():

        #pontuação 
        texto = fonte.render("Pontuação: ", True, (preto), (branco))
        pos_texto = texto.get_rect()
        pos_texto.center = (85,50)
        pontos = 0

        #erros
        texto1 = fonte.render("Erros: ", True, (preto), (branco))
        pos_texto1 = texto1.get_rect()
        pos_texto1.center = (665,50)
        erro = 0

        #fundo
        try: 
            fundo = pygame.image.load('background gam.png') 
        except pygame.error:
            print('erro ao tentar ler imagem: fundo1')
            sys.exit()

        #imagem do furão inicial 
        try:
            imagem_1 = pygame.image.load('furao 3 resized t.png')
        except pygame.error:
            print('erro ao tentar ler imagem: furao')
            sys.exit()

        #música
        try:
            pygame.mixer.music.set_volume(0.2)
            pygame.mixer.music.load('Rouge - Ragatanga (Vídeo Clipe Oficial) HD.mp3')
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

        #velocidade das setas    
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

        t0 = pygame.time.get_ticks()
        TEMPO_MUSICA = 198000

        #loop
        while True: 
            t1 = pygame.time.get_ticks()
            if t1 - t0 > TEMPO_MUSICA:
                tela_final()
                False
                return
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
                         if abs(yd-yfixo)<100:#pontuação
                              pontos += 100
                              texto = fonte.render("Pontuação: "+str(pontos), True, (preto), (branco))
                         else:#pontuação e erros
                             erro += 1
                             texto1 = fonte.render("Erros: "+str(erro), True, (preto), (branco))
                             pontos -= 50
                             texto = fonte.render("Pontuação: "+str(pontos), True, (preto), (branco))
                     if evento.key == pygame.K_UP: #seta para cima
                         try:
                             imagem_1= pygame.image.load("furao 3 resized t.png")
                         except pygame.error:
                             print('erro ao tentar ler imagem: furao 3 resized t.png')
                             sys.exit()      
                         if abs(yc-yfixo)<100:#pontuação
                             pontos += 100
                             texto = fonte.render("Pontuação: "+str(pontos), True, (preto), (branco))
                         else:#pontuação e erros
                            erro += 1
                            pontos -= 50
                            texto1 = fonte.render("Erros: "+str(erro), True, (preto), (branco))
                            texto = fonte.render("Pontuação: "+str(pontos), True, (preto), (branco))
                     if evento.key == pygame.K_LEFT: #seta para a esquerda
                        try:
                            imagem_1= pygame.image.load("furao 1 resized t.png")
                        except pygame.error:
                            print('erro ao tentar ler imagem: furao 1 resized t.png')
                            sys.exit()
                        if abs(ye-yfixo)<100:#pontuação
                            pontos += 100
                            texto = fonte.render("Pontuação: "+str(pontos), True, (preto), (branco))
                        else:#pontuação e erros
                            erro += 1
                            pontos -= 50
                            texto1 = fonte.render("Erros: "+str(erro), True, (preto), (branco))
                            texto = fonte.render("Pontuação: "+str(pontos), True, (preto), (branco))
                     if evento.key == pygame.K_DOWN: #seta para baixo
                        try:
                            imagem_1= pygame.image.load("furao 4 resized t.png")
                        except pygame.error:
                            print('erro ao tentar ler imagem: furao 4 resized t.png')
                            sys.exit()
                        if abs(yd-yfixo)<100:#pontuação
                            pontos += 100
                            texto = fonte.render("Pontuação: "+str(pontos), True, (preto), (branco))
                        else:#pontuação e erros
                            erro += 1
                            pontos -= 50
                            texto1 = fonte.render("Erros: "+str(erro), True, (preto), (branco))
                            texto = fonte.render("Pontuação: "+str(pontos), True, (preto), (branco))

            #cria as setas embaixo da tela em posições aleatórias
            if (yb <= -180):
                yb = randint(700,1500)
            if (yc <=-180):
                yc = randint(700,1500)
            if (yd <=-180):
                yd = randint(700,1500)
            if (ye <= -180):
                ye = randint(700,1500)

            #realiza os movimentos das setas
            yb -= mov        
            yc -= mov
            yd -= mov   
            ye -= mov 

            #atualizações de tela
            surface.blit(fundo, [0,0])#insere a imagem de fundo
            surface.blit(seta_baixo, [xb, yb])#insere a seta que se move
            surface.blit(seta_cima, [xc, yc])#insere a seta que se move
            surface.blit(seta_direita, [xd, yd])#insere a seta que se move
            surface.blit(seta_esquerda, [xe, ye])#insere a seta que se move
            surface.blit(imagem_1, [250, 280])#insere o furão
            surface.blit(seta_baixo, [xb, yfixo])#insere a seta fixa
            surface.blit(seta_cima, [xc, yfixo])#insere a seta fixa
            surface.blit(seta_direita, [xd, yfixo])#insere a seta fixa
            surface.blit(seta_esquerda, [xe, yfixo])#insere a seta fixa
            surface.blit(texto, pos_texto)#insere a pontuação
            surface.blit(texto1, pos_texto1)#insere a quantidade de erros
            pygame.display.flip()#atualiza a tela

    #loop do madagascar
    def madagascar():

        #pontuação 
        texto = fonte.render("Pontuação: ", True, (preto), (branco))
        pos_texto = texto.get_rect()
        pos_texto.center = (85,50)
        pontos = 0

        #erros
        texto1 = fonte.render("Erros: ", True, (preto), (branco))
        pos_texto1 = texto1.get_rect()
        pos_texto1.center = (665,50)
        erro = 0

        #fundo
        try: 
           fundo = pygame.image.load('background gam.png')
        except pygame.error: 
            print('erro ao tentar ler imagem: fundo2')
            sys.exit()

        #imagem do furão inicial 
        try:
            imagem_1 = pygame.image.load('furao 3 resized t.png')
        except pygame.error:
            print('erro ao tentar ler imagem: furao')
            sys.exit()

        #música
        try:
            pygame.mixer.music.load('01 -  CD Edy Lemond - Promocional Julho 2015 - Madagascar.mp3')
            pygame.mixer.music.set_volume(0.2)
            pygame.mixer.music.play(1)
        except pygame.error:
            print('erro ao tentar ler musica1')
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

        #velocidade das setas     
        mov = 11

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

        t0 = pygame.time.get_ticks()
        TEMPO_MUSICA = 223000
        #loop
        while True: 
            t1 = pygame.time.get_ticks()
            if t1 - t0 > TEMPO_MUSICA:
                tela_final()
                return
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
                         if abs(yd-yfixo)<100:#pontuação
                              pontos += 100
                              texto = fonte.render("Pontuação: "+str(pontos), True, (preto), (branco))
                         else:#pontuação e erros
                             erro += 1
                             texto1 = fonte.render("Erros: "+str(erro), True, (preto), (branco))
                             pontos -= 50
                             texto = fonte.render("Pontuação: "+str(pontos), True, (preto), (branco))
                      if evento.key == pygame.K_UP: #seta para cima
                         try:
                             imagem_1= pygame.image.load("furao 3 resized t.png")
                         except pygame.error:
                             print('erro ao tentar ler imagem: furao 3 resized t.png')
                             sys.exit()      
                         if abs(yc-yfixo)<100:#pontuação
                             pontos += 100
                             texto = fonte.render("Pontuação: "+str(pontos), True, (preto), (branco))
                         else:#pontuação e erros
                            erro += 1
                            pontos -= 50
                            texto1 = fonte.render("Erros: "+str(erro), True, (preto), (branco))
                            texto = fonte.render("Pontuação: "+str(pontos), True, (preto), (branco))
                      if evento.key == pygame.K_LEFT: #seta para a esquerda
                        try:
                            imagem_1= pygame.image.load("furao 1 resized t.png")
                        except pygame.error:
                            print('erro ao tentar ler imagem: furao 1 resized t.png')
                            sys.exit()
                        if abs(ye-yfixo)<100:#pontuação
                            pontos += 100
                            texto = fonte.render("Pontuação: "+str(pontos), True, (preto), (branco))
                        else:#pontuação e erros
                            erro += 1
                            pontos -= 50
                            texto1 = fonte.render("Erros: "+str(erro), True, (preto), (branco))
                            texto = fonte.render("Pontuação: "+str(pontos), True, (preto), (branco))
                      if evento.key == pygame.K_DOWN: #seta para baixo
                        try:
                            imagem_1= pygame.image.load("furao 4 resized t.png")
                        except pygame.error:
                            print('erro ao tentar ler imagem: furao 4 resized t.png')
                            sys.exit()
                        if abs(yd-yfixo)<100:#pontuação
                            pontos += 100
                            texto = fonte.render("Pontuação: "+str(pontos), True, (preto), (branco))
                        else:#pontuação e erros
                            erro += 1
                            pontos -= 50
                            texto1 = fonte.render("Erros: "+str(erro), True, (preto), (branco))
                            texto = fonte.render("Pontuação: "+str(pontos), True, (preto), (branco))

           #cria as setas embaixo da tela em posições aleatórias
            if (yb <= -180):
                yb = randint(700,1500)
            if (yc <=-180):
                yc = randint(700,1500)
            if (yd <=-180):
                yd = randint(700,1500)
            if (ye <= -180):
                ye = randint(700,1500)

            #realiza os movimentos das setas
            yb -= mov        
            yc -= mov
            yd -= mov   
            ye -= mov

            #atualizações de tela
            surface.blit(fundo, [0,0])#insere a imagem de fundo
            surface.blit(seta_baixo, [xb, yb])#insere a seta que se move
            surface.blit(seta_cima, [xc, yc])#insere a seta que se move
            surface.blit(seta_direita, [xd, yd])#insere a seta que se move
            surface.blit(seta_esquerda, [xe, ye])#insere a seta que se move
            surface.blit(imagem_1, [250, 280])#insere o furão
            surface.blit(seta_baixo, [xb, yfixo])#insere a seta fixa
            surface.blit(seta_cima, [xc, yfixo])#insere a seta fixa
            surface.blit(seta_direita, [xd, yfixo])#insere a seta fixa
            surface.blit(seta_esquerda, [xe, yfixo])#insere a seta fixa
            surface.blit(texto, pos_texto)#insere a pontuação
            surface.blit(texto1, pos_texto1)#insere a quantidade de erros
            pygame.display.flip()#atualiza a tela


    #loop do me adota
    def me_adota():

        #pontuação 
        texto = fonte.render("Pontuação: ", True, (preto), (branco))
        pos_texto = texto.get_rect()
        pos_texto.center = (85,50)
        pontos = 0

        #erros
        texto1 = fonte.render("Erros: ", True, (preto), (branco))
        pos_texto1 = texto1.get_rect()
        pos_texto1.center = (665,50)
        erro = 0

        #fundo
        try: 
            fundo = pygame.image.load('background gam.png')  
        except pygame.error:
            print('erro ao tentar ler imagem: fundo3')
            sys.exit()

        #imagem do furão inicial 
        try:
            imagem_1 = pygame.image.load('furao 3 resized t.png')
        except pygame.error:
            print('erro ao tentar ler imagem: furao')
            sys.exit()

        #música
        try:
            pygame.mixer.music.load('mc-mirella-me-adota.mp3')
            pygame.mixer.music.set_volume(0.2)
            pygame.mixer.music.play(1)
        except pygame.error:
            print('erro ao tentar ler musica2')
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

        #velocidade das setas     
        mov = 8

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

        t0 = pygame.time.get_ticks()
        TEMPO_MUSICA = 164000
        #loop
        while True: 
            t1 = pygame.time.get_ticks()
            if t1 - t0 > TEMPO_MUSICA:
                tela_final()
                return tela_final
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
                         if abs(yd-yfixo)<100:#pontuação
                              pontos += 100
                              texto = fonte.render("Pontuação: "+str(pontos), True, (preto), (branco))
                         else:#pontuação e erros
                             erro += 1
                             texto1 = fonte.render("Erros: "+str(erro), True, (preto), (branco))
                             pontos -= 50
                             texto = fonte.render("Pontuação: "+str(pontos), True, (preto), (branco))
                    if evento.key == pygame.K_UP: #seta para cima
                         try:
                             imagem_1= pygame.image.load("furao 3 resized t.png")
                         except pygame.error:
                             print('erro ao tentar ler imagem: furao 3 resized t.png')
                             sys.exit()      
                         if abs(yc-yfixo)<100:#pontuação
                             pontos += 100
                             texto = fonte.render("Pontuação: "+str(pontos), True, (preto), (branco))
                         else:#pontuação e erros
                            erro += 1
                            pontos -= 50
                            texto1 = fonte.render("Erros: "+str(erro), True, (preto), (branco))
                            texto = fonte.render("Pontuação: "+str(pontos), True, (preto), (branco))
                    if evento.key == pygame.K_LEFT: #seta para a esquerda
                        try:
                            imagem_1= pygame.image.load("furao 1 resized t.png")
                        except pygame.error:
                            print('erro ao tentar ler imagem: furao 1 resized t.png')
                            sys.exit()
                        if abs(ye-yfixo)<100:#pontuação
                            pontos += 100
                            texto = fonte.render("Pontuação: "+str(pontos), True, (preto), (branco))
                        else:#pontuação e erros
                            erro += 1
                            pontos -= 50
                            texto1 = fonte.render("Erros: "+str(erro), True, (preto), (branco))
                            texto = fonte.render("Pontuação: "+str(pontos), True, (preto), (branco))
                    if evento.key == pygame.K_DOWN: #seta para baixo
                        try:
                            imagem_1= pygame.image.load("furao 4 resized t.png")
                        except pygame.error:
                            print('erro ao tentar ler imagem: furao 4 resized t.png')
                            sys.exit()
                        if abs(yd-yfixo)<100:#pontuação
                            pontos += 100
                            texto = fonte.render("Pontuação: "+str(pontos), True, (preto), (branco))
                        else:#pontuação e erros
                            erro += 1
                            pontos -= 50
                            texto1 = fonte.render("Erros: "+str(erro), True, (preto), (branco))
                            texto = fonte.render("Pontuação: "+str(pontos), True, (preto), (branco))

            #cria as setas embaixo da tela em posições aleatórias
            if (yb <= -180):
                yb = randint(700,1500)
            if (yc <=-180):
                yc = randint(700,1500)
            if (yd <=-180):
                yd = randint(700,1500)
            if (ye <= -180):
                ye = randint(700,1500)

            #realiza os movimentos das setas
            yb -= mov        
            yc -= mov
            yd -= mov   
            ye -= mov 

            #atualizações de tela
            surface.blit(fundo, [0,0])#insere a imagem de fundo
            surface.blit(seta_baixo, [xb, yb])#insere a seta que se move
            surface.blit(seta_cima, [xc, yc])#insere a seta que se move
            surface.blit(seta_direita, [xd, yd])#insere a seta que se move
            surface.blit(seta_esquerda, [xe, ye])#insere a seta que se move
            surface.blit(imagem_1, [250, 280])#insere o furão
            surface.blit(seta_baixo, [xb, yfixo])#insere a seta fixa
            surface.blit(seta_cima, [xc, yfixo])#insere a seta fixa
            surface.blit(seta_direita, [xd, yfixo])#insere a seta fixa
            surface.blit(seta_esquerda, [xe, yfixo])#insere a seta fixa
            surface.blit(texto, pos_texto)#insere a pontuação
            surface.blit(texto1, pos_texto1)#insere a quantidade de erros
            pygame.display.flip()#atualiza a tela

    #menu da tela inicial 
    clicar = False 
    while menu:
        try: 
            fundo = pygame.image.load('background gam.png') 
        except pygame.error:
            print('erro ao tentar ler imagem: fundo')
            sys.exit()
        surface.blit(fundo,[0,0])
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
                madagascar()
        if botao3.collidepoint((px,py)):
            if clicar:
                me_adota()

        pygame.draw.rect(surface, (branco), botao1)
        pygame.draw.rect(surface, (branco), botao2)
        pygame.draw.rect(surface, (branco), botao3)
        texto('Ragatanga', fonte2, preto, surface, 321, 217)
        texto('Madagascar', fonte2, preto, surface, 315, 317)
        texto('Me adota', fonte2, preto, surface, 330, 417)

        clicar = False
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                pygame.quit()
                sys.exit()
            elif event.type == pygame.MOUSEBUTTONDOWN:
                if event.button == 1 :
                    clicar = True

        pygame.display.update()

 
