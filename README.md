# Batch-install the Crontab file for your user


## About

This repo helps you maintain your user's crontab as a set of separate
version-controlled crontabs. There's nothing fancy here; just a shell
script and a directory of crontabs.


## How it works

1. Fork this repo so you can version-control your crontab file.

2. Create any set of `*.cron` files in the [crontab/](./crontab/) directory here.

3. Run `make install` in this repo to install those files to your user's 
   `~/.config/crontab/` directory.

4. In your user's `~/.profile` or `~/.bash_profile` script, call the script
   `~/.config/crontab/apply-crontabs`. This will concatenate all the `*.cron`
   files and pipe them to the `crontab` program. It is safe to run this command
   as often as you want. If your crontab files are incorrectly formatted, this
   script will fail.

5. If you want to maintain and reference shell scripts from your crontab files,
   just keep the files in the [crontab/](./crontab/) directory as `*.sh` scripts,
   and reference them from your crontab like so:
   ```crontab
   * * * * *  $HOME/.config/crontab/my-script.sh
   ```

