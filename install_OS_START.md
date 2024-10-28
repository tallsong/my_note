```bash


export http_proxy='http://mac.local:1082'    
export https_proxy='https://mac.local:1082'

cd /home/cedar/Downloads
sudo apt update
sudo apt install openssh-server vim zsh  git  zsh htop -y
sudo systemctl enable ssh
sudo systemctl restart ssh
sudo systemctl status ssh

git config --global   https.proxy https://mac.local:1082 
git config --global   http.proxy http://mac.local:1082




sh -c "$(wget https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"


git clone --depth=1 https://github.com/amix/vimrc.git ~/.vim_runtime
sh ~/.vim_runtime/install_basic_vimrc.sh

git config --global --unset http.proxy
git config --global --unset https.proxy


sudo apt-get install fonts-powerline

```