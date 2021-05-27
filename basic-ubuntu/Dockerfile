FROM ubuntu:latest

RUN apt update -y
RUN apt upgrade -y
RUN apt install git -y

RUN git config --global user.name "Ryuku-Hisa" && \
    git config --global user.email "b1018015@fun.ac.jp"

RUN cd ~/ && git clone https://github.com/Ryuku-Hisa/bashrc.git
RUN mv ~/bashrc/.bash_profile ~/ && mv ~/bashrc/.bashrc ~/
RUN rm -rf ~/bashrc 

RUN cd ~/ && git clone https://github.com/Ryuku-Hisa/vimrc.git 
RUN mv ~/vimrc/vimrc ~/.vimrc
RUN rm -r ~/vimrc

RUN mkdir ~/.vim
RUN cd ~/.vim && git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
RUN mkdir ~/.vim/colors
RUN cd ~/.vim/ && git clone https://github.com/tomasr/molokai
RUN mv ~/.vim/molokai/colors/molokai.vim ~/.vim/colors/
RUN rm -rf molokai 

RUN echo 'set bell-style none' >> /etc/inputrc

RUN dircolors -p > ~/.dircolors
RUN \
sed -e \
's/OTHER_WRITABLE 34;42 # dir that is other-writable (o+w) and not sticky/OTHER_WRITABLE 01;34 # dir that is other-writable (o+w) and not sticky/g' \
~/.dircolors > ~/.new_dircolors
RUN mv ~/.new_dircolors ~/.dircolors
