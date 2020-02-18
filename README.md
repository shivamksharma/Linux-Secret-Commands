# LINUX SECRET COMMANDS 

# BELOW ARE THE SOME OF THE SIMPLE AND ADVANCED COMMAND THAT YOU CAN TRY ON YOU LINUX SYSTEM





# GET WIFI PASSWORD
  >" cat /etc/NetworkManager/system-connections/[SSID] | grep psk= "
  
# LIST NETWORK INTERFACES
  >lspci | egrep -i --color 'network|ethernet'
  
# GET YOUR FIREFOX HISTORY 
  >sqlite3 ~/.mozilla/firefox/*.[dD]efault/places.sqlite "SELECT strftime('%d.%m.%Y %H:%M:%5',visit_date/1000000, 'unixepoch'.'localtime'),url FROM moz_places,moz_historyvisits WHERE moz_places.id=moz_historyvisits.places_id ORDER BY visit_date;"

# CHECK ALL BASH SCRIPTS IN CURRENT DIR FOR SYSTAX ERRORS
  >find . -name '*sh' -exer bash -n {} \;
 
# LIST DIRECTORIES ONLY
  >ls -d */

# WATCH YOUR NETWORK SERVICE ACTIVITY IN REAL-TIME
  >lsof -i
  
# ESCAPE ANY COMMAND ALIASES
  >/[command]

# KILLS A PROCESS THAT IS LOCKING A FILE
  > fuser -k [filename]

# FINF THE DUPLICATE FILES BASED ON SIZE FIRST, THEN MD5 HASH
  >find -not -empty =type f -printf "%s\n" | sort -rn | uniq -d | xargs - I{} -n1 find -type f -size {}c -print0 | xargs -0 md5sum | sort | uniq -w32 -all-repeated-separate
 
# ACCESS GOOGLE TRANSLATE IN TERMINAL
  > translate(){ wget -q0- "https://ajax.googleapis.com/ajax/servces/language/translate?v=1.0&q=$1&langpair=$2|${3:-en}" | sed 's/.*trasnlatedText":"\([^"]*\)".*}/\1\n/';}
  
# LIST OF RECENT COMMANDS
 > history
 
# CLOSE A FROZEN WINDOW/APPLICATION PACKAGE
 > xkill
 
# LIST ALL BASH SHORTCUTS
 > bind -P
 
# CREATE A QUICK BACK-UP COPY OF A FILE 
 > cp file.txt{,.bak}
 
# TO PRINT A SPECIFIC LINE FROM A FILE
 > sed -n 5p <file>
  
# EDIT GOOGLE DOC WITH VIM
 > google docs edit --title "To-Do list" --editor vim
 
# NICE WHEATHER FORECAST ON YOUR SHELL
 > curl wttr.in/seville

# DOWNLOAD YOUTUBE VIDEO WITH WGET
 > wget http://www.youtube.com/watch?v=dQw4w9WgXcQ -qO- | sed -n "/fmt_url_map/{s/[\'\"\|]/\n/g;p}" | sed -n '/^fmt_url_map/,/videoplayback/p' | sed -e :a -e '$q;N;5,$D;ba' | tr -d '\n' | sed -e 's/\(.*\),\(.\)\{1,3\}/\1/' | wget -i - -O surprise.flv 
 CONDITIONS - YOU'VE TO PUT YOUTUBE VIDEO LINK IN THE LINK AREA AND SET THE FILE NAME THAT YOU WANT TO SAVE IT.
 
# BINARY CLOCK
 > watch -n 1 'echo "obase=2;`date +%s`" | bc'
 
# DOWNLOAD ALL IMAGES FROM A PERTICULAR SITE
 > wget -r -l1 --no-parent -nH -nd -P/tmp -A".gif,.jpg" http://example.com/images
 CONDITIONS - YOU'VE TO PUT YOUR SITE NAME IN LINK SECTION
 
# CONVERT YOUTUBE VIDEOS TO MP3
 > youtube-dl -t --extract-audio --audio-format mp3 http://www.youtube.com/watch?v=dQw4w9WgXcQ
 CONDITIONS - YOU'VE TO PUT YOUR YOUTUBE VIDEO LINK IN THE LINK SECTIONS
 
# QUICK ACCESS TO ASCII CODE OF A KEY
 > showkey -a
