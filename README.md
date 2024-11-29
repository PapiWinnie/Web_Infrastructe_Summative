# Web_Infrastructe_Summative

PART 1: HOW TO DEPLOY

How to Deploy

<!-- 1st Determining the path of my project -->

~/Web_Infrastructure_Summative/Web_Infrastructe_Summative/Dictionary_App/


<!-- Runnning the scp command to transfer project files to the server -->

scp -i ~/.ssh/id_rsa -r ~/Web_Infrastructure_Summative/Web_Infrastructe_Summative/Dictionary_App/* ubuntu@52.91.95.193:/var/www/html/


<!-- Verifying the Transfer on the Server -->

step 1: ssh -i ~/.ssh/id_rsa ubuntu@52.91.95.193

<!-- Once inside the server -->

step 2: ls/var/www/html/

<!-- You should see index.html, app.js, style.css -->

<!-- Repeat this for the the second server and the load balancer (web-02 and lb-01) -->

<!-- Incase Permission denies when using scp/ transferring files -->

Step 1: Check Permision on server:
ssh -i ~/.ssh/id_rsa ubuntu@52.91.95.193

step 2: Check Directory Perission:
ls -ld /var/www/html

if this is returned: 
drwxr-xr-x 2 root root 4096 Nov 9 18:52 /var/www/html/

Step 3: Change Permission to ubuntu
sudo chown -R ubuntu:ubuntu /var/www/html/

step 4: exit

step 5: Retry scp line and it should work
scp -i ~/.ssh/id_rsa -r ~/Web_Infrastructure_Summative/Web_Infrastructe_Summative/Dictionary_App/* ubuntu@<Your Server>:/var/www/html/


PART 2: CREDIT

API link: https://dictionaryapi.dev/
Provider: Free Dictionary API
GitHub: https://github.com/meetDeveloper/freeDictionaryAPI


PART 3: Challenge and how I overcame it.

My main challenge was avoiding the code from displaying duplicate entries. In terms of, if a part of speech was returned, and it had a collection fo similar part of speeches, for example, noun noun and noun, there will be no need for me to display noun three times. 

I was able to solve this duplicate problem by using the Set method. Using a Set here was ideal because it prevented duplicates. 

So if a partOfSpeech was already in the Set, it won't add it to the Set, but if it wasn't, then it'll get added to the Set, then it would be rendered to the DOM. 
