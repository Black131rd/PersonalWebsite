# GitHub Deploy Keys
[Tutorial](https://dylancastillo.co/posts/how-to-use-github-deploy-keys.html)
## Create SSH Key on the Server
[Github Docs](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#generating-a-new-ssh-key)
<br>
1. Command
```
ssh-keygen -t ed25519 -C "USERNAME@EMAIL.com"
```

2. Press Enter
3. Enter Passphrase

## Add Deploy Key to Target Repo
1. Settings in Target Repo
2. Deploy Keys
3. Add new
4. Title < >, Public Key < SHA256:adfdasfasfe > (Contents of generated id_ed25519.pub File)

## Add the Key to SSH Config
1. Command
```
touch ~/.ssh/config
chmod 600 ~/.ssh/config
nano ~/.ssh/config
```
2. Contents
```
Host RepoName
    HostName github.com
    AddKeysToAgent yes
    PreferredAuthentications publickey
    IdentityFile ~/.ssh/id_ed25519
```
* Host: the name you’ll use in the terminal when referring to this server. Choose a name that’s easy to remember.
* HostName: the real hostname that you’ll connect to. In this case, github.com.
* AddKeysToAgent: specifies if it should add the private key to the ssh-agent.
* PreferredAuthentications: order in which the client tries authentication methods. In this case, you only use your publickey.
* IdentityFile: specifies a file from which the key is read. You need to specify the name of the private key you generated earlier. If you used the default name, it should be ~/.ssh/id_ed25519.

## Git Clone
```
git clone git@RepoName:Black131rd/PersonalWebsite.git
```
