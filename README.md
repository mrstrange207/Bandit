OverTheWire BANDIT Writeup

Level 0 
Dual booted with ubuntu
Installed ssh and enabled it 
Then used ssh command to connect with bandit 
ssh bandit0@bandit.labs.overthewire.org -p 2220

Level 0 to level 1 
Used cat to display password in content of readme 
cat readme
Logged in into bandit1 using ssh command again using password in readme 

Level 1 to level 2
Googled about dash command
Used cat ./- (specifying full location) to display the content in file - or can use < ( converts to string)

Level 2 to level 3
Used / (skips the spaces in file ) before every space in file name after searching about it on google 
Or use “” (warapping it together)

Level 3 to level 4
Used ls to list directories 
Then changed current directory to inhere
Viewed the hidden file in inhere using -a(used to see all present files even hidden) command
ls
cd inhere 
ls -a
cat .hidden

Level 4 to level 5
 
Found file type using file(used to display file type )./*(* all file)
Found ascii text file
Used Cat ./-file07 for showing password

Level 5 to level 6
Changed current directory to inhere
Used find -size 1033c to find file
Changed to directory maybehere07
Used find -size 1033c ! -executable
Used file command to find file type 
By above 2 statement confirmed all 3 conditions


Level 6 to level 7
Googled for how to search in whole server 
Used find /(searches from the whole server) -size 33c -user bandit7 group bandit6
Used cat /var/lib/dpkg/info/bandit7.password

Level 7 to level 8
Used grep command ( searches a particular pattern and displays the line its found in)
grep ‘millionth’ data.txt

Level 8 to level 9
Learned about piping ( giving output of one command as input of other
Tired cat data.txt| uniq -c but failed as got to know uniq only search for unique  adjacent  to it
Hence used sort for finding it as it sorts out and we can find count 1
Sort data.txt | uniq -c

Level 9 to level 10
Used strings to find human readable strings in binary file
Strings data.txt | grep ‘=’

Level 10 to level 11
Searched on google about base64 
Decoded the file using base64 -d(decode) data.txt

Level 11 to level 12
Learned about rot13 through link given on level 11 to level 12 page
Used tr to translate that is rotate by rot13 logic 
Cat data.txt | tr ‘A-Za-z’ ‘N-ZA-Mn-za-m’
  
Level 12 to 13
Used cat command to enter the password but it was not in readable format
Made directory pra123 using mkdir
Copy data using cp command
Used file command to check the data type in file
Used xxd -r data.txt file1 to convert it to binary 
Used file and got to know its gzip compressed 
Used mv file1 file1.gz as extension is mandatory to decompress
Used gzip -d file.gz to decompress
Used file file1 to see data type and got bzip2
Used mv file1 file1.bz2 as extension is mandatory to decompress
Used bzip2 -d file.bz2 to decompress
Used file to know we got gzip again repeated the previous process
Used file and got posix tar archive 
Used tar -xvf file3
Repeated the same process till we got data8.bin
When decompressed it gave ascii text file 
Used cat and got password

Level 13 to 14
Used ls 
Used ssh -i(identity file) sshkey.private(private key) bandit14@localhost -p 2220 ( took reference from internet)
Used cat and got password

Level 14 to 15
Used telnet (network protocol sends in plain text) localhost 30000
Entered the password

Level 15 to 16
Used openssl (designed to transfer information) s_client -connect localhost:30001 -ign_eof (keeps connection open to read response)
Entered the password
