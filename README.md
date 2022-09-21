STARTING_POSITION = (0, -280)
MOVE_DISTANCE = 10
FINISH_LINE_Y = 280

from turtle import Turtle


class Player(Turtle):
    def __init__(self):
        super().__init__()
        self.shape("turtle")
        self.penup()
        self.go_starting_pos()
        self.setheading(90)

    def move(self):
        self.forward(MOVE_DISTANCE)

    def go_starting_pos(self):
        self.goto(STARTING_POSITION)

    def is_at_finish_line(self):
        if self.ycor() > FINISH_LINE_Y:
            self.go_starting_pos()
            return True
        else:
            return False
