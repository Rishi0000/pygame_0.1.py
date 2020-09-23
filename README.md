# pygame_0.1.py
Catching Ball

        import pygame, sys
        import random
        pygame.init()
        screen = pygame.display.set_mode((500,500))
        pygame.display.set_caption("Catching")
        clock = pygame.time.Clock()

        ball_x = random.randint(20,480)
        ball_y = 20
        speed = 30

        bat_x = 0
        bat_y = 470
        bat_width = 50
        bat_hight = 50

        #for text
        font = pygame.font.Font('freesansbold.ttf',32)
        text = font.render('GAME OVER', True,(255,255,0), (0,255,0))
        textRect = text.get_rect()
        textRect.center = (250,250)

        run = True
        while run:
                clock.tick(8)

                pygame.display.update()
                for event in pygame.event.get():
                        if event.type == pygame.QUIT:
                                sys.exit()

                if ball_y>=20 and ball_y<=500:
                        ball_y+=speed

                if ball_y >= 500:
                        screen.blit(text, textRect)
                        pygame.display.update()

                keys = pygame.key.get_pressed()
                if keys[pygame.K_LEFT] and bat_x>0:
                        bat_x -= 50
                if keys[pygame.K_RIGHT] and bat_x+bat_width<500:
                        bat_x += 50

                if (ball_x>=bat_x and ball_x<=bat_x+bat_width) and (ball_y>=bat_y):
                        ball_x = random.randint(20,480)
                        ball_y = 20


                screen.fill((0,100,100))
                pygame.draw.rect(screen,(123,180,0),(bat_x,bat_y,bat_width,bat_hight))
                pygame.draw.circle(screen,(123,99,99),(ball_x,ball_y),20)
