# howto-bash-pavlovrcon
#how to issue a batch file (list of rcon commands) to a PavlovVR server using netcat

#There is a very brief example on the pavlov wiki 
#http://wiki.pavlov-vr.com/index.php?title=Dedicated_server

#but it was not very detailed so here is how to do it. also i am very new to all this so if i could do something better please let me know 

#First be aware that connecting and disconnecting a lot can hurt server preformance  

#first you need to make a shell script 

<p>
nano /home/steam/test.sh

</p>
<hr>
<p>

#!/bin/bash<br>
function slowcat(){ while read; do sleep .15; echo "$REPLY"; done; }<br>
cat  $1 | slowcat | nc {SERVER IP} {SERVER PORT}<br>
<hr>
<br>
</p>
#do sleep .15 is how you can set the delay 
#now exit and save the test.sh 

<p>
nano /home/steam/batch
</p>
<hr>
<p>
  {RCON PASSWORD CONVERTED TO MD5 HASH}<br>
  ResetSnd<br>
  {RCON CMD}<br>
  Disconnect<br>
</p>
<hr>
<p>
# here the first line has to be the rcon password converted to MD5 HASH<br>
# https://www.md5hashgenerator.com/<br>
# then each line after that u can use any rcon commands<br>
# the last line must be disconnect <br>
</p>

<p>
# now we need to give the sh permissions to run <br>
sudo chmod +x /home/steam/test.sh
</p>
 
<p>
#now we need to run the bash script <br>
./home/steam/test.sh /home/steam/batch<br>
</p>
<p>
#so to run the script we need to ./ the .sh then after a space we need to pass the batch <br>
</p>
