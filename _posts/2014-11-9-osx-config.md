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
{% endhighlight %}

Install [homebrew](http://brew.sh)

{% highlight bash %}
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
{% endhighlight %}

Install some packages from homebrew

{% highlight bash %}
brew update
packages=(
    git
    brew-cask
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
)
brew cask install --appdir="/Applications" ${packages[@]}
{% endhighlight %}

Install python packages with [pip](https://pip.readthedocs.org)

{% highlight bash %}
easy_install pip
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

Tell vim to install packages

{% highlight bash %}
vim +BundleInstall +q
{% endhighlight %}

Set up shell

{% highlight bash %}
echo "Name Me!"
sudo chsh /bin/zsh
{% endhighlight %}