# Turtle-crossing

import time
from turtle import Screen
from player import Player
from car_manager import CarManager
from scoreboard import Scoreboard

screen = Screen()
screen.setup(width=600, height=600)
screen.tracer(0)

player = Player()
car = CarManager()
scoreboard = Scoreboard()

screen.listen()
screen.onkey(player.move, "Up")

game_is_on = True
while game_is_on:
    time.sleep(0.1)
    screen.update()
    car.create_car()
    car.move()

    # 블럭과 부딪히면 game_over
    for cars in car.all_car:
        if cars.distance(player) < 20:
            scoreboard.game_over()
            game_is_on = False

    # 건너편으로 가면 점수 획득
    if player.is_at_finish_line():
        scoreboard.increase_level()
        car.level_up()


screen.exitonclick()
