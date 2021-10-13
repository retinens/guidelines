# New ubuntu machine 20.04

## Install the base packages

```shell
sudo apt install -y git git-flow curl zsh network-manager libnss3-tools jq xsel software-properties-common
```

## Install Github CLI

```shell
curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo gpg --dearmor -o /usr/share/keyrings/githubcli-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null
sudo apt update
sudo apt install gh
```
Follow the auth process and select the SSH auth method.


## Install Oh My ZSH

```shell
 sh -c "$(wget https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"
```

## Install PHP & composer

```shell
sudo add-apt-repository ppa:ondrej/php
sudo apt install php-cli php-common php-curl php-mbstring php-opcache php-readline php-xml php-zip php-mysql php-gd
```
```shell
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('sha384', 'composer-setup.php') === '906a84df04cea2aa72f40b5f787e49f22d4c2f19492ac310e8cba5b96ac8b64115ac402c8cd292b8a03482574915d1a8') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
php composer-setup.php
php -r "unlink('composer-setup.php');"
sudo mv composer.phar /usr/local/bin/composer
```

## Install MySQL

```shell
sudo apt-get -y install mysql-server
sudo mysql_secure_installation
sudo mysql
```
In MySQL, edit the auth method for the root user
```mysql
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'root';
FLUSH PRIVILEGES;
EXIT;
```

## Install Valet Plus

```shell
composer global require genesisweb/valet-linux-plus
```

Add this at the start of the `.zshrc` file
```
PATH="$PATH:$HOME/.config/composer/vendor/bin"
```

```shell
valet install
cd ~ && mkdir Sites && cd Sites && valet park
```

Clone the laravel-scripts package
```shell
gh repo clone retinens/laravel-scripts
```

## Install NPM

```shell
cd ~
curl -sL https://deb.nodesource.com/setup_16.x -o nodesource_setup.sh
sudo bash nodesource_setup.sh
sudo apt install nodejs
```

## Setup your ssh keys
```shell
#todo
```

## Install JetBrains Toolbox and install PHP
```shell
curl -fsSL https://raw.githubusercontent.com/nagygergo/jetbrains-toolbox-install/master/jetbrains-toolbox.sh | bash
jetbrains-toolbox
```

## Install GIMP
```shell
sudo apt install snapd
sudo snap install gimp
```

## Install Google Chrome
```shell
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo dpkg -i google-chrome-stable_current_amd64.deb
```

## Install Slack
```shell
sudo snap install slack --classic
```

## Manually install these 

* [MySQL workbench](https://dev.mysql.com/downloads/workbench/)
