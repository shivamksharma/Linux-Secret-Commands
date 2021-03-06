# **LINUX SECRET/ADVANCED COMMANDS** 

## SOME OF THE SIMPLE AND ADVANCED COMMAND THAT YOU CAN TRY YOURSELF IN YOU LINUX/UNIX DISTRIBUTIONS



- **GET YOUR WIFI PASSWORD**
```bash
  " cat /etc/NetworkManager/system-connections/[SSID] | grep psk= "
```
  
- **LIST NETWORK INTERFACES**
```bash
  lspci | egrep -i --color 'network|ethernet'
```
  
- **GET YOUR FIREFOX HISTORY** 
 ```bash
  sqlite3 ~/.mozilla/firefox/*.[dD]efault/places.sqlite "SELECT strftime('%d.%m.%Y %H:%M:%5',visit_date/1000000, 'unixepoch'.'localtime'),url FROM moz_places,moz_historyvisits WHERE moz_places.id=moz_historyvisits.places_id ORDER BY visit_date;"
```

- **CHECK ALL BASH SCRIPTS IN CURRENT DIR FOR SYSTAX ERRORS**
```bash
  find . -name '*sh' -exer bash -n {} \;
```  
 
- **LIST DIRECTORIES ONLY**
```bash
  ls -d */
```

- **WATCH YOUR NETWORK SERVICE ACTIVITY IN REAL-TIME**
```bash
  lsof -i
```
  
- **ESCAPE ANY COMMAND ALIASES**
```bash
  /[command]
```

- **KILLS A PROCESS THAT IS LOCKING A FILE**
```bash
  fuser -k [filename]
```

- **FIND THE DUPLICATE FILES BASED ON SIZE FIRST, THEN MD5 HASH**
```bash
  find -not -empty =type f -printf "%s\n" | sort -rn | uniq -d | xargs - I{} -n1 find -type f -size {}c -print0 | xargs -0 md5sum | sort | uniq -w32 -all-repeated-separate
```
 
- **ACCESS GOOGLE TRANSLATE IN TERMINAL**
```bash
  translate(){ wget -q0- "https://ajax.googleapis.com/ajax/servces/language/translate?v=1.0&q=$1&langpair=$2|${3:-en}" | sed 's/.*trasnlatedText":"\([^"]*\)".*}/\1\n/';}
```  
  
- **LIST OF RECENT COMMANDS**
```bash
  history
```  
 
- **CLOSE A FROZEN WINDOW/APPLICATION PACKAGE**
```bash
 xkill
```
 
- **LIST ALL BASH SHORTCUTS**
```bash
 bind -P
```
 
- **CREATE A QUICK BACK-UP COPY OF A FILE** 
```bash
 cp file.txt{,.bak}
```
 
- **TO PRINT A SPECIFIC LINE FROM A FILE**
```bash
 sed -n 5p <file>
```
  
- **EDIT GOOGLE DOC WITH VIM**
```bash
 google docs edit --title "To-Do list" --editor vim
```
 
- **NICE WHEATHER FORECAST ON YOUR SHELL**
```bash
 curl wttr.in/seville
```

- **DOWNLOAD YOUTUBE VIDEO WITH WGET**
```bash
 wget http://www.youtube.com/watch?v=dQw4w9WgXcQ -qO- | sed -n "/fmt_url_map/{s/[\'\"\|]/\n/g;p}" | sed -n '/^fmt_url_map/,/videoplayback/p' | sed -e :a -e '$q;N;5,$D;ba' | tr -d '\n' | sed -e 's/\(.*\),\(.\)\{1,3\}/\1/' | wget -i - -O surprise.flv 
```
>NOTE - YOU'VE TO PUT YOUTUBE VIDEO LINK IN THE LINK AREA & SET THE FILE NAME THAT YOU WANT TO SAVE IT.
 
- **BINARY CLOCK**
```bash
 watch -n 1 'echo "obase=2;`date +%s`" | bc'
```
 
- **DOWNLOAD ALL IMAGES FROM A PERTICULAR SITE**
```bash
 wget -r -l1 --no-parent -nH -nd -P/tmp -A".gif,.jpg" http://example.com/images
```
>NOTE - YOU'VE TO PUT YOUR SITE NAME IN LINK SECTION
 
- **CONVERT YOUTUBE VIDEOS TO MP3**
```bash
 youtube-dl -t --extract-audio --audio-format mp3 http://www.youtube.com/watch?v=dQw4w9WgXcQ
```
>NOTE - YOU'VE TO PUT YOUR YOUTUBE VIDEO LINK IN THE LINK SECTIONS
 
