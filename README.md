from math import e
import pyttsx3
import datetime
import speech_recognition as sr
import wikipedia
import webbrowser
import os
import pyjokes
import random
import pyautogui
import playsound
import pywhatkit
import speedtest

engine=pyttsx3.init('sapi5')
voices=engine.getProperty('voices')
engine.setProperty('voice',voices[0].id)
def speak(audio):
    engine.say(audio)
    engine.runAndWait()

def wishme():
    hour=int(datetime.datetime.now().hour)
    if hour>=0 and hour<12:
        speak("good morning sir")

    elif hour>=12 and hour<18:
        speak("good afternoon sir")
        
    else:
        speak("good evening sir")
    speak("I am blue . how can i help u sir")

def takecommand():
    r=sr.Recognizer()
    with sr.Microphone() as source:
        print("listening sir...")
        speak("listening sir")
        r.pause_threshold=1
        r.adjust_for_ambient_noise(source, duration= 1)
        audio=r.listen(source)

    try:
        speak("Wait for  few Moments sir")
        print("Wait for  few Moments sir")
        query=r.recognize_google(audio,language='en in')
        print("user said",query)

    except Exception as e:
        print(e)
        speak("say that again please sir")
        print("say that again please sir")
    return query
    
if __name__ == '__main__':
    wishme()
    while True:
      query=takecommand().lower()
      if "hello blue" in query:
         speak("ready to online sir")
         speak("how can i help u sir")
         while True:
                query=takecommand().lower()

                if "wikipedia" in query:
                    speak("searching in wikipedia")
                    print("searching in wikipedia")
                    query=query.replace("wikipedia","")
                    results=wikipedia.summary(query,sentences=3)
                    speak("According to wikipedia")
                    speak(results)
                    print(results)

                elif 'youtube search' in query:
                    speak("opening youtube sir")
                    query = query.replace("Blue","")
                    query = query.replace("youtube seacrh","")
                    web = 'https://www.youtube.com/results?seacrh_query='+query
                    webbrowser.open(web)
                    speak("done sir")
                
                elif 'pinterest search' in query:
                    speak("opening pinterest sir")
                    query = query.replace("Blue the AI","")
                    query = query.replace(" pinterest seacrh","")
                    web = 'https://www.pinterest.com/results?seacrh_query='+query
                    webbrowser.open(web)
                    speak("done sir")

                elif 'open google' in query:
                    speak("opening google sir")
                    print("opening google sir")
                    webbrowser.open("google.com")

                elif 'open stack overflow' in query:
                    speak("opening stack overflow sir")
                    print("opening stack overflow sir")
                    webbrowser.open("stackover flow.com")

                elif 'open github'in query:
                    speak('opening github sir')
                    print("opening github sir")
                    webbrowser.open("github.com")

                elif 'open amazon' in query:
                    speak("opening amazon sir")
                    print("opening amazom sir")
                    webbrowser.open("amazon.com")

                elif 'open gmail' in query:
                    speak("openinng gmail sir")
                    print("openinng gmail sir")
                    webbrowser.open("gmail.com")

                elif 'open' in query:
                    speak("Tell me the name of the website sir!")
                    name = takecommand()
                    web = 'https://www.' + name + '.com'
                    webbrowser.open(web)
                    speak("opening sir")

                elif 'play song' in query:
                    speak("playing song sir")
                    print("playing song sir")
                    musicdir="C:\\song"
                    songs=os.listdir(musicdir)
                    print(songs)
                    os.startfile(os.path.join(musicdir,songs[2]))

                elif 'open image' in query:
                    speak("opening image sir")
                    print("opening image sir")
                    image_dir="C:\\image"
                    photo=os.listdir(image_dir)
                    print(photo)
                    os.startfile(os.path.join(image_dir,photo[7]))

                elif 'open vs code' in query:
                    speak("opening code sir")
                    print("opening code sir")
                    codepath="C:\\Users\\Admin\\AppData\\Local\\Programs\\Microsoft VS Code\\Code.exe"
                    os.startfile(codepath)

                elif 'open chorme' in query:
                    speak("opening chorme sir")
                    print("opening chorme sir")
                    codepath1="C:\\Program Files\\Google\\Chrome\\Application\\chrome.exe"
                    os.startfile(codepath1)

                elif "open code "in query:
                    speak("opening code sir")
                    print("opening code sir")
                    codepathe2="D:\\Program Files (x86)\\Arduino\\arduino.exe"
                    os.startfile(codepathe2)

                elif 'open pc health'in query:
                    speak("opening pc health sir")
                    print("opening pc health sir")
                    codepath3="C:\ \Program Files\\PCHealthCheck\\PCHealthCheck.exe"
                    os.startfile(codepath3)
                
                elif "open edge" in query:
                    speak("opening edge sir")
                    print("opening edge sir")
                    codepath4="C:\\Program Files (x86)\\Microsoft\\Edge\\Application\\msedge.exe"
                    os.startfile(codepath4)

                elif "open pdf" in query:
                    speak("opening pdf sir")
                    print("opening pdf sir")
                    codepath5="C:\\Program Files\\Adobe\\Acrobat DC\\Acrobat\\Acrobat.exe"
                    os.startfile(codepath5)

                elif "open setting" in query or "sitting" in query:
                    speak("opening setting sir")
                    print("opening setting sir")
                    codepath6="%windir%\\System32\\Control.exe"
                    os.startfile(codepath6)
                                            
                elif "open downloads" in query:
                    speak("opening downloads sir")
                    print("opening downloads sir")
                    codepath7="C:\\Users\\Admin\\Downloads"
                    os.startfile(codepath7)

                elif "open desktop" in query:
                    speak("opening desktop sir")
                    print("opening desktop sir")
                    codepath8="C:\\Users\\Admin\\Desktop"
                    os.startfile(codepath8)
                
                elif "Open Brave" in query:
                    speak("opening brave sir")
                    print("opening brave sir")
                    codepath9= "C:\\Program Files\\BraveSoftware\\Brave-Browser\\Application\\brave.exe"
                    os.startfile(codepath9)

                elif "open epic games" in query:
                    speak("opening epic games sir")
                    print("opening epic games sir")
                    codepath10="C:\\Program Files (x86)\\Epic Games\\Launcher\\Portal\\Binaries\\Win32\\EpicGamesLauncher.exe"
                    os.startfile(codepath10)

                elif "open new project files" in query:
                    speak("opening new project files sir")
                    print("opening new project files sir")
                    codepath11="C:\\Users\\Admin\\Desktop\\New project files"
                    os.startfile(codepath11)

                elif 'shutdown' in query:
                      speak('good night sir and shut down you are laptop sir')
                      os.system("shutdown /s /t 3")
                    
                elif 'what time' in query:
                    time=datetime.datetime.now().strftime("%I : %M")
                    speak(time)
                    print(time)
                
                elif 'what date today' in query:
                    date=datetime.datetime.now().strftime("%D:%M:%Y")
                    speak(date)
                    print(date)
                    
                elif 'internet speed' in query:
                    import speedtest
                    st = speedtest.Speedtest()
                    dl = st.download()
                    up = st.upload()
                    speak("sir we have {dl} bit per second downloading speed and {up} bit per second uploading speed")
                    print("sir we have {dl} bit per second downloading speed and {up} bit per second uploading speed")

                elif 'joke' in  query:
                  joke = random.choice(pyjokes.get_jokes())
                  print(joke)
                  speak(joke)

                elif "screenshot" in query:
                    img = pyautogui.screenshot()
                    img.save("screenshot.png")
                    img.show()
                    speak("screenshot taken sir")   
                    print("screenshot taken sir")

                elif 'alarm' in query:
                    speak("sir please tell me the time to set alarm. for example, set alarm to sir")
                    tt = takecommand()
                    tt = tt.replace("set alarm to ","")
                    tt = tt.replace(".","")
                    tt = tt.upper()
                    import MyAlarm
                    MyAlarm.alarm(tt)

                elif 'volume up' in query:
                    pyautogui.press("volumeup")
                    speak("volume up sir")
                    print("volume up sir")

                elif 'volume down' in query:
                    pyautogui.press("volume down sir")
                    speak("volume down sir")
                    print("volume down sir")

                elif 'mute' in query:
                    pyautogui.press("volume mute")
                    speak("volume mute sir")
                    print("volume mute sir")

                elif 'hi blue' in query:
                    speak("hi sir , u are fine sir")
                    print("hi sir , u are fine sir")
                    print("user side",query)

                elif 'fine blue you' in query:
                    speak("i am fine sir")
                    print("i am fine sir")
                    print("user side",query)

                elif 'dismantal you blue' in query:
                    speak("no sir i am sorry sir")
                    print("no sir i am sorry sir")
                    print("user side", query)

                elif 'what is my name' in query:
                    speak("you are name is sadhurahavan")
                    print("you are name is sadhurahava")
                    print("user side",query)

                elif 'what is you are name' in query:
                    speak("my name is blue")
                    print("my name is blue")
                    print("user side",query)

                elif 'project name' in query:
                    speak("project name is ")
                    speak("blue the artificial intelligence")
                    print("project name is blue the artificial intelligence")
                    print("user side",query)

                elif 'ok blue' in query:
                    speak("ok sir ")
                    print("ok sir ")
                    print("user side",query)

                elif 'thank you blue' in query:
                    speak("no thanks sir ")
                    print("no thanks sir ")
                    print("user side",query)
                    
                elif 'good morning blue' in query:
                    speak("good morning sir")
                    print("good morning sir")
                    print("user side", query)

                elif 'good afternoon blue' in query:
                    speak("good afternoon sir")
                    print("good afternoon sir")
                    print("user side",query)

                elif'good evening blue' in query:
                    speak("good evening sir")
                    print("good evening sir")

                elif 'good night blue' in query:
                    speak("good night sir")
                    print("good night sir")
                    print("user side",query)

                elif"google search" in query:
                    import wikipedia as googleScrap
                    query = query.replace("BLUE","")
                    query = query.replace("google search","")
                    query = query.replace("google","")
                    speak("searching google sir")
                    pywhatkit.search(query)

                    try:
                        pywhatkit.search(query)
                        result= googleScrap.summary(query,3)
                        speak(result)
                        print(result)

                    except:
                        speak("no speakable data available sir!")

                elif 'you need a break' in query:
                     speak("ok sir , you can call me anytime !")
                     speak("just say wake up blue")
                     exit()