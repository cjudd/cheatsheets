# SSH Cheatsheet

## Resources
* SSH Trouble shooting - https://gitolite.com/gitolite/sts

## SSH single sign-on
```
ssh-add ~/.ssh/id_rsa
```

## SSH to server using key
```
ssh -i ~/.ssh/<keyname> <user>@<server>
```
## secure copy 
To server:
```
scp -i ~/.ssh/<keyname> <file> <user>@<server>:<path>
```
From server:
```
scp -i ~/.ssh/<keyname> <user>@<server>:<path> <file>
```

## finger print AWS key
```
openssl pkcs8 -in ~/.ssh/key.pem -nocrypt -topk8 -outform DER | openssl sha1 -c
```

## password less login
```
mkdir -p ~/.ssh
cd ~/.ssh
ssh-keygen -t rsa -b 4096 [-f <keyname>]
```

## authorize keys
```
cat <keyname>.pub >> ~/.ssh/authorized_keys
chmod 600 ~/.ssh/authorized_keys
```