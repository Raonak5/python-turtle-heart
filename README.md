# python-turtle-heart
import pygame

# Initialize pygame
pygame.init()

# Set up the window
width = 800
height = 600
screen = pygame.display.set_mode((width, height))
pygame.display.set_caption("Car Game")

# Load the car image
car_image = pygame.image.load("car.png")
car_rect = car_image.get_rect()

# Set the initial car position
car_rect.x = width // 2
car_rect.y = height // 2

# Set the car speed
car_speed = 5

# Game loop
running = True
while running:
    # Handle events
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

    # Move the car based on user input
    keys = pygame.key.get_pressed()
    if keys[pygame.K_LEFT]:
        car_rect.x -= car_speed
    if keys[pygame.K_RIGHT]:
        car_rect.x += car_speed
    if keys[pygame.K_UP]:
        car_rect.y -= car_speed
    if keys[pygame.K_DOWN]:
        car_rect.y += car_speed

    # Keep the car inside the window
    if car_rect.left < 0:
        car_rect.left = 0
    if car_rect.right > width:
        car_rect.right = width
    if car_rect.top < 0:
        car_rect.top = 0
    if car_rect.bottom > height:
        car_rect.bottom = height

    # Draw the car
    screen.fill((0, 0, 0))
    screen.blit(car_image, car_rect)
    pygame.display.flip()

# Clean up
pygame.quit()
