# Passwordless Login to CSIF
Setup passwordless login to CSIF using SSH Key Authentication and SSH Config. 

Outcome: 
- Be able to connect to CSIF by simply using command `ssh csif`

What you need:
- [VS Code](https://code.visualstudio.com/)
- VS Code Extension **Remote - SSH**

### For Windows

- Open **Windows Powershell**
- Run command `ssh-keygen`
  - You don't need to (of course you can) change the default location or set a password for the key, so press enter directly when you see any prompts
  - This command generates a pair of public and private key used in SSH Key Authentication
- Run command `cat ~/.ssh/id_rsa.pub | ssh username@pcXX.cs.ucdavis.edu "cat >> ~/.ssh/authorized_keys"`
  - You need to replace `username` and `XX` in the command
  - This command uploads the public key you just generated to a CSIF computer
- Open **VS Code** and click the little green button in the bottom-left corner of the window
- Select **Remote-SSH: Open Configuration File...** and choose the first option prompted
- Replace the file content with the following and save it (of course, you need to replace `username` and `XX` too)
    ```
    Host csif
        HostName pcXX.cs.ucdavis.edu
        User username
        IdentityFile ~/.ssh/id_rsa
    ```
- Return to **Windows PowerShell** and run command `ssh csif` to connect to a CSIF computer passwordlessly
  - If you are still prompted for entering a password, your SSH Key Authentication is not set up correctly
  - You can connect to CSIF in this passwordless way on your computer from now on!

### For macOS & Linux

- Open **Terminal**
- Run command `ssh-keygen`
  - You don't need to (of course you can) change the default location or set a password for the key, so press enter directly when you see any prompts
  - This command generates a pair of public and private key used in SSH Key Authentication
- Run command `ssh-copy-id username@pcXX.cs.ucdavis.edu`
  - You need to replace `username` and `XX` in the command
  - This command uploads the public key you just generated to a CSIF computer
- Open **VS Code** and click the little green button in the bottom-left corner of the window
- Select **Remote-SSH: Open Configuration File...** and choose the first option prompted
- Replace the file content with the following and save it (of course, you need to replace `username` and `XX` too)
    ```
    Host csif
        HostName pcXX.cs.ucdavis.edu
        User username
        IdentityFile ~/.ssh/id_rsa
    ```
- Return to **Terminal** and run command `ssh csif` to connect to a CSIF computer passwordlessly
  - If you are still prompted for entering a password, your SSH Key Authentication is not set up correctly
  - You can connect to CSIF in this passwordless way on your computer from now on!

 ## Give some Feedback
- Give a star to this if you enjoy it!
- Open up an issue or pull request to report typos, problems, or anything that can help make this better
- Follow me on GitHub!
