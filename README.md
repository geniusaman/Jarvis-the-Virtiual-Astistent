# Jarvis-the-Virtiual-Astistent
## Usage:
***1. First Step is to install all requirnment modules and library in python by following command,*** 
```
!pip install -r requirnment.txt
```
***2. After successfully installing requirnment file now finally run our main.py file for Jarvis-the-Virtiual-Astistent,***
```
!python main.py
```
> Before Executing main.py file make sure you have Installed all the specified versions of moduels mentioned in the requirement.txt.


# ***Workings:***
> A VA Build on python by using several libraries. it can perform various tasks by just spoken command
import os
import pyttsx3
import speech_recognition as sr
import webbrowser
import pywhatkit
from pywikihow import search_wikihow
from googletrans import Translator




def get_audio():
    r = sr.Recognizer()
    with sr.Microphone() as source :
        print("Listening....")
        audio = r.listen(source)
        said = ''
        r.pause_threshold = 1

        try:
            print("Recognizing....")
            said = r.recognize_google(audio , language='eng-in')
            print('You said : ',said)

        except Exception as e :

            print("Exception :" + str(e))

    return said

def get_audio_Hindi():
    r = sr.Recognizer()
    with sr.Microphone() as source :
        print("Listening....")
        audio = r.listen(source)
        said = ''
        r.pause_threshold = 1

        try:
            print("Recognizing....")
            said = r.recognize_google(audio , language='Hi')
            print('You said : ',said)

        except Exception as e :

            print("Exception :" + str(e))

    return said

def Translation():
    speak1("In what language you want to make translation")
    lang = get_audio()
    if "English to Hindi" in lang:

        speak1("say the line")
        line = get_audio()
        translate = Translator()
        result = translate.translate(line, dest="hi")
        Text = result.text
        speak_Hi(Text)


    elif "Hindi to English" in lang:
     speak1("say the line")
     line2 = get_audio_Hindi()
     translator = Translator()
     result = translator.translate(line2)
     Text = result.text
     speak1(Text)

def whatsapp():
    speak1("Tell me the name of the person sir")
    name = get_audio()

    if "Aslam" in name:
       speak1("tell me the message sir")
       msg = get_audio()
       speak1("tell me the time sir !")
       speak1("Time in hour sir")
       hour = int(get_audio())
       speak1("tell me the minute sir")
       minute = int(get_audio())
       pywhatkit.sendwhatmsg("+917400242987",msg,hour,minute)
       speak1("done sir! messege is sending to" + name + "sir!")

    elif "PK" in name:
       speak1("tell me the message sir")
       msg = get_audio()
       speak1("tell me the time sir !")
       speak1("Time in hour sir")
       hour = int(get_audio())
       speak1("tell me the minute sir")
       minute = int(get_audio())
       pywhatkit.sendwhatmsg("+918657336613",msg,hour,minute)
       speak1("done sir! messege is sending to" + name + "sir!")

    elif "Abhishek" in name:
       speak1("tell me the message sir")
       msg = get_audio()
       speak1("tell me the time sir !")
       speak1("Time in hour sir")
       hour = int(get_audio())
       speak1("tell me the minute sir")
       minute = int(get_audio())
       pywhatkit.sendwhatmsg("+918828763583",msg,hour,minute)
       speak1("done sir! messege is sending to" + name + "sir!")


    elif "Ganesh" in name:
       speak1("tell me the message sir")
       msg = get_audio()
       speak1("tell me the time sir !")
       speak1("Time in hour sir")
       hour = int(get_audio())
       speak1("tell me the minute sir")
       minute = int(get_audio())
       pywhatkit.sendwhatmsg("+918268029972",msg,hour,minute)
       speak1("done sir! messege is sending to" + name + "sir!")


    else:
        speak1("tell me the phone number")
        phone = int(get_audio())
        ph = "+91" +phone
        speak1("tell me the message sir")
        msg = get_audio()
        speak1("tell me the time sir !")
        speak1("Time in hour sir")
        hour = int(get_audio())
        speak1("tell me the minute sir")
        minute = int(get_audio())
        pywhatkit.sendwhatmsg(ph, msg, hour, minute)
        speak1("done sir! messege is sending to" + name + "sir!")

def speak0(text):
    engine = pyttsx3.init()
    voices = engine.getProperty('voices')
    engine.setProperty('voice', voices[5].id)
    engine.setProperty('rate', 155)

    engine.say(text)
    print(text)
    engine.runAndWait()

def speak1(text):
    engine = pyttsx3.init()
    voices = engine.getProperty('voices')
    engine.setProperty('voice' , voices[0].id)
    engine.setProperty('rate', 155)




    engine.say(text)
    print(text)
    engine.runAndWait()

def speak_Hi(text1):
    engine = pyttsx3.init()
    voices = engine.getProperty('voices')
    engine.setProperty('voice' , voices[2].id)
    engine.setProperty('rate', 155)





    engine.say(text1)
    print(text1)
    engine.runAndWait()







#speak0('Welcome to the world of Guptaji. I am Gupta Jarvis 1.0')
#speak0('assigning BAli for you')
speak1('bali activated')



def task_executer():
 while  True:
  text = get_audio()
 #text = input('Enter here: ')
  if "how are you" in text:
      speak1("I am good sir !  How are you?")

  elif "who made you" in text:
      speak1("i was discoverd by shri shri shri Aaman Gupta Sir")


  elif " you can go" in text:
      speak1("ok sir will meet soon")
      break

  elif "YouTube" in text:
      speak1("ok sir ! This is what i Found sir")
      text = text.replace("Gupta ji", "")
      text = text.replace("YouTube ", "")
      web = 'https://www.youtube.com/results?search_query=' + text
      webbrowser.open(web)
      speak1("Done sir")

  # elif " Google search" in text:
  #     speak1("ok sir ! this is what i found")
  #     text = text.replace("Gupta ji", "")
  #     text = text.replace("Google search", "")
  #     pywhatkit.search(text)
  #     speak1("done sir")

  elif "launch" in text:
      speak1("tell me the name of website")


      name = get_audio()
      web = "http://www." + name + ".com"
      webbrowser.open(web)
      speak1("Done sir")

  elif "play music" in text:
      speak1("tell me your favourite song")
      name = get_audio()
      pywhatkit.playonyt(name)
      speak1("done sir")

  elif "WhatsApp" in text:
      whatsapp()

  elif "translate" in text:
      Translation()

  elif "remember that" in text:
      remebermsg = text.replace("remember that", '')
      remenbermsg = remebermsg.replace("Bali", '')
      speak1("you told me to remind you"+remenbermsg)
      remember = open('data.txt','w')
      remember.write(remenbermsg)
      remember.close()


  elif "anything you remember" in text:
      remember = open('data.txt', 'r')
      speak1("you told me that" + remember.read())


  elif "Google search" in text:
         import wikipedia as googlescrap
         text = text.replace("Bali", "")
         text = text.replace("Google search", "")
         text = text.replace("google", "")
         speak1("this is what I found")

         try:
             pywhatkit.search(text)
             result = googlescrap.summary(text,3)
             speak_Hi(result)


         except:
             speak1("sorry! no speakable data found")


  elif "how to" in text:
      speak1('getting gathering data for you')
      op = text.replace("Bali", "")
      max_result = 1
      how_to_fun = search_wikihow(op,max_result)
      assert len(how_to_fun)==1
      how_to_fun[0].print()
      speak1(how_to_fun[0].summary)

  elif "Abhishek" in text:
      speak_Hi("प्रियांशु भैया आपको नहीं पता पर आप भोसड़ीवाले हो")






