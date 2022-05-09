#### Babun

- 安装 `pact install tmux`（需管理员权限）


#### MAC OS X

- 安装 `brew install tmux`


#### 启动

- `tmux`
  
- 常用参数
  
  ``` shell
  # 创建session
  tmux
  
  # 创建并指定session名字
  tmux new -s $session_name
  
  # 列出session
  tmux ls
  
  # 进入已存在的session
  tmux a -t $session_name
  
  # 删除指定session
  tmux kill-session -t $session_name
  
  # 删除所有session
  Ctrl+b :kill-server
  
  # 删除session
  Ctrl+b :kill-session
  
  # 临时退出session
  Ctrl+b d
  ```
  


#### 复制/粘贴

- `brew install reattach-to-user-namespace`
- Add to ~/.tmux.conf


``` shell
# getting tmux to copy a buffer to system clipboard
set-option -g default-command "reattach-to-user-namespace -l zsh" # or bash...
bind y run "tmux save-buffer - | reattach-to-user-namespace pbcopy" \; display-message "Copied tmux buffer to system clipboard"
bind C-v run "reattach-to-user-namespace pbpaste | tmux load-buffer - && tmux paste-buffer"
```

- Usage
  
  - copy/selection: `prefix + y` 
  - paste: `ctrl + v`
  


#### 配置Powerline-Shell

- `git clone https://github.com/erikw/tmux-powerline.git`
  
- edit your `~/.tmux.conf` to use the scripts
  
  ``` shell
  set-option -g status on
  set-option -g status-interval 2
  set-option -g status-utf8 on
  set-option -g status-justify "centre"
  set-option -g status-left-length 60
  set-option -g status-right-length 90
  set-option -g status-left "#(~/path/to/tmux-powerline/powerline.sh left)"
  set-option -g status-right "#(~/path/to/tmux-powerline/powerline.sh right)"
  ```
  


#### 自定义配置

``` shell
#-- bindkeys --#
# prefix key (Ctrl+a)
set -g prefix ^a
unbind ^b
bind a send-prefix

# refresh
bind r source-file ~/.tmux.conf \; display "Reloaded!"

# mouse
setw -g mode-mouse on
set -g mouse-select-pane on
set -g mouse-resize-pane on
set -g mouse-select-window on
set -s escape-time 1

# split window
unbind '"'
# vertical split (prefix -)
bind - splitw -v
unbind %
# horizontal split (prefix |)
bind | splitw -h

# panel
bind h select-pane -L
bind j select-pane -D
bind k select-pane -U
bind l select-pane -R

# panel shortcuts
bind -r C-h select-window -t :-
bind -r C-l select-window -t :+

# panel resize
bind -r H resize-pane -L 5
bind -r J resize-pane -D 5
bind -r K resize-pane -U 5
bind -r L resize-pane -R 5

# set default zsh shell
set-option -g default-shell /bin/zsh
```

#### Tmuxinator & Teamocil

- Site <https://github.com/tmuxinator/tmuxinator> <https://github.com/remiprev/teamocil>
  
- Install
  
  ``` shell
  curl https://rubygems.org/downloads/thor-0.19.1.gem
  sudo gem install --local <path/to/thor-0.19.1.gem>
  
  curl https://rubygems.org/downloads/erubis-2.7.0.gem
  sudo gem install --local <path/to/erubis-2.7.0.gem>
  
  curl https://rubygems.org/downloads/tmuxinator-0.6.10.gem
  sudo gem install --local <path/to/tmuxinator-0.6.10.gem>
  
  curl https://rubygems.org/downloads/teamocil-1.2.gem
  sudo gem install --local <path/to/teamocil-1.2.gem>
  ```
  



- Tmuxinator
  
  - Usage
    
    ``` shell
    mux xxx
    ```
    
  - Config
    `mkdir .tmuxinator && cd .tmuxinator`
	
    ``` yaml
    name: simptab
    root: ~/
    windows:
      - project:
          root: ~/
          panes:
            - clear
            - cd ~/Work/11-Web/01-work/simptab
    ```
    
  
- Teamocil
  
  - Usage
    
    ``` shell
    tmux
    teamocil xxx
    ```
    
  - Config
     `mkdir .teamocil && cd .teamocil`

	 ``` yaml
    windows:
      - name: simptab
        root: ~/Work/11-Web/01-work/simptab
        layout: even-horizontal
        panes:
          - cd ~
          - git status
    ```
    
  


#### 参考

- <http://foocoder.com/blog/zhong-duan-huan-jing-zhi-tmux.html>
- <http://cenalulu.github.io/linux/tmux/>
- <https://github.com/tmuxinator/tmuxinator>
- <https://github.com/gpakosz/.tmux>
- <http://foocoder.com/blog/zhong-duan-huan-jing-zhi-tmux.html/>
- <http://baiqiuyi.com/linux/tmux%E5%B8%B8%E7%94%A8%E5%91%BD%E4%BB%A4.html>
- <http://mingxinglai.com/cn/2012/09/tmux/>
- <https://github.com/aqua7regia/tmux-Productive-Mouse-Free-Development_zh>
- <https://github.com/xfyuan/oh-my-cygwin/blob/master/tmux.conf>
- <http://stackoverflow.com/questions/26435333/cygwin-tmux-on-windows-7-why-wont-tmux-use-the-current-path>
- <https://github.com/arafatm/dotfiles/blob/master/home/.tmux.conf>
- <http://wing2south.com/post/40670260768/tmux/>
- <http://zuyunfei.com/2013/08/09/tmuxinator-best-mate-of-tmux/>
- <http://blog.xeonxu.info/blog/2012/11/04/shi-yong-tmuxgai-jin-zhong-duan-ti-yan/>
- <https://github.com/seebi/tmux-colors-solarized>
- <https://github.com/seebi/dircolors-solarized>
- <https://github.com/tmuxinator/tmuxinator>
- <http://zanshin.net/2013/09/05/my-tmux-configuration/>
- <http://nakkaya.com/2014/01/05/tmux-configuration/>
- <https://github.com/erikw/tmux-powerline>
- <https://wiki.freebsdchina.org/software/t/tmux>
- <http://imtx.me/archives/1805.html>
- <http://zuyunfei.com/2013/08/09/tmuxinator-best-mate-of-tmux/>
- <https://fabianfranke.de/2013/11/19/use-tmuxinator-to-recreate-tmux-panes-and-windows/>
- <http://tony.github.io/tmux-config/>
