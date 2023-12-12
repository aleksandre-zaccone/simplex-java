# **ZSH Shell Configuration**

I've created this tutorial to demonstrate how I use my Arch laptop for everyday work and to share 
my configuration with others. This guide will help you set up and optimize your shell environment 
for increased efficiency on your Ubuntu system. You'll learn how to install and configure Zsh, 
Oh-My-Zsh, and the Powerlevel10k theme. These tools will greatly enhance your command-line experience 
and streamline your everyday work.

## **What is Zsh?**

`Zsh`, short for Z Shell, is a powerful and highly customizable Unix shell that can be used as an interactive login shell and as a powerful scripting language. It offers numerous features, including improved tab completion, better scripting capabilities, and a wide range of plugins and themes to enhance your terminal experience.

## **What is Oh-My-Zsh?**

`Oh-My-Zsh` is an open-source framework for managing your Zsh configuration. It comes with a wide variety of themes, plugins, and features designed to make your command-line interface more productive and enjoyable. Oh-My-Zsh simplifies the process of customizing Zsh and provides an easy way to add plugins and themes.

Web Site - <https://ohmyz.sh/>


## **What is Powerlevel10k?**

`Powerlevel10k` is a highly customizable Zsh theme designed to work seamlessly with Oh-My-Zsh. 
It's known for its flexibility, speed, and eye-catching prompts. Powerlevel10k is feature-rich and 
offers various prompt styles, colors, and a configuration wizard that allows you to customize your 
terminal appearance to suit your preferences.

GitHub - <https://github.com/romkatv/powerlevel10k>

# **Installation and Configuration**

1. check current shell  version
```zsh
echo $SHELL
```

2. install ZSH
```zsh
sudo pacman -Syu
sudo pacman -S zsh
```

3. switch default shell from bash to zsh, then logout and log in
```zsh
chsh -s $(which zsh)
```


4. check current shell  version
```zsh
echo $SHELL
```

5. install oh-my-zsh via curl
```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```


6. install Nerd Font -  https://www.nerdfonts.com/


7. add Nerd Font in Konsole 


8. install powerlevel10k
```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```


9. set `ZSH_THEME="powerlevel10k/powerlevel10k"` in `~/.zshrc`.


10. run powerlevel10k configuration wizard
```bash
p10k configure
```

11. add zsh-syntax-highlighting plugin
```bash
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

12. add 'zsh-syntax-highlighting' in '.zshrc' file in PLUGINS


13. add zsh-autosuggestions
```bash
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

14. add 'zsh-autosuggestions' in '.zshrc'


