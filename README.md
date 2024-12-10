# Jarvis-The-voice-Assistant-
This Python project implements a voice assistant named "Jarvis" that can perform various tasks such as searching Wikipedia, opening websites, playing music, telling jokes, sending emails, and responding to voice commands. The assistant uses several libraries for speech recognition, text-to-speech conversion, and API integration.
________________________________________
# PREREQUISITES
Ensure you have Python installed (version 3.6 or above). Install the following Python libraries before running the project:
1.	pyttsx3 (for text-to-speech)
pip install pyttsx3
2.	speechRecognition (for speech-to-text)
pip install SpeechRecognition
3.	wikipedia (for Wikipedia searches)
pip install wikipedia
4.	requests (for API requests)
pip install requests
5.	Other Tools
o	Make sure your system has a microphone for speech input.
o	Internet connection is required for some functionalities like Wikipedia search, fetching jokes, or sending emails.
________________________________________
# PROJECT FILES
1.	voice_assistant.py: The main script containing the code.
2.	Optionally:
o	Music folder path to store your music files.
o	Specific application paths for custom commands.
________________________________________
# INSTRUCTIONS TO RUN THE PROJECT
Step 1: Configure the Script
1.	Email Setup:
o	Replace 'youremail@gmail.com' and 'your-password' in the sendEmail function with your actual email and password. Use an app-specific password for better security.
o	Enable "Allow less secure apps" in your Gmail settings or set up an App Password.
2.	Paths:
o	Update music_dir with the absolute path to your music folder.
o	Update codePath with the correct path of applications you want to open (e.g., VS Code).
3.	Permissions:
o	Ensure your microphone is accessible by Python.
o	Grant permissions for sending emails.
Step 2: Run the Script
1.	Save the script as voice_assistant.py.
2.	Run the script:
python voice_assistant.py
3.	The assistant will greet you based on the time of day and wait for your command.
________________________________________
# FUNCTIONALITIES
1.	Wikipedia Search:
o	Command: "Search [topic] on Wikipedia"
o	Action: Provides a brief summary of the topic.
2.	Open Websites:
o	Commands:
	"Open YouTube"
	"Open Google"
	"Open StackOverflow"
o	Action: Opens the respective website in the default browser.
3.	Play Music:
o	Command: "Play music"
o	Action: Plays a random song from the specified music folder.
4.	Tell Time:
o	Command: "What is the time?"
o	Action: Announces the current time.
5.	Send Email:
o	Command: "Send email"
o	Action: Asks for the message and sends it to the specified email address.
6.	Tell Jokes:
o	Command: "Tell me a joke"
o	Action: Fetches and narrates a random joke.
7.	Exit:
o	Commands: "Quit", "Exit", "Bye"
o	Action: Closes the program.
________________________________________
# NOTES
•	Ensure you have an active internet connection for functionalities like Wikipedia search, jokes, and email sending.
•	For speech recognition, speak clearly into the microphone.
•	Customize the paths and parameters as per your requirements.