- **QUICK ACCESS TO ASCII CODE OF A KEY**
```bash
 showkey -a
```

- **SHUTDOWN A WINDOWS MACHINE FROM LINUX**
```bash
 net rpc shutdown -I ipAddressOfWindowsPC -U username%password
```

- **DELETE ALL FILES FOUND IN DIRECTORY A FROM DIRECTORY B**
```bash
 for file in <directory A>/*; do rm <directory B>/`basename $file`; done
```
  
- **TERMINAL REDIRECTION**
```bash
 script /dev/null | tee /dev/pts/3
``` 

- **DISPLAY THE ATTEMPTED USERNAME, IP ADDRESS & TIME OF SSH FAILED LOGINS ON DEBIAN MACHINES**
```bash
 awk '/sshd/ && /Failed/ {gsub(/invalid user/,""); printf "%-12s %-16s %s-%s-%s", $9, $11, $1, $2, $3}' /var/log/auth.log
```

- **LAUNCH A COMMAND FROM A MANPAGE**
```bash
 !date
```

- **MATRIX STYLE**
```bash
 echo -e "e[32m"; while :; do for i in {1..16}; do r="$(($RANDOM % 2))"; if [[ $(($RANDOM % 5)) == 1 ]]; then if [[ $(($RANDOM % 4)) == 1 ]]; then v+="e[1m $r   "; else v+="e[2m $r   "; fi; else v+="     "; fi; done; echo -e "$v"; v=""; done
```

- **CREATE A SSH SOCKS PRIXT SERVER ON LOCALHOST:8000 THAT'LL RESTART ITSELF IF SOMETHING BREAKS THE CONNECTION TEMPORARILY**
```bash
 autossh -f -M 20000 -D 8000 somehost -N
```

- **RENAMES MULTIPLE FILES THAT MATCH THE PATTERN**
```bash
 rename 's/foo/bar/g' *
```

- **SHOW DIRETORIES IN THE PATH ONE PER LINE**
```bash
 echo "${PATH//:/$''}"
```

- **RUN THE LAST COMMAND AS ROOT**
```bash
 sudo!!
```

- **MOVE LOTS OF FILES OVER SSH**
```bash
 rsync -az /home/user/test user@sshServer:/tmp/
``` 

- **SERVE CURRENT DIRECTORY TREE AT http://$HOSTNAME:8000/**
```bash
 python -m SimpleHTTPServer
```
 
- **GENERATE A UNIQUE & SECURE PASSWORD FOR EVERY WEBSITE THAT YOU LOGIN TO**
```bash
 sitepass() { echo -n "$@" |  md5sum | sha1sum | sha224sum | sha256sum | sha384sum | sha512sum | gzip - | strings -n 1 | tr -d "[:space:]"  | tr -s '[:print:]' | tr '!-~' 'P-~!-O' | rev | cut -b 2-11; history -d $(($HISTCMD-1)); }
```
 
- **SALVAGE A BORKED TERMINAL**
```bash
 reset
```
 
- **PLAY MUSIC FROM YOUTUBE WITHOUT DOWNLOAD**
```bash
 wget -q -O - `youtube-dl -b -g $url`| ffmpeg -i - -f mp3 -vn -acodec libmp3lame -| mpg123  -
```
 
- **EXECUTED A COMMAND AT A GIVEN TIME**
```bash
 echo "ls -l" | at midnight
```
 
- **QUERY WIKIPEDIA VIA CONSOLE OVER DNS**
```bash
 dig +short txt <keyword>.wp.dg.cx
```
 
- **TYPING THE CURRENT DATE VIA A SHORTCUT AS IF THE KEYS HAS BEEN ACTUALLY TYPED WITH THE HARDWARE KEYBOARD IN ANY APPLICATION**
```bash
 xvkbd -xsendevent -text $(date +%Y%m%d)
```
 
- **MOUNT FOLDER/FILESYSTEM THROUGH SSH**
```bash
 sshfs name@server:/path/to/folder /path/to/mount/point
```
 
- **OUTPUT YOUR MICROPHONE TO A REMOTE COMPUTER'S SPEAKER**
```bash
 dd if=/dev/dsp | ssh -c arcfour -C username@host dd of=/dev/dsp
```
 
- **MAKE ISO IMAGE OF A FOLDER**
```bash
 mkisofs -J -allow-lowercase -R -V "OpenCD8806" -iso-level 4 -o OpenCD.iso ~/OpenCD
```
