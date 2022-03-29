# dDNS
dDNS is a PyPI package for periodically activating dynamicDNS in freedns.afraid.org.

You need to have an account on freedns.afraid.org and choose dynamic domain names:
https://freedns.afraid.org/

# How to activate and deactivate Python2.7 under Python3.8
<pre>
To activate python2.7
conda create --name py2 python=2.7
conda activate py2

To deactivate:
conda deactivate
</pre>

# How to prepare for dDNS
To use this PyPI dDNS, you need to prepare for .freedns directory and two files: crypted and key.
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
4. Change to the key file that only you can read.
$ chmod 700 key
5. Encrypt freedns.info to crypted file
$ openssl enc -e -aes256 -pbkdf2 -in freedns.info -out crypted -k `cat key` 
6. ".freedns" directory has two files: crypted and key
</pre>

# How to install dDNS
$ pip install dDNS

# How to run dDNS
$ dDNS

# crontab
You should type the following command to set crontab schedule:

$ crontab -e

The following shows an example in crontab scheduler to run dDNS every 9 minutes.

*/9 * * * * dDNS >/dev/null
