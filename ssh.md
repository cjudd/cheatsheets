# SSH Cheatsheet

## ssh to serve using key key
```
ssh -i ~/.ssh/<keyname> <user>@<server>
```
## secure copy 
```
scp -i ~/.ssh/<keyname> <file> <user>@<server>:<path>
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