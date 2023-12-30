## Print the contents of /etc/passwd file in the following format

root:x:0:0:root:/root:/bin/bash

```
Username: root
    Password: x
    UserID: 0
    GroupID: 0
    Comment: root
    HomeDirectory: /root
    DefaultShell: /bin/bash
```

<details>
    <summary>Solution</summary>

```bash
OLDIFS="$IFS"
IFS=':'
while read u p i g c d s ; do
    echo -e "Username: $u\n \tPassword: $p\n \tUserID: $i\n \tGroupID: $g\n \tComment: $c\n \tHomeDirectory: $d\n \tLoginShell: $s"
done < /etc/passwd
IFS="$OLDIFS"
```

</details>