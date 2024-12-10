import pyttsx3  # pip install pyttsx3
import speech_recognition as sr  # pip install speechRecognition
import datetime
import wikipedia  # pip install wikipedia
import webbrowser
import os
import smtplib
import requests  # pip install requests
import random

# Initialize Text-to-Speech Engine
engine = pyttsx3.init('sapi5')
voices = engine.getProperty('voices')
engine.setProperty('voice', voices[0].id)  # Use male voice
engine.setProperty('rate', 170)  # Adjust speaking speed


def speak(audio):
    """Speak the provided text."""
    engine.say(audio)
    engine.runAndWait()


def wishMe():
    
    """Greet the user based on the time of the day."""
    hour = int(datetime.datetime.now().hour)
    if 0 <= hour < 12:
        speak("Good Morning!")
    elif 12 <= hour < 18:
        speak("Good Afternoon!")
    else:
        speak("Good Evening!")
        

    speak("I am Jarvis. How can I assist you today?")


def takeCommand():
    """Take microphone input from the user and return it as a string."""
    r = sr.Recognizer()
    with sr.Microphone() as source:
        print("Listening...")
        r.pause_threshold = 1
        audio = r.listen(source)

    try:
        print("Recognizing...")
        query = r.recognize_google(audio, language='en-in')
        print(f"User said: {query}\n")
    except Exception as e:
        print("Could not recognize your voice. Please say that again...")
        return "None"
    return query.lower()


def sendEmail(to, content):
    """Send an email to the specified recipient."""
    try:
        server = smtplib.SMTP('smtp.gmail.com', 587)
        server.ehlo()
        server.starttls()
        # Replace with your email and password
        server.login('youremail@gmail.com', 'your-password')
        server.sendmail('youremail@gmail.com', to, content)
        server.close()
        speak("Email has been sent successfully!")
    except Exception as e:
        print(e)
        speak("I am sorry, I could not send the email.")


def tellJoke():
    """Fetch a random joke from an API."""
    try:
        response = requests.get("https://official-joke-api.appspot.com/random_joke")
        joke = response.json()
        speak(f"Here's a joke: {joke['setup']}")
        speak(f"{joke['punchline']}")
    except Exception as e:
        print(e)
        speak("Sorry, I couldn't fetch a joke at the moment.")


if __name__ == '__main__':
    wishMe()
    while True:
        query = takeCommand()

        # Wikipedia Search
        if 'wikipedia' in query:
            speak('Searching Wikipedia...')
            query = query.replace("wikipedia", "")
            results = wikipedia.summary(query, sentences=2)
            speak("According to Wikipedia")
            print(results)
            speak(results)

        # Open Websites
        elif 'open youtube' in query:
            webbrowser.open("youtube.com")
        elif 'open google' in query:
            webbrowser.open("google.com")
        elif 'open stackoverflow' in query:
            webbrowser.open("stackoverflow.com")
        elif 'open wiki' in query:
            webbrowser.open("wikipedia.com")   

        # Play Music
        elif 'play music' in query:
            music_dir = "C:\\Users\\YourMusicFolder"  # Replace with your music folder
            songs = os.listdir(music_dir)
            if songs:
                song = random.choice(songs)
                os.startfile(os.path.join(music_dir, song))
            else:
                speak("I couldn't find any music in your folder.")

        # Tell the Time
        elif 'the time' in query:
            strTime = datetime.datetime.now().strftime("%H:%M:%S")
            speak(f"The time is {strTime}")

        # Open Applications
        elif 'open code' in query:
            codePath = "C:\\Users\\Desktop\\AppData\\Local\\Programs\\Microsoft VS Code\\Code.exe"  # Replace with your app path
            os.startfile(codePath)

        # Email Functionality
        elif 'email' in query:
            try:
                speak("What should I say?")
                content = takeCommand()
                to = "recipientemail@gmail.com"  # Replace with the recipient's email
                sendEmail(to, content)
            except Exception as e:
                print(e)
                speak("I couldn't send the email.")

        # Fetch a Joke
        elif 'tell me a joke' in query:
            tellJoke()
            print("{query}\n")
        # Fetch a Joke
        elif 'tell me other joke' in query or 'tell me another joke' in query:
            tellJoke()
            print("{query}\n") 

        # Quit the Assistant
        elif 'quit' in query or 'exit' in query or 'bye' in query:
            speak("Goodbye! Have a nice day.")
            break

        else:
            speak("I am sorry, I don't understand that command. Please try again.")


            
