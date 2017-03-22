# Orchestrator
This project aims at running multiples instances of LOTRO game clients and synchronize them to play as an orchestra in game.
Current features :
  - log and launch multiples accounts on the same computer
  - synchronize clients to play tracks of the targeted music
  - support LOTRO French client, but dont worry, english implemented but not tested, german is present in code too but i'll need translator
  - logs for debug

roughtly this is how the launcher part works :
- login/password is sent to authentication server
- he answers with a ticket if correct
- launch lotroclient.exe with ticket as argument to play
- repeat previous steps for each account based on a file account list

roughtly this is how synchronization of clients works :
  - custom version of plugin songbookbb writes to a file the file path of the targeted music if sync button is pushed
  - this .abc file is parsed, needed instrument for each track is stored
  - handmade plugin writes to file the name of the currently equipped instrument for each lotro client 
  - player/instrument list and track/instrument list are crossed, a player/track instrument list is created based on this
  - now we know who must play what, we can send the needed commands to every clients, hotkeynet does it
  
  as this tool use the api the game provides to do automation, and no direct memory editing, 
  and also as this program is meant to make possible for one player to make an orchestra and not soloing dungeons,
  it should not be a problem to lotro staff.
  the game api has been made slow to make botting difficult, so when writing instruments or music name to file it take few seconds
  

I have a working tool using the game LUA API, java code and hotkeynet but it's quite messy to install and use for now
my current steps is to merge these multiple files and functionnalities in the same java program for ease of coding and contributing :
  - remove hotkeynet from this toolset and replace it by windows api calls using JNI,
  so that i can manipulate directly a client window,  i want to do this because i find this part of the code big, 
  clumsy and a bit obfuscated (script parsing and editing for an other exe), really not helping for contributors
  - remove some hardcoded informations (files path mainly)
  - put all needed informations by the program in one ini file
  (optionnal, create a GUI to setup ini file content)

when all of this will be done, i will commit code (probably in two weeks max)
