# The-Dancing-Furao
#Um furão dançando no ritmo do ragatanga
#Luca Oshiro, João Vitor Magalhães, Mariana Cezar

import pygame
import os
import sys

pygame.init()

surface = pygame.display.set_mode([600, 800])

arquivo = os.path.joint('imagem', 'background.jpg')

try:
    
    imagem = pygame.image.load('background.jpg')

except pygame.error:
    
    print('erro ao tentar ler imagem: logo.jpg')
    
    sys.exit()
