# config tmux

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
```
