
Linux from Scratch by CIsco
https://www.netacad.com/courses/os-it/ndg-linux-unhatched

Linux Cheat Sheet:
https://assets.hostinger.com/content/tutorials/pdf/Linux-Commands-Cheat-Sheet.pdf

YouTube: Introduction to Linux
https://www.youtube.com/watch?v=sWbUDq4S6Y8


## Listing Files

![[Pasted image 20261026204530.png|693]]

Each line corresponds to a file contained within the directory. The information can be broken down into fields separated by spaces. The fields are as follows:

**File Type**
![[Pasted image 20261026204715.png]]


The first field actually contains ten characters, where the first character indicates the type of file and the next nine specify permissions. The file types are:

| Symbol | File Type      | Description                                                                |
| ------ | -------------- | -------------------------------------------------------------------------- |
| `d`    | directory      | A file used to store other files.                                          |
| `-`    | regular file   | Includes readable files, images files, binary files, and compressed files. |
| `l`    | symbolic link  | Points to another file.                                                    |
| `s`    | socket         | Allows for communication between processes.                                |
| `p`    | pipe           | Allows for communication between processes.                                |
| `b`    | block file     | Used to communicate with hardware.                                         |
| `c`    | character file | Used to communicate with hardware.                                         |

The first file `alternatives.log` is a regular file `-`, while the second file `apache2` is a directory `d`.

**Permissions**

![[Pasted image 20261026204737.png]]

Permissions indicate how certain users can access a file. Keep reading to learn more about permissions.

**Hard Link Count**

![[Pasted image 20261026204816.png]]

This number indicates how many hard links point to this file.

**User Owner**

![[Pasted image 20261026204911.png]]

User `syslog` owns this file. Every time a file is created, the ownership is automatically assigned to the user who created it.

**Group Owner**

![[Pasted image 20261026204955.png]]

Indicates which group owns this file

**File Size**

![[Pasted image 20261026205033.png]]

Directories and larger files may be shown in kilobytes since displaying their size in bytes would present a very large number. Therefore, in the case of a directory, it might actually be a multiple of the block size used for the file system. Block size is the size of a series of data stored in the filesystem.

**Timestamp**

![[Pasted image 20261026205147.png]]

This indicates the time that the file's contents were last modified.

**Filename**

![[Pasted image 20261026205215.png]]

The final field contains the name of the file or directory.


**Consider This**

In the case of symbolic links, a file that points to another file, the link name will be displayed along with an arrow and the pathname of the original file.

![[Pasted image 20261026205254.png]]

### Sorting

By default the output of the `ls` command is sorted alphabetically by filename. It can sort by other methods as well.

The `-t` option will sort the files by timestamp:

![[Pasted image 20261026205504.png]]


The `-S` option will sort the files by file size:

![[Pasted image 20261026205627.png]]


The `-r` option will reverse the order of any type of sort.

![[Pasted image 20261026205724.png]]


Used alone the `-r` option with list the files in reverse alphabetical order:

![[Pasted image 20261026205828.png]]


## Administrative Access

There are many Linux commands which deal with sensitive information like passwords, system hardware, or otherwise operate under other exceptional circumstances. Preventing regular users from executing these commands helps to protect the system. Logging in as the root user provides administrative access, allowing for the execution of some of the privileged commands.

### The `su` Command

``` shell
su OPTIONS USERNAME
```

The `su` command allows you to temporarily act as a different user. It does this by creating a new shell. The shell is simply a text input console that lets you type in commands. By default, if a user account is not specified, the `su` command will open a new shell as the root user, which provides administrative privileges.

Simple analogy: Imagine you're using your computer as a regular employee. The `su` command lets you temporarily log in as another employee or the administrator without ending your original session.


Utilizing the login shell option is recommended, as the login shell fully configures the new shell with the settings of the new user. This option can be specified one of three ways:

![[Pasted image 20261026210528.png]]

After executing the `su` command, a password is required. On our virtual machines, the password for both the `root` and `sysadmin` accounts is `netlab123`. If you ever forget, it is displayed every time a new virtual machine is started. As a security measure, the password will not be visible as it is typed.

![[Pasted image 20261026210656.png]]

Note the command prompt has changed to reflect that you are now logged in as the `root` user. To logout and return to the `sysadmin` account, use the `exit` command. Note the prompt changes back:

![[Pasted image 20261026210809.png]]

To avoid executing any sensitive commands, we’ve configure the Steam Locomotive command, the `sl` command, to require administrative access. If the command is executed as `sysadmin`, it fails:

![[Pasted image 20261026210949.png]]

Use the `su` command to switch to the root account and execute the `sl` command with administrative access:

![[Pasted image 20261026211206.png]]

![[Pasted image 20261026211104.png]]


### The `sudo` Command

``` shell
sudo [OPTIONS] COMMAND
```

The `sudo` command allows a user to execute a command as another user without creating a new shell. Instead, to execute a command with administrative privileges, use it as an argument to the `sudo` command. Like the `su` command, the `sudo` command assumes by default the `root` user account should be used to execute commands.

**Consider This**

The `sudo` command can be used to switch to other user accounts as well. To specify a different user account use the `-u` option.

