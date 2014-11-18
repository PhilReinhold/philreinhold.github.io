---
layout: post
title: Setting up OS X from Scratch
---
I'm a fan of *tabula rasa*, and a fan of automation. Here's setting up OSX from
scratch in the form of a small shell script

First, install xcode from the app store. This doesn't seem to be automatable
Then, get the command line tools

{% highlight bash %}
xcode-select --install
xcodebuild -license
{% endhighlight %}

Install [homebrew](http://brew.sh)

{% highlight bash %}
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
{% endhighlight %}

Install some packages from homebrew

{% highlight bash %}
brew update
brew tap homebrew/science
packages=(
    git
    hub
    ack
    tree
    python
    qt
    hdf5
    pyqt
    tmux
    zsh
    vim
    llvm
)

brew install ${packages[@]}
brew cleanup
{% endhighlight %}

Install some apps from [brew cask](http://caskroom.io)

{% highlight bash %}
brew install caskroom/cask/brew-cask
apps=(
    google-chrome
    google-drive
    iterm2
    bettertouchtool
    flash
    flux
    caffeine
    karabiner
    seil
    mactex
    latexit
    papers
    steam
)
brew cask install --appdir="/Applications" ${packages[@]}
{% endhighlight %}

Install python packages with [pip](https://pip.readthedocs.org)

{% highlight bash %}
pip install --upgrade setuptools
pip install --upgrade pip
pypackages=(
    numpy
    scipy
    matplotlib
    ipython
    sympy
    qutip
    pyqtgraph
    pyzmq
    h5py
    gdsCAD
    Pint
)
pip install ${pypackages[@]}
{% endhighlight %}

Get git config and start adding repositories

{% highlight bash %}
curl -f https://raw.githubusercontent.com/PhilReinhold/dotfiles/master/gitconfig > .gitconfig
mkdir ~/code
cd ~/code
git clone PhilReinhold/dotfiles
git clone PhilReinhold/liveplot
git clone PhilReinhold/qutip_explorer
git clone PhilReinhold/H5Explorer
git clone PhilReinhold/qpropertytree
git clone PhilReinhold/gui_builder
git clone PhilReinhold/vectfit_python
cd ~
{% endhighlight %}

Link dotfiles to the appropriate locations

{% highlight bash %}
rm .gitconfig
ln -s code/dotfiles/gitconfig .gitconfig
ln -s code/dotfiles/profile .profile
ln -s code/dotfiles/vimrc .vimrc
ln -s code/dotfiles/zshrc .zshrc
ln -s code/dotfiles/tmux.conf .tmux.conf
{% endhighlight %}

Tell vim to install packages from [vundle](http://github.com/gmarik/vundle.vim)

{% highlight bash %}
mkdir -p .vim/bundle
git clone gmarik/Vundle.vim .vim/bundle
vim +BundleInstall +q
{% endhighlight %}

Set up shell with [antigen](http://github.com/zsh-users/antigen)

{% highlight bash %}
git clone zsh-users/antigen .antigen
sudo chsh -s /bin/zsh phil
{% endhighlight %}
