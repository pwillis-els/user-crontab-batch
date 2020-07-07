# Batch-install the Crontab file for your user


## About

This repo helps you maintain your user's crontab as a set of separate
version-controlled crontabs. There's nothing fancy here; just a shell
script and a directory of crontabs.


## How it works

1. Fork this repo so you can version-control your crontab files. You can keep different crontab files in branches named like `hostname_username`.

2. Create any `*.cron` files in this directory (see [sample-file.cron](./sample-file.cron))

3. In your user's `~/.profile` or `~/.bash_profile` script, call the script
   [apply-crontabs](./apply-crontabs). This will concatenate all the `*.cron`
   files and pipe them to your system `crontab` program. It is safe to run this
   command as often as you want. If your crontab files are incorrectly formatted,
   this script will fail.

If you want to maintain and reference shell scripts from your crontab files,
just keep the files in this directory and reference them from your crontab:
```crontab
* * * * *  $HOME/git/user-crontab-batch/my-script.sh
```
