dotfiles
========

install NeoBundle and lua enabled vim

```shellscript:install.sh
# install dotfiles
cd ~
curl https://raw.githubusercontent.com/Shougo/neobundle.vim/master/bin/install.sh | sh
git clone https://github.com/eka2513/dotfiles.git dotfiles
pushd /usr/local/src


# install enable-luainterp vim
sudo yum install ncurses-devel lua-devel perl-ExtUtils-Embed
wget ftp://ftp.vim.org/pub/vim/unix/vim-7.4.tar.bz2 -O - | tar xjf -
pushd vim74
./configure \
 --enable-multibyte \
 --with-features=huge \
 --enable-luainterp \
 --enable-perlinterp \
 --enable-pythoninterp \
 --with-python-config-dir=/usr/lib64/python2.6/config \
 --enable-rubyinterp \
 --with-ruby-command=/usr/bin/ruby
make && sudo make install
echo 'alias vi='/usr/local/bin/vim' >> ~/.bashrc
echo 'alias vim='/usr/local/bin/vim' >> ~/.bashrc
. ~/.bashrc
popd


# NeoBundle Setting
/usr/local/bin/vim
# type Y
# some error occurs
pushd ~/.vim/bundle/vimproc/ && make && popd

```
