# NETWORKING FILES SYSTEM
## Contrbutors
* Sanyam Agrawal
* Ansh Acharya
* Adithya Addepalli Casichetty
* Karthik Venkat Malavathula

## How to run?
* After cloning the repo, go to `/namingserver` and type `gcc main.c -o ns` then `./ns` on your shell to setup naming server.
* Then go to `/storageserver`. By default we have provided list of accessible paths in Root Directory folder inside storageserver
* The list of accessible paths is in `ss<Number>_paths.md` and you can do `./ss<number>` on the shell to run that storage server we have made storage servers 1 to 9 by default
* Then go to `/client` and type `make` then `./a.out` on your shell to set up client.
* After sending the file paths from SS to NS you are ready to go :smiley:.
* Note: Each of these NS,SS AND CLIENT should be performed in different terminals.
* We also support multiple devices but all devices should run on same network (do ifconfig to get ip of Naming Server)
* 
## Assumptions
* The files could be of `.txt`, `.c`, `.h` and `.mp3` format only.
* Across all storage servers, any two files or folder can't have same name.

## Functions we support
READ Request  
FORMAT :  
READ <filepath>  
  
WRITE Request  
FORMAT :  
WRITE <filepath>  
  
CREATE FILE Request  
FORMAT:  
CREATE <path> <filename>  
  
CREATE FOLDER Request  
FORMAT :  
CREATEFOLDER <path> <foldername>  

DELETE FILE OR FOLDER Request  
FORMAT :  
DELETE <path>  
  
COPY FILE/FOLDER Request  
FORMAT :  
COPY <src> <dest>  
  
INFO Request  
FORMAT :  
INFO <path>  
  
LIST Request  
FORMAT :  
LIST  
DESCRIPTION :
Lists all accessible paths which can be accessed at the moment (if a storage server is down as well , they are accessible just under read operation only).

## Naming Server
* On it's initialization, NS creates two threads for registering Storage Servers and for handling incoming client requests.
* For both of the communcations we are using TCP protocol for better reliability.
* NS receives paths of files and directories from the storage server along with the two ports the storage server uses(one for communication with the NS and the other for communication with the client).
* Whenever a client makes a request, NS first searches the cache for the file, and returns the appropriate SS IP and port.
* If the file is not found in the cache, then it searches through the paths received from all the SSs and then sends IP and port number of appropriate SS if the file is found.
* Backup thingie.
 
## Storage Server
* On it's initialization, storage server adds the file paths to the naimg server along with it's IP and port number. 
## Client 
* On it's initialization, storage server adds the file paths to the naimg server along with it's IP and port number.