Execute the `sl` command as the root user by putting `sudo` in front of it:
![[Pasted image 20261026211528.png]]

![[Pasted image 20261026211104.png]]

Once the command has completed, notice the prompt has not changed, you are still logged in as `sysadmin`. The `sudo` command only provides administrative access for the execution of the specified command. This is an advantage as it reduces the risk that a user accidentally executes a command as root. The intention to execute a command is clear; the command is executed as root if prefixed with the `sudo` command. Otherwise, the command is executed as a regular user.


## Permissions

Permissions determine the ways different users can interact with a file or directory. When listing a file with the `ls -l` command, the output includes permission information. For the example we will use a script called `hello.sh` located in the `Documents` directory:

**sysadmin@localhost:~$** cd ~/Documents

![[Pasted image 20261027104431.png]]

### File Type Field

![[Pasted image 20261027104511.png]]

The first character of this output indicates the type of a file. Recall that if the first character is a `-`, this is a regular file. If the character was a `d`, it would be a directory.

### Permissions Field

![[Pasted image 20261027104559.png]]

After the file type character, the permissions are displayed. The permissions are broken into three sets of three characters:
#### Owner

![[Pasted image 20261027104705.png]]

The first set is for the user who owns the file. If your current account is the user owner of the file, then the first set of the three permissions will apply and the other permissions have no effect.

The user who owns the file, and who these permissions apply to, can be determined by the user owner field:

![[Pasted image 20261027104759.png]]

#### Group

![[Pasted image 20261027104844.png]]

The second set is for the group that owns the file. If your current account is not the user owner of the file and you are a member of the group that owns the file, then the group permissions will apply and the other permissions have no effect.

The group for this file can be determined by the group owner field:
![[Pasted image 20261027104958.png]]

#### Other

![[Pasted image 20261027105041.png]]

The last set is for everyone else, any one who that first two sets of permissions do not apply to. If you are not the user who owns the file or a member of the group that owns the file, the third set of permissions applies to you.


### Permission Types

There are three different permissions that can be placed on a file or directory: read, write, and execute. The manner in which these permissions apply differs for files and directories, as shown in the chart below:

| Permission    | Effects on File                                                                                              | Effects on Directory                                                                                                                                      |
| ------------- | ------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| read (`r`)    | Allows for file contents to be read or copied.                                                               | Without execute permission on the directory, allows for a non-detailed listing of files. With execute permission, `ls -l` can provide a detailed listing. |
| write (`w`)   | Allows for contents to be modified or overwritten. Allows for files to be added or removed from a directory. | For this permission to work, the directory must also have execute permission.                                                                             |
| execute (`x`) | Allows for a file to be run as a process, although script files require read permission, as well.            | Allows a user to change to the directory if parent directories have execute permission as well.                                                           |

**Consider This**

Understanding which permissions apply is an important skill set in Linux. For example, consider the following set of permissions:

![[Pasted image 20261027105321.png]]

In this scenario, the user `sysadmin` ends up having less access to this file than members of the `staff` group or everyone else. The user `sysadmin` only has the permissions of `r--`. It doesn't matter if `sysadmin` is a member of the `staff` group; once user ownership has been established, only the user owner's permissions apply.


## Changing File Permissions

The `chmod` command is used to change the permissions of a file or directory. Only the root user or the user who owns the file is able to change the permissions of a file.

**Consider This**

Why is the command named `chmod` instead of `chperm`? Permissions used to be referred to as modes of access, so the command `chmod` really means **ch**ange the **mod**es of access.


There are two techniques for changing permissions with the `chmod` command: 
- symbolic 
- octal

The symbolic method is good for changing one set of permissions at a time.

The octal or numeric method requires knowledge of the octal value of each of the permissions and requires all three sets of permissions (user, group, other) to be specified every time.

### The Symbolic Method

``` shell
chmod [<SET><ACTION><PERMISSIONS>]... FILE
```

To use the symbolic method of `chmod` first indicate which set of permissions is being changed:

![[Pasted image 20261027111000.png]]

|Symbol|Meaning|
|---|---|
|`u`|User: The user who owns the file.|
|`g`|Group: The group who owns the file.|
|`o`|Others: Anyone other than the user owner or member of the group owner.|
|`a`|All: Refers to the user, group and others.|

Next, specify an action symbol:

![[Pasted image 20261027111051.png]]

|Symbol|Meaning|
|---|---|
|`+`|Add the permission, if necessary|
|`=`|Specify the exact permission|
|`-`|Remove the permission, if necessary|

After an action symbol, specify one or more permissions to be acted upon.

![[Pasted image 20261027111136.png]]

|Symbol|Meaning|
|---|---|
|`r`|read|
|`w`|write|
|`x`|execute|

Finally, a space and the pathnames for the files to assign those permissions.

![[Pasted image 20261027111215.png]]


![[Pasted image 20261027111545.png]]


**Consider This**

Notice that to execute the script in the previous example, a `./` character combination was placed before the script name.

