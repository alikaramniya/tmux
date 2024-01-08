# config tmux

### زمانی که داریم توی tmux کار میکنیم و کد میزنیم امکان داره کامندی که وارد میکنیم خروجیش زیاد باشه و نیاز به scroll کردن داشته باشیم برای این کار ابتدا ctrl + b و بعد ] رو میزنیم که بریم توی مود scroll و بعد میتونیم با arrow key های بالا و پایین عملیات scroll کردن رو انجام بدیم ولی برای این که سریع تر این عمل انجام بشه کافیه ctrl رو بگیریم و بعد به بالا و پایین با arrow key ها عملیات scroll رو انجام بدیم 
```
ctrl+b [
```

### برای کانفگیک کردن باید ابتدا یک فایل به نام tmux.conf در مسیر home سیستم خود بسازید برای انجام این کار کافیه دستور زیر رو اجرا کنید

```
touch ~/.tmux.conf
```

### برای حذف کردن status bar در tmux کافیه دستور زیر رو داخل این فایل  tmux.conf کپی کنید

```
set -g status off
set-hook -g after-new-window      'if "[ #{session_windows} -gt 1 ]" "set status on"'
set-hook -g after-kill-pane       'if "[ #{session_windows} -lt 2 ]" "set status off"'
set-hook -g pane-exited           'if "[ #{session_windows} -lt 2 ]" "set status off"'
set-hook -g window-layout-changed 'if "[ #{session_windows} -lt 2 ]" "set status off"'

# config tmux for support color and italic font
set -g default-terminal 'tmux-256color'
```

### اگر از i3 استفاده میکنید و میخواین زمانی که ترمینال رو باز میکنین به صورت خودکار tmux هم برای شما اجرا بشه کافیه اول از همه فایل کانفیگ رو باز کنین که معمولا توی ادرس پایینه

```
vim .config/i3/config
```

### و بعد از اون دستور پایین رو اضافه کنین به جای دستور قبلی که برای باز کردن ترمینال داشتین 

```
bindsym $mod+Return exec kitty -e tmux
```
