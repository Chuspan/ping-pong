# ping-pong
2 ракетки
1 мячик
бить туда сюда

from pygame import *
from random import randint
from time import time as time

#класс-родитель для других спрайтов
class GameSprite(sprite.Sprite):
 #конструктор класса
   def __init__(self, player_image, player_x, player_y, size_x, size_y, player_speed):
       #Вызываем конструктор класса (Sprite):
       sprite.Sprite.__init__(self)


       #каждый спрайт должен хранить свойство image - изображение
       self.image = transform.scale(image.load(player_image), (size_x, size_y))
       self.speed = player_speed


       #каждый спрайт должен хранить свойство rect - прямоугольник, в который он вписан
       self.rect = self.image.get_rect()
       self.rect.x = player_x
       self.rect.y = player_y
 #метод, отрисовывающий героя на окне
   def reset(self):
       window.blit(self.image, (self.rect.x, self.rect.y))


#класс главного игрока
class Player(GameSprite):
   #метод для управления спрайтом стрелками клавиатуры
   def update(self):
       keys = key.get_pressed()
   def update_l(self):
       if keys[K_LEFT] and self.rect.x > 5:
           self.rect.x -= self.speed
       if keys[K_RIGHT] and self.rect.x < win_width - 80:
           self.rect.x += self.speed
   def update_r(self):
       if keys[K_UP] and self.rect.y > 5:
           self.rect.y -= self.speed
       if keys[K_DOWN] and self.rect.y < 80:
           self.rect.y -= self.speed
   def fire(self):
        bullet = Bullet(img_bullet, self.rect.centerx, self.rect.top, 15, 20, -105)
        bullets.add(bullet)


col = (255, 255, 255) 
win_width = 600
win_height = 500
display.set_caption("Ping pong")
window = display.set_mode((win_width, win_height))
window.fill(col)

game = True
finish = False
clock = time.Clock()
FPS = 60

While game:
    for e in event.get():
        if e.type == QUIT:
           run = False


 if finish != True:
       window.fill(col)




    display.update()
