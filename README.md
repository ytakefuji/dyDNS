# dDNS
dDNS is a PyPI package for periodically activating dynamicDNS in freedns.afraid.org.

To use this PyPI dDNS, you need to execute the followings: 
<pre>
1.You must create .freedns directory.
$ mkdir .freedns
$ cd .freedns
2.In .freedns directory, you should create a plain authenticiation file: freedns.info.
freedns.info file has three lines (username, password, dynamic domain name).
$ cat freedns.info
USERNAME = "username_freedns.afraid.org"
PASSWORD = "password_freedns.afraid.org"
UPDATE_DOMAINS = ["your_domain_name", ] 
3. Create a plain file of encryption key for openssl.
$ cat key
your_key 
4. Encrypt freedns.info.
$ openssl enc -e -aes256 -pbkdf2 -in freedns.info -out crypted -k `cat key` 



$ openssl enc -d -aes256 -pbkdf2 -in freedns.info .freedns/crypted -out result

