# How can I push/pull code to/from remote github repo

1. Create github account
2. Create a secret key  on your laptop so you dont have to login and put password when pushing code

```
ssh-keygen -t ed25519 -C "your_email_address"
```
Mostly confirm by pressing enter
```
cat id_ed25519_nsc.pub
```
-> put this output to your github account (https://github.com/settings/keys)
```
e.g. ssh-ed25519 AAAAC3NzaC...your@email.com
```

# Checks if you are correctly connected to git
```
ssh -T git@github.com
```


# Create a repo
- create a repo on github
- create a folder with the same name on your laptop

```
git remote add origin https://github.com/YOUR_ACCOUNT/cas-so101-jetson.git
```