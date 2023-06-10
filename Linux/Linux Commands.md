# Linux Essential Commands

| Command                                    | Description                                                                                                                                  |
| ------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------- |
| `chsh`                                     | Change default Shell                                                                                                                         |
| `alias [alias name]="value"`               | Adds Alias                                                                                                                                   |
| `unalias [alias name]`                     | Removes Alias                                                                                                                                |
| `alias -p`                                 | prints all the defined aliases                                                                                                               |
| `which command`                        | allows users to search the list of paths in the $PATH environment variable and outputs the full path of the command specified as an argument |
| `gpasswd -d user group`                    | Remove user from a group                                                                                                                     |
| `usermod -aG group user`                   | Add user to a group                                                                                                                          |
| `usermod -d /home/myhome --move-home user` | Change user home directory, `--move-home` flag is used to move the home content to the new directory                                         |
| `usemod -l newUserName userName`           | Change the name of the user                                                                                                                  |
| `usermod -L user`                          | Locks the user's account                                                                                                                     |
| `usermod -U user`                          | Unlocks the user's account                                                                                                                   |
| `usermod user -e year-month-day`           | set an expiration date for the user's password                                                                                               |
| `chage user`                               | view and change the user password expiry information, adding `-l` option will list the user's password expiry info                           |
|                                            |                                                                                                                                              |
