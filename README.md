# Use Remote AITom Service via Visual Studio Code

## Install AITom on your Server

### GENERAL STEPS...

The server should be Linux based.

## Install SSH Extensions on Visual Studio Code

- This extension strongly recommends using key-based authentication (if you use a username/password, you'll be prompted to enter your credentials more than once by the extension)[[*](https://code.visualstudio.com/docs/remote/ssh-tutorial)];

- It does not support X11 Forwarding when using username/password authentication.

- Before connecting to your server, you may want to generate your own SSH key pairs and add your key to the server.

### Windows 10

- Search and install the following extensions:
  - [Remote - SSH](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-ssh)  
    - Extension ID:  `ms-vscode-remote.remote-ssh` 
  - [Remote - SSH: Editing Configuration Files](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-ssh-edit) 
    - Extension ID:  `ms-vscode-remote.remote-ssh-edit` 
- Please also check out the **Remote - SSH** tutorial: [Remote development over SSH](https://code.visualstudio.com/docs/remote/ssh-tutorial) 
- Make sure you enable OpenSSH service on your windows machine.

### Linux Distributions: Ubuntu 20.04

PLACEHOLDER

### MacOS X

PLACERHOLDER

## Install X Server Client

Make sure your remote server has X server running.

### Windows 10

- Install any Windows X Server e.g. [Xming](https://sourceforge.net/projects/xming/), [Cygwin](https://x.cygwin.com/), we use and recommend [VcXsrv Windows X Server](https://sourceforge.net/projects/vcxsrv/).

### Linux Distributions: Ubuntu 20.04

~~PLACEHOLDER~~ 

### MacOS X

~~PLACEHOLDER~~ 

## Configure Remote - SSH X11 Forwarding

- Edit your `settings.json`, put the following configuration to the head of the settings. This makes your VS Code terminal capable of forwarding the X11 window to your local client.

  ```json
  {
  "terminal.integrated.env.windows": {
          "DISPLAY":"localhost:0.0"
      },
      ... ...
  }
  ```

### <a name="startxsrv"></a> Start Windows X Server

- Start your [VcXsrv Windows X Server](https://sourceforge.net/projects/vcxsrv/).
  - Select your preferred display settings, click *Next*.
  - Select start no client, click *Next*.
  - Click *Next* and click *Finish*, you should be all set.

## Configure and Connect to your Host Server

1. Follow the instructions on the **Remote - SSH** tutorial: [Remote development over SSH](https://code.visualstudio.com/docs/remote/ssh-tutorial) 
2. Tips:
   - When you bring up the list of Remote extension commands, remember to put -X or -Y parameters in order to connect to the remote X server. e.g. `ssh -Y -p 22 aitom@scs.cmu.edu` 
   - Please also check your SSH `config` file, make sure it has `ForwardX11 yes` or `ForwardX11Trusted yes` options enabled.
3. In VS Code terminal, after connected to the host, enter `xclock` command to validate if you set up all the steps correctly.

## Configure Remote Python Interpreter

- To set up your remote python interpreter, please refer to [Using Python environments in VS Code](https://code.visualstudio.com/docs/python/environments).

## Workflow

### Windows 10

1. [Start Windows X Server](#startxsrv) 
2. Open VS Code and connect to your host.

### Linux Distributions: Ubuntu

PLACEHOLDER

### MacOS

PLACEHOLDER
