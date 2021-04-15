import pigpio
import time

class Motor(object):
    def __init__(self):
        pigpio.exceptions = False
        self.pi = pigpio.pi()
        if not self.pi.connected:
            exit()
        self.left_0 = 4
        self.left_1 = 18
        self.left_en = 23
        self.right_0 = 12
        self.right_1 = 13
        self.right_en = 24

        self.speed = 200

        self.xbuff = ''

    def stop(self):
        print("stop")
        self.pi.write(self.left_en, 0)
        self.pi.write(self.left_0, 0)
        self.pi.write(self.left_1, 0)
        self.pi.write(self.right_en, 0)
        self.pi.write(self.right_0, 0)
        self.pi.write(self.right_1, 0)

    def forward(self):
        print("forward")
        self.pi.write(self.left_en, 1)
        self.pi.set_PWM_dutycycle(self.left_0,  self.speed)
        self.pi.write(self.left_1, 0)

        self.pi.write(self.right_en, 1)
        self.pi.set_PWM_dutycycle(self.right_0,  self.speed)
        self.pi.write(self.right_1, 0)
        
    def backward(self):
        print("back")
        self.pi.write(self.left_en, 1)
        self.pi.write(self.left_0, 0)
        self.pi.set_PWM_dutycycle(self.left_1,  self.speed)

        self.pi.write(self.right_en, 1)
        self.pi.write(self.right_0, 0)
        self.pi.set_PWM_dutycycle(self.right_1,  self.speed)
        
    def left(self):
        print("left")
        self.pi.write(self.right_en, 1)
        self.pi.set_PWM_dutycycle(self.right_0,  self.speed)
        self.pi.write(self.right_1, 0)
        
        self.pi.write(self.left_en, 1)
        self.pi.write(self.left_0, 0)
        self.pi.set_PWM_dutycycle(self.left_1,  self.speed)

    def right(self):
        print("right")
        self.pi.write(self.left_en, 1)
        self.pi.set_PWM_dutycycle(self.left_0,  self.speed)
        self.pi.write(self.left_1, 0)

        self.pi.write(self.right_en, 1)
        self.pi.write(self.right_0, 0)
        self.pi.set_PWM_dutycycle(self.right_1,  self.speed)
        
    def control(self,x):
        if x == 'forward':
            self.forward()
            time.sleep(0.1)
            self.stop()
        elif x == 'backward':
            self.backward()
            time.sleep(0.1)
            self.stop()
        elif x == 'left':
            self.left()
            time.sleep(0.1)
            self.stop()
        elif x == 'right':
            self.right()
            time.sleep(0.1)
            self.stop()
        else:
            self.stop() 

