# `ls`

## Description

The `ls` command by default _lists_ the files and directories inside the current working directory.

When given an argument, `ls <path>`, it prints the contents of the specified directory or a listing of the specified file. If the directory or file doesn't exist, it returns an error message.

The `ls` command accepts a number of options that modify its behaviour. For example:

- `ls -F` adds an indicator to the output to distinguish file types.
  - `/` indicates a directory.
  - `@` indicates a symbolic link.
  - `*` indicates an executable file.
- `ls -R` _recursively_ lists files and directories, including the contents of nested subdirectories.
- `ls -a` lists _all_ files and directories, including hidden ones. Hidden files start with `.` and are usually configuration files.
- `ls -l` lists files and directories in a _long_ listing format. It doesn't just show names, but also file details like permissions, ownership, size and the last modification date and time.
- `ls -h` when paired with `-l` lists file sizes in a _human-readable_ format (file sizes displayed in KB, MB, and so on, instead of just bytes).
- `ls -t` lists files sorted by modification _time_, instead of the default alphabetical order. The **newest appears first**.
- `ls -S` lists files and directories sorted by file _size_, instead of the default alphabetical order. The **largest appears first**.
- `ls -r` lists files and directories in _reverse_ order when sorting.

## Example

```sh
ls -F
```

```
notes.md  projects/
```

In the example above, `ls` on its own lists files and directories in the current working directory, and the `-F` option adds an indicator to the output. The `/` in `projects/` indicates that `projects` is a directory.

```sh
ls -F projects
```

```
backend-projects/  frontend-projects/  fullstack-projects/
```

Here, `ls` with the argument `projects` lists all files and directories in the `projects` directory. The `/` indicates that each of the listed items is a directory.

```sh
ls -R
```

```
notes.md  projects

./projects:
backend-projects  frontend-projects  fullstack-projects

./projects/backend-projects:
blog-platform-api  task-management-api

./projects/backend-projects/blog-platform-api:

./projects/backend-projects/task-management-api:

./projects/frontend-projects:
portfolio  weather-app

./projects/frontend-projects/portfolio:

./projects/frontend-projects/weather-app:

./projects/fullstack-projects:
e-commerce  social-media

./projects/fullstack-projects/e-commerce:

./projects/fullstack-projects/social-media:
```

In this example, `ls -R` first lists the contents of the current working directory (`notes.md` and `projects`). It then recursively lists the contents of each subdirectory, showing `backend-projects`, `frontend-projects`, and `fullstack-projects` inside `projects`, and the further nested directories within each of those.

```sh
ls -a
```

```
.  ..  .bash_history  .bash_logout  .bashrc  .cache  .lesshst  .profile  .python_history  .ssh  notes.md  projects
```

In this example, `ls -a` lists **all** files and directories in the current working directory, including hidden ones (files starting with `.`), such as `.bashrc`, `.bash_history` and `.ssh`. `.` refers to the current directory and `..` refers to the parent directory.

```sh
ls -alh
```

```
total 44K
drwxr-x--- 5 ubuntu ubuntu 4.0K Mar 31 12:57 .
drwxr-xr-x 3 root   root   4.0K Mar 28 15:05 ..
-rw------- 1 ubuntu ubuntu 2.2K Mar 31 14:19 .bash_history
-rw-r--r-- 1 ubuntu ubuntu  220 Mar 31  2024 .bash_logout
-rw-r--r-- 1 ubuntu ubuntu 3.7K Mar 31  2024 .bashrc
drwx------ 2 ubuntu ubuntu 4.0K Mar 28 15:05 .cache
-rw------- 1 ubuntu ubuntu   37 Mar 30 13:06 .lesshst
-rw-r--r-- 1 ubuntu ubuntu  807 Mar 31  2024 .profile
-rw------- 1 ubuntu ubuntu    7 Mar 31 11:35 .python_history
drwx------ 2 ubuntu ubuntu 4.0K Mar 28 15:05 .ssh
-rw-rw-r-- 1 ubuntu ubuntu    0 Mar 31 12:57 notes.md
drwxrwxr-x 5 ubuntu ubuntu 4.0K Mar 31 12:44 projects
```

Here, `ls -alh` lists all files and directories (including hidden ones) in the current working directory with detailed information. The file sizes are displayed in human-readable format (4.0K, 3.7K, 2.2K) making them easier to understand compared to the default byte count (4096, 3771, 2248).

```sh
ls -alhS
```

```
total 44K
drwxr-x--- 5 ubuntu ubuntu 4.0K Mar 31 12:57 .
drwxr-xr-x 3 root   root   4.0K Mar 28 15:05 ..
drwx------ 2 ubuntu ubuntu 4.0K Mar 28 15:05 .cache
drwx------ 2 ubuntu ubuntu 4.0K Mar 28 15:05 .ssh
drwxrwxr-x 5 ubuntu ubuntu 4.0K Mar 31 12:44 projects
-rw-r--r-- 1 ubuntu ubuntu 3.7K Mar 31  2024 .bashrc
-rw------- 1 ubuntu ubuntu 2.2K Mar 31 14:19 .bash_history
-rw-r--r-- 1 ubuntu ubuntu  807 Mar 31  2024 .profile
-rw-r--r-- 1 ubuntu ubuntu  220 Mar 31  2024 .bash_logout
-rw------- 1 ubuntu ubuntu   37 Mar 30 13:06 .lesshst
-rw------- 1 ubuntu ubuntu    7 Mar 31 11:35 .python_history
-rw-rw-r-- 1 ubuntu ubuntu    0 Mar 31 12:57 notes.md
```

Here, the `-S` option sorts files by size, with the **largest file appearing first**.

```sh
ls -alhtr
```

```
total 44K
-rw-r--r-- 1 ubuntu ubuntu  807 Mar 31  2024 .profile
-rw-r--r-- 1 ubuntu ubuntu 3.7K Mar 31  2024 .bashrc
-rw-r--r-- 1 ubuntu ubuntu  220 Mar 31  2024 .bash_logout
drwxr-xr-x 3 root   root   4.0K Mar 28 15:05 ..
drwx------ 2 ubuntu ubuntu 4.0K Mar 28 15:05 .ssh
drwx------ 2 ubuntu ubuntu 4.0K Mar 28 15:05 .cache
-rw------- 1 ubuntu ubuntu   37 Mar 30 13:06 .lesshst
-rw------- 1 ubuntu ubuntu    7 Mar 31 11:35 .python_history
drwxrwxr-x 5 ubuntu ubuntu 4.0K Mar 31 12:44 projects
-rw-rw-r-- 1 ubuntu ubuntu    0 Mar 31 12:57 notes.md
drwxr-x--- 5 ubuntu ubuntu 4.0K Mar 31 12:57 .
-rw------- 1 ubuntu ubuntu 2.2K Mar 31 14:19 .bash_history
```

In this example, `ls -alhtr` lists all files and directories (including hidden ones) in the current working directory in long format with human-readable files sizes sorted by modification time in reverse order. The most recently modified file is shown at the bottom of the list.