**./** hello.sh

This indicates the "command" should be run from the current directory.

---

The trick is to count the characters in groups of three, starting after the first character.

```
- | rwx | r-- | r--
   User  Group Others
```



## Changing File Ownership

Initially, the owner of a file is the user who creates it. The `chown` command is used to change the ownership of files and directories. Changing the user owner requires administrative access. A regular user cannot use this command to change the user owner of a file, even to give the ownership of one of their own files to another user. However, the `chown` command also permits changing group ownership, which can be accomplished by either root or the owner of the file.

To change the user owner of a file, the following syntax can be used. 

The first argument, `[OWNER]`, specifies which user is to be the new owner. 

The second argument, `FILE`, specifies which file's ownership is changing.

![[Pasted image 20261027112230.png]]

Currently all the files in the `Documents` directory are owned by the `sysadmin` user.

![[Pasted image 20261027112625.png]]

To switch the owner of the `hello.sh` script to the `root` user, use `root` as the first argument and `hello.sh` as the second argument.

![[Pasted image 20261027112559.png]]

**Consider This**

Try executing the `hello.sh` script again. It fails! Why?

![[Pasted image 20261027113622.png]]

Only the user owner has the execute permission, and now the `root` user is the user owner. This file now requires administrative access to execute. Use the `sudo` command to execute the script as the `root` user.

![[Pasted image 20261027114317.png]]



## Viewing Files

There are a few Linux commands available to view the content of files. The `cat` command, which stands for “concatenate”, is often used to quickly view the contents of small files.

The `cat` command will display the entire contents of the file, hence why it is mainly recommended for smaller files where the output is limited and does not require scrolling. To view the contents of a file using the `cat` command, simply type the command and use the name of the file you wish to view as the argument:

``` shell
cat [OPTIONS] [FILE]
```

Example:
![[Pasted image 20261027121311.png]]

The `cat` command displays all five lines of the file above. When viewing larger files, the `cat` command can result in very lengthy output that cannot be paused to scroll through. A better method of viewing long text files, is with a pager command which has a functionality that can pause and scroll through the output of the file.

Examples of pager commands include the `more` and `less` commands.

Another way to view the content of files is by using the `head` and `tail` commands. These commands are used to view a select number of lines from the top or bottom of a file. Taking a look at a few lines of a file can sometimes be helpful to ensure that the file is the one you want to use.

Another reason to preview only the first or last few lines, is because some files, such as system log files are frequently updated with new entries. Similar to the `cat` command, the `head` and `tail` commands use the name of the file you want to view as the argument to the command:

``` shell
head [OPTIONS] [FILE]

tail [OPTIONS] [FILE]
```

Example:
![[Pasted image 20261027121557.png]]

To filter the output and view lines from the top of the `alpha.txt` file, use the `head` command:

![[Pasted image 20261027121646.png]]

Then, to view lines at the bottom of the `alpha.txt` file, you use the `tail` command:

![[Pasted image 20261027121842.png]]

By examining the output of the `head` and `tail` commands above, you can see that the default behavior of the `head` and `tail` commands in this shell is to display ten lines.

The `-n` option with the `head` and `tail` commands can be used to specify the amount of lines to display. To use the `-n` option, specify the amount of lines from the file you want to display after the option and use the filename as an argument:

``` shell
head -n number_of_lines filename
```

Example:

![[Pasted image 20261027122003.png]]

![[Pasted image 20261027122049.png]]


## Copying Files

Creating copies of files can be useful for numerous reasons:

- If a copy of a file is created before changes are made, then it is possible to revert back to the original.
- A copy of a file can be used to transfer a file to removable media devices.
- A copy of an existing document can be used as a template for a new document.

``` shell
cp [OPTIONS] SOURCE DESTINATION
```

![[Pasted image 20261027122350.png]]

**Consider This**

Permissions can have an impact on file management commands, such as the `cp` command. In order to copy a file, it is necessary to have execute permission to access the directory where the file is located and the read permission for the file being copied.

It is also necessary to have write and execute permission on the directory the file is being copied to. Typically, there are two places where you should always have write and execute permission on the directory: your home directory and the `/tmp` directory.


The `dd` command is a utility for copying files or entire partitions at the bit level.

``` shell
dd [OPTIONS] OPERAND
```

This command has several useful features, including:

- It can be used to clone or delete (wipe) entire disks or partitions.
- It can be used to copy raw data to removable devices, such as USB drives and CDROMs.
- It can backup and restore the MBR (Master Boot Record).
- It can be used to create a file of a specific size that is filled with binary zeros, which can then be used as a swap file (virtual memory).

Let's examine the following example. The `dd` command creates a file named `/tmp/swapex` with 50 blocks of zeros that are one megabyte in size:

![[Pasted image 20261027123659.png]]

![[Pasted image 20261027123747.png]]

**Consider This**

No block size or count needs to be specified when copying over entire devices. For example, to clone from one hard drive (`/dev/sda`) to another (`/dev/sdb`) execute the following command:

``` shell
dd if=/dev/sda of=/dev/sdb
```


## Moving Files

The `mv` command is used to move a file from one location in the filesystem to another.

``` shell
mv SOURCE DESTINATION
```

The `mv` command requires at least two arguments. 

The first argument is the source, a path to the file to be moved. 

The second argument is the destination, a path to where the file will be moved to. 

The files to be moved are sometimes referred to as the source, and the place where the files are to be placed is called the destination.

Example:
![[Pasted image 20261027124819.png]]

The `mv` command is able to move multiple files, as long as the final argument provided to the command is the destination. For example, to move three files into the `School` directory:

![[Pasted image 20261027124954.png]]

Moving a file within the same directory is an effective way to rename it. For example, in the following example the `animals.txt` file is given a new name of `zoo.txt`:

``` shell
mv animals.txt zoo.txt
```

![[Pasted image 20261027125147.png]]

**Consider This**

Permissions can have an impact on file management commands, such as the `mv` command. Moving a file requires write and execute permissions on both the origin and destination directories.


## Removing Files

The `rm` command is used to delete files and directories. It is important to keep in mind that deleted files and directories do not go into a "trash can" as with desktop-oriented operating systems. When a file is deleted with the `rm` command, it is almost always permanently gone.

``` shell
rm [OPTIONS] FILE
```

Without any options, the `rm` command is typically used to remove regular files:

![[Pasted image 20261027125514.png]]

The `rm` command will ignore directories that it's asked to remove; to delete a directory, use a recursive option, either the `-r` or `-R` options. Just be careful since these options are "recursive", this will delete all files and all subdirectories:

![[Pasted image 20261027125808.png]]

**Consider This**

Permissions can have an impact on file management commands, such as the `rm` command.

To delete a file within a directory, a user must have write and execute permission on a directory. Regular users typically only have this type of permission in their home directory and its subdirectories.



## Filtering Input

The `grep` command is a text filter that will search input and return lines which contain a match to a given pattern.

``` shell
grep [OPTIONS] PATTERN [FILE]
```

For example, the `passwd` file we previously copied into the `Documents` directory contains the details of special system accounts and user accounts on the system. This file can be very large, however the `grep` command can be used to filter out information about a specific user, such as the `sysadmin` user. Use `sysadmin` as the pattern argument and `passwd` as the file argument:

![[Pasted image 20261027131133.png]]

The command above returned the line from the `passwd` which contains the pattern `sysadmin`.

The example above uses a simple search term as the pattern, however `grep` is able to interpret much more complex search patterns.


## Regular Expressions

Regular expressions have two common forms: basic and extended. Most commands that use regular expressions can interpret basic regular expressions. However, extended regular expressions are not available for all commands and a command option is typically required for them to work correctly.

The following table summarizes basic regular expression characters:

| Basic Regex Character(s) | Meaning                                                                                                                 |
| ------------------------ | ----------------------------------------------------------------------------------------------------------------------- |
| `.`                      | Any one single character                                                                                                |
| `[ ]`                    | Any one specified character                                                                                             |
| `[^ ]`                   | Not the one specified character                                                                                         |
| `*`                      | Zero or more of the previous character                                                                                  |
| `^`                      | If first character in the pattern, then pattern must be at beginning of the line to match, otherwise just a literal `^` |
| `$`                      | If last character in the pattern, then pattern must be at the end of the line to match, otherwise just a literal `$`    |

The following table summarizes the extended regular expressions, which must be used with either the `egrep` command or the `-E` option with the `grep` command:

| Extended Regex Character(s) | Meaning                                                           |
| --------------------------- | ----------------------------------------------------------------- |
| `+`                         | One or more of the previous pattern                               |
| `?`                         | The preceding pattern is optional                                 |
| `{ }`                       | Specify minimum, maximum or exact matches of the previous pattern |
| \|                          | Alternation - a logical "or"                                      |
| `( )`                       | Used to create groups                                             |

## Basic Patterns

### Anchor Characters

Anchor characters are one of the ways regular expressions can be used to narrow down search results. For example, the pattern `root` appears many times in the `/etc/passwd` file:

![[Pasted image 20261027131916.png]]

To prevent the shell from misinterpreting them as special shell characters, these patterns should be protected by strong quotes, which simply means placing them between single quotes.

The first anchor character `^` is used to ensure that a pattern appears at the beginning of the line. For example, to find all lines in `/etc/passwd` that start with `root` use the pattern `^root`. Note that `^` must be the first character in the pattern to be effective.

![[Pasted image 20261027132152.png]]

The second anchor character `$` can be used to ensure a pattern appears at the end of the line, thereby effectively reducing the search results. To find the lines that end with an `r` in the `alpha-first.txt` file, use the pattern `r$`:

![[Pasted image 20261027132348.png]]


### Match a Single Character With `.`

One of the most useful expressions is the period `.` character. It will match any character except for the new line character. The pattern `r..f` would find any line that contained the letter `r` followed by exactly two characters (which can be any character except a newline) and then the letter `f`:

![[Pasted image 20261027132613.png]]

The same concept can be repeated using other combinations. The following will find four letter words that start with `r` and with `d`:

![[Pasted image 20261027132745.png]]

This character can be used any number of times. To find all words that have at least four characters the following pattern can be used:

![[Pasted image 20261027132858.png]]

The line does not have to be an exact match, it simply must contain the pattern, as seen here when `r..t` is searched for in the `/etc/passwd` file:

![[Pasted image 20261027133202.png]]


### Match a Single Character With `[]`

The square brackets `[ ]` match a single character from the list or range of possible characters contained within the brackets.

To find all the lines in the `profile.txt` which have a number in them, use the pattern `[0123456789]` or `[0-9]`:

![[Pasted image 20261027133531.png]]

On the other hand, to find all the lines which contain any non-numeric characters, insert a `^` as the first character inside the brackets. This character negates the characters listed:

![[Pasted image 20261027133750.png]]

**Note**

Do not mistake `[^0-9]` to match lines which do not contain numbers. It actually matches lines which contain non-numbers. Look at the original file to see the difference. The third and sixth lines only contain numbers, they do not contain non-numbers so those lines do not match.


When other regular expression characters are placed inside of square brackets, they are treated as literal characters. For example, the `.` normally matches any one character, but placed inside the square brackets, then it will just match itself. In the next example, only lines which contain the `.` character are matched.

![[Pasted image 20261027134015.png]]


### Match a Repeated Character Or Patterns With `*`

The regular expression character `*` is used to match zero or more occurrences of a character or pattern preceding it. For example `e*` would match zero or more occurrences of the letter `e`:

![[Pasted image 20261027134156.png]]

It is also possible to match zero or more occurrences of a list of characters by utilizing the square brackets. The pattern `[oe]*` used in the following example will match zero or more occurrences of the `o` character or the `e` character:

![[Pasted image 20261027134323.png]]

When used with only one other character, `*` isn't very helpful. Any of the following patterns would match every string or line in the file: `.*` `e*` `b*` `z*`.

![[Pasted image 20261027134514.png]]

![[Pasted image 20261027134528.png]]

This is because `*` can match zero occurrences of a pattern. In order to make the `*` useful, it is necessary to create a pattern which includes more than just the one character preceding `*`. For example, the results above can be refined by adding another `e` to make the pattern `ee*` effectively matching every line which contains at least one `e`.

![[Pasted image 20261027134659.png]]

### Standard Input

If a file name is not given, the `grep` command will read from standard input, which normally comes from the keyboard with input provided by the user who runs the command. This provides an interactive experience with `grep` where the user types in the input and `grep` filters as it goes. Feel free to try it out, just press **Ctrl-D** when you're ready to return to the prompt.

![[Pasted image 20261027135052.png]]



## Shutting Down

The `shutdown` command arranges for the system to be brought down in a safe way. All logged-in users are notified that the system is going down and within the last five minutes leading up to the shutdown, new logins are prevented.

``` shell
shutdown [OPTIONS] TIME [MESSAGE]
```

The `shutdown` command requires administrative access, switch to the `root` account for this section using the following command. Use `netlab123` as the password.

![[Pasted image 20261027135432.png]]

![[Pasted image 20261027135604.png]]

Unlike other commands used to bring the system down, the `shutdown` command requires a time argument specifying when the shutdown should begin. Formats of this time argument can be the word `now`, a time of day in the format `hh:mm` or the number of minutes to delay in the format `+minutes`.

**Consider This**

The clock on our system may be set to a different timezone than the one in which you are located. To check the time in the terminal, use the `date` command. On our machines, the default format of the `date` command output is as follows:

``` shell
weekday month day hour:minute:second UTC year
```

The letters `UTC` present in the output indicates that the time is being displayed as Universal Coordinated Time.

![[Pasted image 20261027140637.png]]

The `shutdown` command also has an optional message argument, indicating a message that will appear in the terminals of all users. For example:

![[Pasted image 20261027140925.png]]


## Network Configuration

The `ifconfig` command stands for "interface configuration" and is used to display network configuration information.

``` shell
ifconfig [OPTIONS]
```

**Note**

The `iwconfig` command is similar to the `ifconfig` command, but it is dedicated to wireless network interfaces.

Not all network settings are important for this module, but it is important to note in the following example that the IPv4 address of the primary network device `eth0` is `192.168.1.2` and that the device is currently active (`UP`):

![[Pasted image 20261027185951.png]]

**Consider This**

The `lo` device is referred to as the loopback device. It is a special network device used by the system when sending network-based data to itself.


The `ifconfig` command can also be used to temporarily modify network settings. Typically these changes should be permanent, so using the `ifconfig` command to make such changes is fairly rare.

The `ping` command is used to verify connectivity between two computers. It does this by sending packets to another machine on a network. If the sender receives a response it should be possible to connect to that machine.

Information is sent using “packets”; the encapsulated unit of data sent over a network. In order for the packets to find the other computer, they will need an address. The `ping` command uses IP addresses to identify a computer on the network that it wants to connect to.

By default, the `ping` command will continue sending packets until the break command (**CTL** + **C**) is entered at the console. To limit how many pings are sent, use the `-c` option followed by the number of pings to be sent. The example below shows `ping` being limited to 4 iterations with `-c 4`.

If the `ping` command is successful, you will see output like the following:

![[Pasted image 20261027190434.png]]

If the `ping` command fails, you will receive a message stating, `Destination Host Unreachable`:

![[Pasted image 20261027190541.png]]

The `ping` command may fail even though the remote machine is connecting. This is because some administrators configure their machines, or even entire networks, not to respond to `ping` requests as a security measure. The `ping` command also works with a hostname, or domain name like yahoo.com. Using this first saves time, if that `ping` command is successful, there is proper name resolution AND the IP address is functioning properly as well.


## Viewing Processes

Running a command results in something called a process. In the Linux operating system, processes are executed with the privileges of the user who executes the command. This allows for processes to be limited to certain capabilities based upon the user identity.

Although there are exceptions, generally the operating system will differentiate users based upon whether they are the administrator. Typically regular users, like the `sysadmin` user, cannot control another user's processes. Users who have administrative privileges, like the `root` account, can control any user processes, including stopping any user process.

The `ps` command can be used to list processes.

``` shell
ps [OPTIONS]
```

![[Pasted image 20261027191209.png]]

The `ps` command will display the processes that are running in the current terminal by default. In the example above, the bottom line is the process created by the execution of the `ps` command. The output includes the following columns of information:

- `PID`: The process identifier, which is unique to the process. This information is useful for controlling the process by its ID number.
    
- `TTY`: The name of the terminal where the process is running. This information is useful for distinguishing between different processes that have the same name.
    
- `TIME`: The total amount of processor time used by the process. Typically, this information isn't used by regular users.
    
- `CMD`: The command that started the process.

Instead of viewing just the processes running in the current terminal, users may want to view every process running on the system. The `-e` option will display every process:

![[Pasted image 20261027191733.png]]

Typically, the `-f` option is also used as it provides more detail in the output of the command, including options and arguments. Look for the `ps` command on the last line, the `CMD` column now includes the options used:

![[Pasted image 20261027192026.png]]


## Package Management

Package management is a system by which software can be installed, updated, queried or removed from a filesystem. In Linux, there are many different software package management systems, but the two most popular are those from Debian and Red Hat. The virtual machines for this course use Ubuntu, a derivative of Debian.

At the lowest level of the Debian package management system is the `dpkg` command. This command can be tricky for novice Linux users, so the Advanced Package Tool, `apt-get`, a front-end program to the `dpkg` tool, makes management of packages even easier.

**Note**

A front-end program is a program that users can see and interact with.

### Installing Packages

Package files are commonly installed by downloading them directly from repositories located on Internet servers. The Debian repositories contain more than 65,000 different packages of software. Before installing a package, it is good practice to refresh the list of available packages using the `apt-get update` command.

``` shell
sudo apt-get update
```

![[Pasted image 20261027192456.png]]

To search for keywords within these packages, you can use the `apt-cache search` command.

``` shell
apt-cache search [keyword]
```

The keyword that is used should match part of the name or description of the package that is to be located. Multiple keywords can be used to further clarify the search; for example, the search term `web server` would provide better results than `web` or `server`.

To find packages associated with the `cow` keyword:

![[Pasted image 20261027192757.png]]

Once you've found the package that you want to install, you can install it with the `apt-get install` command:

``` shell
sudo apt-get install [package]
```

![[Pasted image 20261027193041.png]]

**Consider This**

The `cowsay` command is a configurable talking cow! Use a word or phrase as an argument:

![[Pasted image 20261027193159.png]]

### Updating Packages

The `apt-get install` command can also update a package, if that package is installed and a newer version is available. If the package is not already on the system, it would be installed; if it is on the system, it would be updated.

Updating all packages of the system should be done in two steps. First, update the cache of all packages available with `apt-get update`. Second, execute the `apt-get upgrade` command and all packages and dependencies will be updated.

``` shell
apt-get update

apt-get upgrade
```

![[Pasted image 20261027193455.png]]


### Removing Packages

The `apt-get` command is able to either remove or purge a package. The difference between the two is that purging deletes all package files, while removing deletes all but the configuration files for the package.

An administrator can execute the `apt-get remove` command to remove a package or the `apt-get purge` command to purge a package completely from the system.

``` shell
apt-get remove [package]

apt-get purge [package]
```

![[Pasted image 20261027193924.png]]


## Updating User Passwords

The `passwd` command is used to update a user’s password. Users can only change their own passwords, whereas the root user can update the password for any user.

``` shell
passwd [OPTIONS] [USER]
```

For example, since we are logged in as the `sysadmin` user we can change the password for that account. Execute the `passwd` command. You will be prompted to enter the existing password once and the new password twice. For security reasons, no output is displayed while the password is being typed. The output is shown as follows:

![[Pasted image 20261027194331.png]]

If the user wants to view status information about their password, they can use the `-S` option:

![[Pasted image 20261027194434.png]]

| Field           | Example      | Meaning                                                                                                     |
| --------------- | ------------ | ----------------------------------------------------------------------------------------------------------- |
| User Name       | `sysadmin`   | The name of the user.                                                                                       |
| Password Status | `P`          | `P` indicates a usable password.<br><br>`L` indicates a locked password.<br><br>`NP` indicates no password. |
| Change Date     | `03/01/2015` | The date when the password was last changed.                                                                |
| Minimum         | `0`          | The minimum number of days that must pass before the current password can be changed by the user.           |
| Maximum         | `99999`      | The maximum number of days remaining for the password to expire.                                            |
| Warn            | `7`          | The number of days prior to password expiry that the user is warned.                                        |
| Inactive        | `-1`         | The number of days after password expiry that the user account remains active.                              |

Switch the `root` account using the following command. Use `netlab123` as the password:

The root user can change the password of any user. If the root user wants to change the password for `sysadmin`, they would execute the following command:

![[Pasted image 20261027194820.png]]


## Redirection

Adding content to files in Linux can be done in a variety of ways. Linux has a few text editors that can be used to add content to a file. However, this method requires some familiarity with Linux text editor commands.

There is a way in Linux to quickly add content to a file using a command line feature called input/output (I/O) redirection. I/O redirection allows for information in the command line to be sent to files, devices, and other commands. The input or output of a command is redirected from its default destination to a different location. I/O redirection is like a series of train tracks, where a switch can be enabled to direct the output of a command on a different track so it goes somewhere else in the shell. In this section, we are writing to files by redirecting the output of a command to a file.

When it comes to command input and output there are three paths, or “tracks”. These paths are called file descriptors. The first file descriptor is standard input, abbreviated as STDIN. Standard input is the information the command receives and processes when it is executed, essentially what a user types on the keyboard. The second file descriptor is standard output, abbreviated as STDOUT. Standard output is the information that the command displays, the output of the command. The last file descriptor is standard error, abbreviated as STDERR. STDERR, are the error messages generated by commands that are not correctly executed. The following are examples of how file descriptors will appear in the terminal:

![[Pasted image 20261027200317.png]]

This section will cover one of the three file descriptors, STDOUT, and how to redirect STDOUT from where you normally see it, in the terminal, to a file in the filesystem. To use redirection, simply use a greater-than symbol `>` along with a filename:

``` shell
[COMMAND] > [FILE]
```

To demonstrate redirection, we will use the output of the `cat` command. Without redirection, the output of the `cat` command will be displayed in the terminal:

![[Pasted image 20261027200529.png]]

Now use the `>` character to redirect the STDOUT of the `cat food.txt` command above to a new file called `newfile1.txt`:

![[Pasted image 20261027200640.png]]

This is useful if you need to copy content from an important file to another file in order to edit the contents without modifying the original file. However, what if you want to add a comment or note to a file? To do this, you can use the `echo` command. The `echo` command is used to print output in the terminal:

![[Pasted image 20261027200837.png]]

Printing comments to the screen is a fun feature but the `echo` command can be made more useful by using redirection. Using the `echo` command, content can be added to the `newfile1.txt` file:

![[Pasted image 20261027200928.png]]

Notice that the STDOUT of the `echo` command has replaced the original content of the file. This is because the single `>` character will overwrite any contents in an existing file. To append rather than overwrite content to a file, use a double greater-than symbol `>>`:

![[Pasted image 20261027201130.png]]

**Important**

To redirect information to an existing file, the user must have write permissions on that file.


## Text Editor

The premier text editor for Linux and UNIX is a program called `vi`. While there are numerous editors available for Linux that range from the tiny editor `nano` to the massive `emacs` editor, there are several advantages to the `vi` editor:

- The `vi` editor is available on every Linux distribution in the world. This is not true of any other editor.
    
- The `vi` editor can be executed both in a CLI (command line interface) and a GUI (graphical user interface).
    
- While new features have been added to the `vi` editor, the core functions have been around for decades. This means that if someone learned the `vi` editor in the 1970s, they could use a modern version without any problem. While that seems trivial, it may not seem so trivial twenty years from now.

In reality, most Linux systems don't include the original `vi`, but an improved version of it known as `vim`, for vi improved. This fact may be hidden by most Linux distributions. For the most part, `vim` works just like `vi`, but has additional features. For the topics that will be covered in this course, either `vi` or `vim` will work.

To get started using `vi`, simply type the command followed by the pathname to the file to edit or create:

``` shell
vi newfile.txt
```

There are three modes used in `vi`: command mode, insert mode, and ex mode.

### Command Mode Movement

Initially, the program starts in command mode. Command mode is used to type commands, such as those used to move around a document, manipulate text, and access the other two modes. To return to command mode at any time, press the **Esc** key.

Once some text has been added into a document, to perform actions like moving the cursor, the **Esc** key needs to be pressed first to return to command mode. This seems like a lot of work, but remember that `vi` works in a terminal environment where a mouse is useless.

Movement commands in `vi` have two aspects, a motion and an optional number prefix, which indicates how many times to repeat that motion. The general format is as follows:

``` shell
[count] motion
```

The following table summarizes the motion keys available:

|Motion|Result|
|---|---|
|`h`|Left one character|
|`j`|Down one line|
|`k`|Up one line|
|`l`|Right one character|
|`w`|One word forward|
|`b`|One word back|
|`^`|Beginning of line|
|`$`|End of the line|
**Note**

Since the upgrade to `vim` it is also possible to use the arrow keys `←``↓``↑``→` instead of `h``j``k``l` respectively.

These motions can be prefixed with a number to indicate how many times to perform the movement. For example, `5h` would move the cursor five characters to the left and `3w` would move the cursor three words to the right.

To move the cursor to a specific line number, type that line number followed by the `G` character. For example, to get to the fifth line of the file type `5G`. `1G` or `gg` can be used to go to the first line of the file, while a lone `G` will take you to the last line. To find out which line the cursor is currently on, use **CTRL+G**.

### Command Mode Actions

The standard convention for editing content with word processors is to use copy, cut, and paste. The `vi` program has none of these. Instead, `vi` uses the following three commands:

| Standard | Vi         | Meaning |
| -------- | ---------- | ------- |
| cut      | `d`        | delete  |
| copy     | `y`        | yank    |
| paste    | `P` \| `p` | put     |
The motions learned from the previous page are used to specify where the action is to take place, always beginning with the present cursor location. Either of the following general formats for action commands is acceptable:

``` shell
action [count] motion

[count] action motion
```

### Delete

Delete removes the indicated text from the page and saves it into the buffer, the buffer being the equivalent of the "clipboard" used in Windows or Mac OSX. The following table provides some common usage examples:

|Action|Result|
|---|---|
|`dd`|Delete current line|
|`3dd`|Delete the next three lines|
|`dw`|Delete the current word|
|`d3w`|Delete the next three words|
|`d4h`|Delete four characters to the left|

### Change

Change is very similar to delete; the text is removed and saved into the buffer, however, the program is switched to insert mode to allow immediate changes to the text. The following table provides some common usage examples:

|Action|Result|
|---|---|
|`cc`|Change current line|
|`cw`|Change current word|
|`c3w`|Change the next three words|
|`c5h`|Change five characters to the left|

### Yank

Yank places content into the buffer without deleting it. The following table provides some common usage examples:

|Action|Result|
|---|---|
|`yy`|Yank current line|
|`3yy`|Yank the next three lines|
|`yw`|Yank the current word|
|`y$`|Yank to the end of the line|

### Put

Put places the text saved in the buffer either before or after the cursor position. Notice that these are the only two options, put does not use the motions like the previous action commands.

|Action|Result|
|---|---|
|`p`|Put (paste) after cursor|
|`P`|Put before cursor|

### Searching in vi

Another standard function that word processors offer is find. Often, people use **CTRL+F** or look under the edit menu. The `vi` program uses search. Search is more powerful than find because it supports both literal text patterns and regular expressions.

To search forward from the current position of the cursor, use the `/` to start the search, type a search term, and then press the **Enter** key to begin the search. The cursor will move to the first match that is found.

To proceed to the next match using the same pattern, press the `n` key. To go back to a previous match, press the `N` key. If the end or the beginning of the document is reached, the search will automatically wrap around to the other side of the document.

To start searching backwards from the cursor position, start by typing `?`, then type the pattern to search for matches and press the **Enter** key.

### Insert Mode

Insert mode is used to add text to the document. There a few ways to enter insert mode from command mode, each differentiated by where the text insertion will begin. The following table covers the most common:

|Input|Purpose|
|---|---|
|`a`|Enter insert mode right after the cursor|
|`A`|Enter insert mode at the end of the line|
|`i`|Enter insert mode right before the cursor|
|`I`|Enter insert mode at the beginning of the line|
|`o`|Enter insert mode on a blank line after the cursor|
|`O`|Enter insert mode on a blank line before the cursor|

### Ex Mode

Originally, the `vi` editor was called the `ex` editor. The name `vi` was the abbreviation of the **visual** command in the `ex` editor which switched the editor to "visual" mode.

In the original normal mode, the `ex` editor only allowed users to see and modify one line at a time. In the visual mode, users could see as much of the document that will fit on the screen. Since most users preferred the visual mode to the line editing mode, the `ex` program file was linked to a `vi` file, so that users could start `ex` directly in visual mode when they ran the `vi` link.

Eventually, the actual program file was renamed `vi` and the `ex` editor became a link that pointed the `vi` editor.

When the ex mode of the `vi` editor is being used, it is possible to view or change settings, as well as carry out file-related commands like opening, saving or aborting changes to a file. In order to get to the ex mode, type a `:` character in command mode. The following table lists some common actions performed in ex mode:

|Input|Purpose|
|---|---|
|`:w`|Write the current file to the filesystem|
|`:w filename`|Save a copy of the current file as `filename`|
|`:w!`|Force writing to the current file|
|`:1`|Go to line number 1 or whatever number is given|
|`:e filename`|Open `filename`|
|`:q`|Quit if no changes made to file|
|`:q!`|Quit without saving changes to file|

A quick analysis of the table above reveals that if an exclamation mark, `!`, is added to a command, it then attempts to force the operation. For example, imagine you make changes to a file in the `vi` editor and then try to quit with `:q`, only to discover that the command fails. The `vi` editor doesn't want to quit without saving the changes you made to a file, but you can force it to quit with the ex command `:q!`.


**Consider This**

Although the ex mode offers several ways to save and quit, there's also `ZZ` that is available in command mode; this is the equivalent of `:wq`. There are many more overlapping functions between ex mode and command mode. For example, ex mode can be used to navigate to any line in the document by typing `:` followed by the line number, while the `G` can be used in command mode as previously demonstrated.

**Follow Along**

If you have a text file open, exit it by executing the `:q!` command. This will quit without saving changes.

