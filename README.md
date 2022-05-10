# Access-control_final
#My project is to do something like access control. When the sensor detects that someone approaching the door is less than 0.3 meters away. It will automatically show that you need to enter a password to enter.

from gpiozero import DistanceSensor
from gpiozero import LED
from gpiozero import Button
from time import sleep
sensor = DistanceSensor(echo=24, trigger=23, max_distance=1)
led = LED(4)
button = Button(17)
mypassword = str(1234)
def blink():
    led.on()
    sleep(0.2)
    led.off()
    sleep(0.2)
    
while True:
  distance=sensor.distance  
  sleep(0.1)
  if  distance <= 0.3:
          code=input(str("Please type your password:"))
          print("Please press the Button to Enter your password."
          button.wait_for_press()
          if mypassword==code:
                led.on()
                print("Welcome!")
                sleep(5)
                led.off()
               
          else:
              blink()
              blink()
              blink()
              blink()
              blink()
              print("The password you type is WRONG!")
              print("please press the Button to Continue!")
              button.wait_for_press()
