# voice-based-email-system-for-blind-people 
it is a voice based email system for blind people end to end project

import speech_recognition as sr
import pyaudio
import platform
import sys
import import imaplib
from bs4 import BeautifulSoup import email
speech_recognition as sr smtplib
import os, time
pyglet.have_avbin=True # audio decode 
#project: :. Project: Voice based Email for blind :.
#fetch project name
tts = gTTS(text="Project: Voice based Email for blind", lang='en')
ttsname=("name.mp3")
tts.save(ttsname)
music = pyglet.media.load(ttsname, streaming = False) music.play()
time.sleep(music.duration) os.remove(ttsname)

#login from os
login = os.getlogin
print ("You are logging from : "+login())
#choices
print ("0. composed a mail.")
tts = gTTS(text="option 0. composed a mail.", lang='en') ttsname=("hello.mp3")
tts.save(ttsname)
music = pyglet.media.load(ttsname, streaming = False) music.play()
time.sleep(music.duration) os.remove(ttsname)
print ("1. Check your inbox")
tts = gTTS(text="option 1. Check your inbox", lang='en') ttsname=("second.mp3")
tts.save(ttsname)
music = pyglet.media.load(ttsname, streaming = False) music.play()
time.sleep(music.duration) os.remove(ttsname)
#this is for input choices
tts = gTTS(text="Your choice ", lang='en') ttsname=("hello.mp3")

tts.save(ttsname)
music = pyglet.media.load(ttsname, streaming = False) music.play()
time.sleep(music.duration) os.remove(ttsname)
#voice recognition part
r = sr.Recognizer()
#m = sr.Microphone()
with sr.Microphone() as source:
r.adjust_for_ambient_noise(source,duration=1) print ("Your choice:") r.energy_threshold+=280 audio=r.listen(source)
print ("ok done!!")
try:
text=r.recognize_google(audio, language='en-GB') print ("You said : "+text)
except sr.UnknownValueError:
print("Google Speech Recognition could not understand audio.")
except sr.RequestError as e:
print("Could not request results from Google Speech Recognition service; {0}".format(e))
#choices details
if text == '0' or text == 'zero' or text == 'zhero' or text == 'hero' or text == 'Hero':
r = sr.Recognizer() #recognize

with sr.Microphone() as source: print ("Your message :") audio=r.listen(source)
print ("ok done!!")
try: text1=r.recognize_google(audio) print ("You said : "+text1)
msg = text1
except sr.UnknownValueError:
print("Google Speech Recognition could not understand audio.")
except sr.RequestError as e:
print("Could not request results from Google Speech Recognition service; {0}".format(e))
mail = smtplib.SMTP('smtp.gmail.com',587) #host and port area
mail.ehlo() #Hostname to send for this command defaults to the FQDN of the local host. mail.starttls() #security connection
mail.login(‘ xxxxxx@gmail.com','sgna moxq mxfs fnio') #login part mail.sendmail('yyyyyyyyyy@gmail.com','yyyyyyyyyyyyy@gmail.com',msg) #send part print ("Congrates! Your mail has send. ")
tts = gTTS(text="Congrates! Your mail has send. ", lang='en')
ttsname=("send.mp3")
tts.save(ttsname)
music = pyglet.media.load(ttsname, streaming = False)
music.play()
time.sleep(music.duration)
os.remove(ttsname)
mail.close()
if text == '1' or text == 'one' or text == 'van' or text == 'won':
mail = imaplib.IMAP4_SSL('imap.gmail.com',993) #this is host and port area .... ssl security
#ssl= secure socket layer

unm = ('xxxxxxxxxx@gmail.com') #username
psw = ('sgna moxq mxfs fnio') #password
mail.login(unm,psw) #login
stat,total=mail.select('Inbox') #totalnumberofmailsininbox print ("Number of mails in your inbox :"+str(total))
tts = gTTS(text="Total mails are :"+str(total), lang='en') #voice out ttsname=("total.mp3")
tts.save(ttsname)
music = pyglet.media.load(ttsname, streaming = False) music.play()
time.sleep(music.duration) os.remove(ttsname)
#unseen mails
unseen = mail.search(None, 'UnSeen') # unseen count
print ("Number of UnSeen mails :"+str(unseen))
tts = gTTS(text="Your Unseen mail :"+str(unseen), lang='en')
ttsname=("unseen.mp3") #Example: path -> C:\Users\sayak\Desktop> just change with your
desktop directory. Don't use my directory. tts.save(ttsname)
music = pyglet.media.load(ttsname, streaming = False) music.play()
time.sleep(music.duration)
os.remove(ttsname)
#search mails
result, data = mail.uid('search',None, "ALL")
inbox_item_list = data[0].split()
new = inbox_item_list[-1]
old = inbox_item_list[0]
result2, email_data = mail.uid('fetch', new, '(RFC822)') #fetch

raw_email = email_data[0][1].decode("utf-8") #decode email_message = email.message_from_string(raw_email) print ("From: "+email_message['From'])
print ("Subject: "+str(email_message['Subject']))
tts = gTTS(text="From: "+email_message['From']+" And Your subject: "+str(email_message['Subject']), lang='en')
ttsname=("mail.mp3")
tts.save(ttsname)
music = pyglet.media.load(ttsname, streaming = False) music.play()
time.sleep(music.duration)
os.remove(ttsname)
#Body part of mails
stat, total1 = mail.select('Inbox')
stat, data1 = mail.fetch(total1[0], "(UID BODY[TEXT])") msg = data1[0][1]
soup = BeautifulSoup(msg, "html.parser")
txt = soup.get_text()
print ("Body :"+txt)
tts = gTTS(text="Body: "+txt, lang='en') ttsname=("body.mp3")
tts.save(ttsname)
music = pyglet.media.load(ttsname, streaming = False) music.play()
time.sleep(music.duration)
os.remove(ttsname)
mail.close()
mail.logout()



