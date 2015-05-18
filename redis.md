### How to launch it after installing with **homebrew**

To have launchd start redis at login:

```bash
    ln -sfv /usr/local/opt/redis/*.plist ~/Library/LaunchAgents
```

Then to load redis now:

```bash
    launchctl load ~/Library/LaunchAgents/homebrew.mxcl.redis.plist
```

Or, if you don't want/need launchctl, you can just run:

```bash
    redis-server /usr/local/etc/redis.conf
```
