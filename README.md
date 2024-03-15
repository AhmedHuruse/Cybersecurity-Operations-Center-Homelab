# Cybersecurity Operations Center Homelab

## Objective and Description


### Skills Learned


  
  

### Tools Used


## Steps
- Step 1:
  
  <img src="https://i.imgur.com/F9MHOD2.png" height="80%" width="80%" alt="Malware Analysis Steps"/>
- Step 2:
  
  <img src="https://i.imgur.com/vx5jb1d.png" height="80%" width="80%" alt="Malware Analysis Steps"/>
- Step 3:
  
  <img src="https://i.imgur.com/kABf92P.png" height="40%" width="40%" alt="Malware Analysis Steps"/> <img src="https://i.imgur.com/TZOJAb5.png" height="40%" width="40%" alt="Malware Analysis Steps"/>
- Step 4:
  
 <img src="https://i.imgur.com/3OsCKef.png" height="80%" width="80%" alt="Malware Analysis Steps"/> 

- Step 5:
  
   <img src="https://i.imgur.com/4DjgVQG.png" height="40%" width="40%" alt="Malware Analysis Steps"/> <img src="https://i.imgur.com/E7y04bY.png" height="40%" width="40%" alt="Malware Analysis Steps"/>
- Step 5: Since we found out that we are dealing with an ole file, we can use the ole command and see which ole tools can be useful to use so that we can learn more information. We use oledump.py tool and it seems to function similarly as the previous rtfdump.py tool but for ole files. We find a single stream labeled "EQUATION NATIVE" and we drill into it do not find much use for it. Under it could be running shellcode that gives instructions so maybe thats the next objective.

  <img src="https://i.imgur.com/RFwsXPq.png" height="80%" width="80%" alt="Malware Analysis Steps"/>
-Step 6: Next, we use the scDbg tool on REmnux which is a shellcode analyzer. Shellcode is small piece of machine code typically used as payload that can exploit vulnerabilities or run certain instructions to do a certain task. On the scDbg GUI we search for and select our object.bin ole file we want to analyze. We then click the "create dump" option box to output whatever it found to the machin and also click the "find sc" option box to search/find any shellcode. When we click launch, the tool finds 7 entry points that have a "GetProcAddress" function. Thhis function fetches an exported funtion or variable from a dynamic linked library (DLL) and proceeds its to its tasks by writing to and embedding files.

<img src="https://i.imgur.com/R4SKR8i.png" height="40%" width="40%" alt="Malware Analysis Steps"/> <img src="https://i.imgur.com/iDO8BbX.png" height="40%" width="40%" alt="Malware Analysis Steps"/>

-Step 7: We have now selected one of the GetProcAddress entries of shellcode; outputed by the scDbg tool and arrived to some readable information. We can see an executable named "aro.exe" written into the file path of "APPDATA" which should be alarming. The shellcode also intstructs to load a library called "UrlMon" and lastly, to download a malicious file via url straight to file from the internet called "jan2.exe" with a domain of seed-bc.com and put this file into the application data path called "aro.exe". This is very dangerous and reveals the attackers methods.

<img src="https://i.imgur.com/tCbwrBB.png" height="80%" width="80%" alt="Malware Analysis Steps"/>

-Step 8: We look to find the IP address and port information the malware communicates with. We do this by searching up the domain "seed-bc.com" from the url on VirusTotal, an Open-Source Intelligence (OSINT) tool. The url started with "http" so we know that its communicates on port 80 and we found the IP address which is 185.36.74.48. VirusTotal has flagged this malware as dangerous and malicious from multiple recurring entries. We could have initially ran the first hash on VirusTotal but running a complete intial investigation is safer and more covert so that the attacker is not alarmed by the investigation.

 <img src="https://i.imgur.com/t8tEwN4.png" height="80%" width="80%" alt="Malware Analysis Steps"/>

 -Step 9: Answer all the questions on the LetsDefend site to complete this challange.

 <img src="https://i.imgur.com/tCdGdlB.png" height="40%" width="40%" alt="Malware Analysis Steps"/> <img src="https://i.imgur.com/jvQVIIX.png" height="40%" width="40%" alt="Malware Analysis Steps"/>

Step 10: Challenge Completed!
 <img src="https://i.imgur.com/CJO8Erd.png" height="80%" width="80%" alt="Malware Analysis Steps"/>



