# howto-bash-pavlovrcon
#how to issue a batch file (list of rcon commands) to a PavlovVR server using netcat

#There is a very brief example on the pavlov wiki 
#http://wiki.pavlov-vr.com/index.php?title=Dedicated_server

#but it was not very detailed so here is how to do it. also i am very new to all this so if i could do something better please let me know 

#First be aware that connecting and disconnecting a lot can hurt server preformance  

#first you need to make a bash script 

<p>
nano test.sh 
</p>
<hr>
<p>

#!/bin/bash
function slowcat(){ while read; do sleep .15; echo "$REPLY"; done; }
cat  $1 | slowcat | nc {SERVER IP} {SERVER PORT}
<hr>
<br>
</p>
#do sleep .15 is how you can set the delay 

#now exit and save the test.sh 
<hr>
<p>
nano batch
</p>
<p>
  {RCON PASSWORD CONVERTED TO MD5 HASH}
  ResetSnd
  {RCON CMD}
  Disconnect
</p>

# here the first line has to be the rcon password converted to MD5 HASH
# https://www.md5hashgenerator.com/
# then each line after that u can use any rcon commands
# the last line must be disconnect 

 

