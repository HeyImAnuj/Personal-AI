# Personal-AI
creating basic AI model:
 import speech_recognition as sr
 import pyttsx3
 import datetime
 import wikipedia
 import webbrowser
 import os
 import time
 import subprocess
 import json
 import requests
 
engine = pyttsx3.init('sapi5'),
voices = engine.getProperty('voices'),
engine.setProperty('rate', 150),
engine.setProperty('volume', 3.0),
engine.setProperty('voice', voices[0].id)

def speak(text):

    engine.say(text)
    engine.runAndWait()
    
def wishMe():
    hour=datetime.datetime.now().hour
    if hour>=0 and hour<=12:
        speak('Hello, Good morning')
        print('Hello, Good Morning')
    elif hour>=12 and hour<18:
        print('Hello, Good Afternoon')
        speak('Namaste, shuv dopahar')
    else:
        print("Good Evening, sir")
        speak('Good Evening, sir')
        
def takeCommand():

    r=sr.Recognizer()
    with sr.Microphone() as source:
    
        print('Listening...')
        audio=r.listen(source)
        
        try:
            statement=r.recognize_google(audio,language='en-in')
            print(f"user said: {statement}\n")
        except Exception as e:
            speak("pardon me, please say that again")
            return "None"
        return statement
print("Hello sir, Loading your AI personal assistant ")
speak("Hello sir, Loading your AI personal assistant ")
wishMe()

if __name__=='__main__':
    
    while (True):
        
        speak("Tell me how can i help you?")
        statement=takeCommand().lower()
        if statement==0:
            continue
        if "sleep" in statement or "ok bye" in statement or "stop" in statement:
            print("your personal assistent is shutting down, Good bye")
            speak("your personal assistent is shutting down, Good bye")
            break
