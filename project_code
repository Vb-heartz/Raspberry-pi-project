import bluedot
import RPi.GPIO as GPIO
import time

# Set the GPIO mode and pin number for the servo
GPIO.setmode(GPIO.BOARD)
servo_pin = 18

# Setup the GPIO pin as output
GPIO.setup(servo_pin, GPIO.OUT)

# Create a PWM object with a frequency of 50Hz
pwm = GPIO.PWM(servo_pin, 50)

# Define the servo angle range
servo_min_angle = 0
servo_max_angle = 180

# Define the pulse width range for the servo
pulse_min = 2.5  # 0 degrees
pulse_max = 12.5  # 180 degrees

# Start the PWM with 0% duty cycle (servo at 0 degrees)
pwm.start(0)

def move_servo(angle):
    # Convert the angle to duty cycle
    duty_cycle = (angle / 18) + 2.5
    pwm.ChangeDutyCycle(duty_cycle)


# Callback functions for different buttons
def  handle_event(pos):
    if pos.top:
        move_servo(180)  # Move to 180 degrees
    elif pos.bottom:
        move_servo(0)  # Move to 0 degrees
    elif pos.middle:
        move_servo(90)  # Move to 90 degrees


# Create a BlueDot object
bd = bluedot.BlueDot()

# Assign the callback functions to different buttons
bd.when_pressed = handle_event

# Run the program until it's interrupted
try:
    while True:
        time.sleep(0.1)
except KeyboardInterrupt:
    # Clean up the GPIO on program exit
    GPIO.cleanup()
