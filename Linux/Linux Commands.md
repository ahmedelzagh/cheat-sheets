# Linux Essential Commands

| Command                                    | Description                                                                                                                                              |
| ------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `chsh`                                     | Change default Shell.                                                                                                                                    |
| `alias [alias name]="value"`               | Adds Alias.                                                                                                                                              |
| `unalias [alias name]`                     | Removes Alias.                                                                                                                                           |
| `alias -p`                                 | Prints all the defined aliases.                                                                                                                          |
| `history`                                  | Feature in many operating system shells that allows the user to recall, edit and rerun previous commands.                                                |
| `which command`                            | Allows users to search the list of paths in the $PATH environment variable and outputs the full path of the command specified as an argument.            |
| `usermod -aG group user`                   | Add user to a group, note that group membership doesn't take effect until you login again.                                                               |
| `gpasswd -d user group`                    | Remove user from a group.                                                                                                                                |
| `usermod -d /home/myhome --move-home user` | Change user home directory, `--move-home` flag is used to move the home content to the new directory.                                                    |
| `usemod -l new-name user-name`             | Change the name of the user.                                                                                                                             |
| `usermod -L user`                          | Locks the user's account.                                                                                                                                |
| `usermod -U user`                          | Unlocks the user's account.                                                                                                                              |
| `usermod user -e year-month-day`           | Set an expiration date for the user's password.                                                                                                          |
| `groups user`                              | Display user groups.                                                                                                                                     |
| `chage user`                               | View and change the user password expiry information, adding `-l` option will list the user's password expiry info.                                      |
| `sudo -l`                                  | Will let you know what you're allowed to do.                                                                                                             |
| `visudo`                                   | Used to edit the `sudoers` file.                                                                                                                         |
| `sudo apt-get autoremove app --purge`      | used to remove a package and its associated dependencies from an Ubuntu, `--purge` used to remove not only the package but also its configuration files. |
