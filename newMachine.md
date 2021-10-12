# New ubuntu machine 20.04

## Base packages

```
sudo apt install -y git curl zsh network-manager libnss3-tools jq xsel software-properties-common
```

## Install Oh My ZSH

```
 sh -c "$(wget https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"
```

## Install PHP & composer

```
sudo add-apt-repository ppa:ondrej/php
sudo apt install php-cli php-common php-curl php-mbstring php-opcache php-readline php-xml php-zip php-mysql php-gd
```
```
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('sha384', 'composer-setup.php') === '906a84df04cea2aa72f40b5f787e49f22d4c2f19492ac310e8cba5b96ac8b64115ac402c8cd292b8a03482574915d1a8') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
php composer-setup.php
php -r "unlink('composer-setup.php');"
sudo mv composer.phar /usr/local/bin/composer
```

## Install MySQL

```
sudo apt-get -y install mysql-server
sudo mysql_secure_installation
sudo mysql
```
```
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'root';
FLUSH PRIVILEGES;
exit;
```

## Install Valet Plus

```
composer global require genesisweb/valet-linux-plus
```

Add this to the `.zshrc` file
```
PATH="$PATH:$HOME/.config/composer/vendor/bin"
```

```
valet install
mkdir Sites
cd Sites
valet park
```

## Install Github CLI 

```
curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo gpg --dearmor -o /usr/share/keyrings/githubcli-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null
sudo apt update
sudo apt install gh
```

Follow the auth process and select the SSH auth method.

Install : 
Chrome
Npm
Phpstorm
GIMP
Slack
GitHub cli
Laravel scripts repo
SSH keys

MySQL workbench
