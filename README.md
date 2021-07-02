# Provisions

This repository is a personal note to me if I ever get a new device in order to make the shifting process as swift as possible. In order to separate the concerns between personal use and development, please do not use the same device for work and personal matters (my personal preference is Windows machines for personal use and Unix systems for software engineering).

The provisioning process is automated using [Ansible](https://www.ansible.com/), an Infrastructure-as-Code.

## Notes

Some notes to keep in mind before provisioning your device.

- Make sure you get a PC with Intel processors. Homebrew (for Linux) does not support ARM processors.
- You can ignore the above if you are provisioning a Raspberry Pi device.
- You have to use either Darwin-based Linux, Ubuntu-based Linux, or a Debian-based Raspberry Pi.
- I am a 'minimalist' developer. I don't really have any personal configurations other than the synchronized one in Visual Studio Code. I am content with factory settings.
- I write how I provision both Windows and Unix systems here so I don't forget anything.

## Preparations

Before starting to automatically configure stuff, we have to configure our machine manually first.

For Windows:

- Take care of Windows Updates and Drivers first to prevent any unwanted happenings.
- Log in to Microsoft Account, link it to the device, setup synchronizations (settings, accounts).

For MacOS:

- Take care of Apple Updates.
- Log in to iCloud. Setup synchronizations and settings.

For Ubuntu/Linux:

- Update software using `apt`.

## Setup - Windows

My personal preference is that I will try to avoid programming in Windows for separation of concerns between my personal life and my development life. Windows machines are simple and I don't think the process could get any more straightforward than it is already. I usually provision my Windows devices like the following steps.

- Install [Google Chrome](https://www.google.com/chrome/).
- Install [Drive Backup and Sync](https://www.google.com/drive/download/) and setup it to guard important folders.
- Install games if I ever feel like playing one. Maybe [Genshin Impact](https://genshin.mihoyo.com/)?
- Install other essential applications, refer to Google Drive for list of essential applications for Windows.

## Setup - MacOS

For my software engineering device (should be MacOS), please follow below steps to get your device provisioned.

- Let's configure Mac's Command Line Tools and configure Homebrew.

```bash
xcode-select --install
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
brew install ansible
brew install git
```

- Setup global configurations for Git. After that is done, generate [SSH key for GitHub](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent). Then, [add it to your GitHub account](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account). Finally, don't forget to test your connection and remember to [verify the RSA fingerprint](https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh/testing-your-ssh-connection).

```bash
git config --global user.email <MY_EMAIL>
git config --global user.name <MY_GITHUB_USERNAME>
ssh -T git@github.com
```

- Clone repository and run Ansible.

```bash
git clone git@github.com:lauslim12/provisions.git
cd provisions
make setup
```

## Setup - WSL / Ubuntu

Just in case I don't work on MacOS, we can also replicate the above on Ubuntu/WSL.

- Let's finish up system updates first.

```bash
sudo apt update
sudo apt upgrade
```

- Configure Homebrew and Git as above.

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
brew install ansible
brew install git
git config --global user.email <MY_EMAIL>
git config --global user.name <MY_GITHUB_USERNAME>
ssh -T git@github.com
```

- Clone repository and run Ansible.

```bash
git clone git@github.com:lauslim12/provisions.git
cd provisions
make setup
```

## Setup - Raspberry Pi

To configure my Raspberry Pi, we don't really need complicated stuff.

- Finish up system updates.

```bash
sudo apt update
sudo apt upgrade
```

- Prepare Ansible and Git.

```bash
sudo apt install ansible
sudo apt install git
git config --global user.email <MY_EMAIL>
git config --global user.name <MY_GITHUB_USERNAME>
ssh -T git@github.com
```

- Clone repository and run Ansible.

```bash
git clone git@github.com:lauslim12/provisions.git
cd provisions
make setup
```

## Update

Updating the packages can be done by typing the following command.

```bash
# for homebrew
make update

# for apt/linux
make update-linux
```

You can use both commands in order to update both package managers!

## Manual Configurations

After you have configured everything in your system, it's time to do some manual works.

Configure MacOS:

- System Preferences -> Trackpad -> Tap to Click
- Battery -> Show Percentage
- Create projects folder: `mkdir Projects` and `ln -s ~/Projects ~/Desktop/Projects`.

Configure Google Chrome:

- Log in to all of Google Accounts.
- Setup Google Synchronization (Contacts, Drive, Calendar, and more).
- Change Privacy and Security to Public DNS.
- Log in to all webservices that I use (StackOverflow, LinkedIn, GitHub, etcetera).

Configure Visual Studio Code:

- Log in to Microsoft Account inside Visual Studio Code to sync all of my extensions and settings.

## Next Steps

- Download all of essential data that might still be used from Google Drive. Keep data backed up and updated!
- Fetch all currently being worked on projects from GitHub. Just a simple `git clone` will suffice.
- Check the repository every so often to update the commands and links (should be highly unlikely).
