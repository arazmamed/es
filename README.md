# es


import random


class dog:

    def __init__(self, name):
        self.name = name
        self.gladness = 50
        self.commands = 0
        self.food = 100
        self.alive = True
        self.sleep = 120
    def command(self):
        print("Time to comand")
        self.commands += 0.12
        self.gladness -= 5
        self.food+=100
    def to_sleep(self):
        print("I will sleep")
        self.gladness += 1
        self.sleep +=1

    def eat(self):
        self.food-=10
        return self.food

    def to_chill(self):
        print("Rest time")
        self.gladness += 5
        self.commands -= 0.1

    def is_alive(self):
        if self.commands < -0.5:
            print("bad boy")
            self.alive = False
        elif self.gladness <= 0:
            print("Depression…")
            self.alive = False
        elif self.sleep < 1:
            print("sleep")
            self.alive = False
        elif self.food < 1:
            print("eat")
            self.alive = False

    def end_of_day(self):
        print(f"Gladness = {self.gladness}")
        print(f"Progress ={round(self.commands, 2)}")

    def live(self, day):
        day = "Day" + str(day) + "of" +self.name + "life"
        print(f"{day:=^50}")
        live_cube = random.randint(1, 4)
        if live_cube == 1:
             self.command()
        elif live_cube == 2:
             self.to_sleep()
        elif live_cube == 3:
             self.eat()
        elif live_cube == 4:
            self.to_chill()
            self.end_of_day()
            self.is_alive()

nick = dog(name="dock")
for day in range(365):
    if nick.alive == False:
        break
    nick.live(day)
