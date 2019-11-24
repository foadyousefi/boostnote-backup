# Boostnote auto backup

This is a very simple, yet effective way of backing up your Boostnote notes to a github repository. Follow these steps:

1. Create a private github repository
2. Find Boostnote storage directory on your computer and CD into it
3. Create an empty repository by running `git init` 
4. Add your github repository as the remote origin to your local repo `git remote add origin git@github.com:<your-user-name>/<your-repo-name>.git`
5. Push your repo `git push -u origin master`
6. Create a shell script file with the following content:
```sh
cd <your-boostnote-storage-location>
git add .
git commit -a -m "<Some message for your commit>"
git push
```
7. Change shell command permission: `chmod 755 commit.sh`
8. Create a cronjob with your desire intervals by running `crontab -e` with the following content: (In this example, cronjob runs every 30 minutes, but you can change it however you want it to run)
```ah
*/30 * * * * <your-boostnote-storage-location>/commit.sh 1&>/dev/null
```

