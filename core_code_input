# pip install pyttsx3
# pip install SpeechRecognition
# pip install PyAudio

import pyttsx3
import speech_recognition as sr
import webbrowser
import datetime

bot_template = "BOT : {0}"
user_template = "USER : {0}"

def assistant(audio):
    engine = pyttsx3.init()
    voices = engine.getProperty('voices')
    # [0] for male voice
    # [1] for female voice
    engine.setProperty('voice', voices[1].id)
    engine.say(audio)
    engine.runAndWait()
    
def greeting():
    assistant("Hello, I am your Virtual Assistant.How Can I Help You")
    
def audioinput():
    # this function is all about taking the audio input from the user
    aud = sr.Recognizer()
    with sr.Microphone() as source:
        print('listening and processing')
        # The pause is optional here
        aud.pause_threshold = 0.7
        audio = aud.listen(source)
        # Using try (for valid commands) and exception for when the assistant
        # doesnt "catch" the command
        try:
            print("understanding")
            # en-eu is simply for the accent here english we can use 'en-GB' or 'en-au'
            # for UK and Australian accents
            phrase = aud.recognize_google(audio, language='en-us')
            print("you said: ", phrase)
        except Exception as exp:
            print(exp)
            print("Can you please repeat that")
            return "None"
        return phrase

def theDay():
    # This function is for the day
    day = datetime.datetime.today().weekday() + 1
    # assigning a number makes it a bit cleaner
    Day_dict = {
    1: 'Monday', 2: 'Tuesday',
    3: 'Wednesday', 4: 'Thursday',
    5: 'Friday', 6: 'Saturday',
    7: 'Sunday'
    }
    if day in Day_dict.keys():
        weekday = Day_dict[day]
        print(bot_template.format(weekday))

    assistant("it's " + weekday)

def theTime():
    # This function is for time
    time = str(datetime.datetime.now())
    # time needs to be sliced for
    # better audio comprehension
    print(bot_template.format(time))
    hour = time[11:13]
    min = time[14:16]
    assistant("The time right now is" + hour + "Hours and" + min + "Minutes")
    
def core_code():
    global phrase
    greeting()
    while (True):
        # changing the query to lowercase
        # ensures it works most of the time
        phrase = input("USER : ").lower()
        if "name" in phrase:
            print(bot_template.format("I am your nameless virtual assistant"))
            assistant("I am your nameless virtual assistant")
            continue
        elif "day " in phrase:
            theDay()
            continue
        elif "time" in phrase:
            theTime()
            continue
        elif "google" in phrase:
            print(bot_template.format("Opening Google."))
            assistant("Opening Google ")
            webbrowser.open("www.google.com")
            continue
        elif "search" in phrase:
            print(bot_template.format("Google search"))
            assistant("Google search")
            print(bot_template.format("What are you searching for?"))
            assistant("What are you searching for?")
            x = input("USER (search): ").lower()
            assistant("search"+x+"on google")
            webbrowser.open("www.google.com/search?q="+x)
            continue
        # trigger/condition to exit the program
        elif "bye" in phrase:
            print(bot_template.format("Exiting. Have a Good Day"))
            assistant("Exiting. Have a Good Day")
            exit()
        
core_code()
# https://www.google.com/search?q=
