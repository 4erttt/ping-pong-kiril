# ping-pong-kiril
from pygame import *
from random import randint
from time import time as timer

class GameSprite(sprite.Sprite):
   def __init__(self, player_image, player_x, player_y, size_x, size_y, player_speed):
       sprite.Sprite.__init__(self)
       self.image = transform.scale(image.load(player_image), (size_x, size_y))
       self.speed = player_speed
       self.rect = self.image.get_rect()
       self.rect.x = player_x
       self.rect.y = player_y
   def reset(self):
       window.blit(self.image, (self.rect.x, self.rect.y))
       
class Player(GameSprite):
   def update_l(self):
       keys = key.get_pressed()
       if keys[K_w] and self.rect.y > 5:
           self.rect.y -= self.speed
       if keys[K_s] and self.rect.y < win_height - 80:
           self.rect.y += self.speed
   def update_r(self):
       if keys[K_UP] and self.rect.y > 5:
           self.rect.y -= self.speed
       if keys[K_DOWN] and self.rect.y < win_height - 80:
           self.rect.y += self.speed
   
class Enemy(GameSprite):
   def update(self):

buck=(200,255,255)
win_width = 700
win_height = 500
display.set_caption("Ping-pong")
window = display.set_mode((win_width, win_height))
window.fill(buck)

game=True
finish=False
clock=time.Clock()
FPS=60

1 = Player('racket.png', 5, win_height - 100, 80, 100, 10)
2=Player('racket.png', 520)

font.init()
font=font.Font(None,35)
lose1=font.render('PLAYER 1 LOSE!', True, (180, 0, 0))
lose2=font.render('PLAYER 2 LOSE!', True, (180, 0, 0))

speed_x=3
speed_y=3

while finish != True:
    for e in event.get():
        ife.type == QUIT:
        game =False

    if finish !=True:
        window.fill(back)
        1.update_l()
        2.update_r()
        ball.rect.x += speed_x
        ball.rect.y += speed_y
