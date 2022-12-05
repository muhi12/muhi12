
import kivy
from kivy.app import App
from kivy.uix.label import Label
from kivy.uix.gridlayout import GridLayout
from kivy.uix.textinput import TextInput
from kivy.uix.button import Button
from kivy.clock import Clock

class StopClock(GridLayout):
    def __init__(self, **kwargs):
        super(StopClock, self).__init__(**kwargs)
        self.cols = 1
        self.time = 0
        self.paused = False

        self.add_widget(Label(text='Stop Watch', font_size='20sp'))
        self.time_lbl = Label(text="0:00:00")
        self.add_widget(self.time_lbl)

        self.start_btn = Button(text="Start")
        self.start_btn.bind(on_press=self.start)
        self.add_widget(self.start_btn)

        self.stop_btn = Button(text="Stop")
        self.stop_btn.bind(on_press=self.stop)
        self.add_widget(self.stop_btn)

        self.reset_btn = Button(text="Reset")
        self.reset_btn.bind(on_press=self.reset)
        self.add_widget(self.reset_btn)

    def start(self, instance):
        self.paused = False
        Clock.schedule_interval(self.update, 1)

    def stop(self, instance):
        self.paused = True
        Clock.unschedule(self.update)

    def reset(self, instance):
        self.time = 0
        self.time_lbl.text = "0:00:00"

    def update(self, dt):
        if self.paused:
            return
        self.time += 1
        m, s = divmod(self.time, 60)
        h, m = divmod(m, 60)
        self.time_lbl.text = "%d:%02d:%02d" % (h, m, s)
#This code is part of a program that creates a timer widget. It defines a function called update, which is used to increment the timer. The function takes one parameter, dt, which is the delta time, or the amount of time that has elapsed since the last update. The if statement checks to see whether the timer is paused, and if so, exits the function. The time variable is then incremented by one, and the m, s, h, and m variables are used to calculate the hours, minutes, and seconds of the timer. Finally, the time_lbl.text is set to the current time in a HH:MM:SS format.  1
class StopClockApp(App):
    def build(self):
        return StopClock()

StopClockApp().run()- 👋 



Hi, I’m @muhi12
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
muhi12/muhi12 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
