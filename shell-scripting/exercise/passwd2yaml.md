## Print the /etc/passwd file as a yaml file

### Sample Output

```
users: 
  - user: root
    passwd: x
    uid: 0
    gid: 0
    comment: root
    HomeDirectory: /root
    LoginShell: /bin/bash
  - user: daemon
    passwd: x
    uid: 1
    gid: 1
    comment: daemon
    HomeDirectory: /usr/sbin
    LoginShell: /usr/sbin/nologin
...

```

<details>
<summary>Solution</summary>

```bash
awk -f passwd2yml.awk /etc/passwd
```

passwd2yml.awk
```
BEGIN {
    FS=":";
    print "users: "
}

{
    printf "  %s%s\n    %s%s\n    %s%s\n    %s%s\n    %s%s\n    %s%s\n    %s%s\n", "- user: ",$1, "passwd: ",$2, "uid: ", $3, "gid: ", $4,"comment: ", $5,"HomeDirectory: ", $6,"LoginShell: ", $7;
}
```
</details>


### Now print records for root and mail users as yaml

<details>
<summary>Solution</summary>

```
BEGIN {
    FS=":";
    print "users: "
}

/root|mail/ {
    printf "  %s%s\n    %s%s\n    %s%s\n    %s%s\n    %s%s\n    %s%s\n    %s%s\n", "- user: ",$1, "passwd: ",$2, "uid: ", $3, "gid: ", $4,"comment: ", $5,"HomeDirectory: ", $6,"LoginShell: ", $7;
}
```

</details>

### Try to variablize the pattern so as to make it work for any user

<details>
<summary>Solution</summary>

```bash
# We can pass variables to the awk command with the -v option
awk -v pattern="ubuntu|root" -f passwd2yml.awk /etc/passwd
```

```
BEGIN {
    FS=":";
    print "users: "
}

# Check if the row matches the pattern.
$0 ~ pattern {
    printf "  %s%s\n    %s%s\n    %s%s\n    %s%s\n    %s%s\n    %s%s\n    %s%s\n", "- user: ",$1, "passwd: ",$2, "uid: ", $3, "gid: ", $4,"comment: ", $5,"HomeDirectory: ", $6,"LoginShell: ", $7;
}
```