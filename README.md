from smartwatch_api import Smartwatch, HeartRateMonitor, StepCounter, AlertSystem
smartwatch = Smartwatch()
heart_rate_monitor = HeartRateMonitor()
smartwatch.add_sensor(heart_rate_monitor)

step_counter = StepCounter()
smartwatch.add_sensor(step_counter)

alert_system = AlertSystem()
smartwatch.set_alert_system(alert_system)

def monitor_heart_rate():
    heart_rate = heart_rate_monitor.get_heart_rate()
    print(f"Current Heart Rate: {heart_rate} bpm")
    if heart_rate < 50 or heart_rate > 120:
        alert_system.send_alert("Abnormal heart rate detected!")

def count_steps():
    steps = step_counter.get_steps()
    print(f"Steps taken today: {steps}")
    if steps >= 10000:
        alert_system.send_alert("Congratulations! You've reached your step goal!")

while True:
    monitor_heart_rate()
    count_steps()
    smartwatch.sleep(60)  
 Basic smartwatch function

# Adding communication functionalities
from smartwatch_api import Messaging, CallSystem

messaging = Messaging()
smartwatch.add_messaging(messaging)

call_system = CallSystem()
smartwatch.add_call_system(call_system)

def send_message(contact, message):
    messaging.send_message(contact, message)
    print(f"Message sent to {contact}: {message}")

def make_call(contact):
    call_system.make_call(contact)
    print(f"Calling {contact}...")

send_message("John Doe", "Hello from my smartwatch!")
make_call("Jane Doe")

# Adding productivity features
from smartwatch_api import Calendar, Reminder

calendar = Calendar()
smartwatch.add_calendar(calendar)

reminder = Reminder()
smartwatch.add_reminder(reminder)

def add_event(event):
    calendar.add_event(event)
    print(f"Event added: {event}")
    
def set_reminder(reminder_text, time):
    reminder.set_reminder(reminder_text, time)
    print(f"Reminder set: {reminder_text} at {time}")

add_event("Meeting with Bob at 3 PM")
set_reminder("Take medication", "8:00 AM")

# Main loop to integrate all features
while True:
    monitor_heart_rate()
    count_steps()
    if messaging.has_new_message():
        new_message = messaging.get_new_message()
        print(f"New message from {new_message.sender}: {new_message.content}")
    
    if call_system.has_incoming_call():
        incoming_call = call_system.get_incoming_call()
        print(f"Incoming call from {incoming_call.caller}")
    
    smartwatch.sleep(60)  # Sleep for 60 seconds before next check 
Integrating all features
