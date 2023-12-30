## grep

### Prints lines that match patterns

<details>
<summary>Count the number of lines in a file using grep?</summary>

```bash
grep -c '' /etc/services
```   
</details>

<details>
<summary>Print all lines in a file that do not start with a comment or is an empty line</summary>

```bash
grep -vE '^(#|$)' /etc/ssh/ssh_config
```
</details>

<details>
<summary>What is the use of -E option?</summary>

Used for passing Enhanced Regular Expression instead of a Basic Regular Expression

</details>

<details>
<summary>Print only filenames where a match has been found</summary>

```bash
$ grep -l 'pam_motd' /etc/pam.d/*
/etc/pam.d/login

$ grep 'pam_motd' /etc/pam.d/*

/etc/pam.d/login:session    optional   pam_motd.so motd=/run/motd.dynamic
/etc/pam.d/login:session    optional   pam_motd.so noupdate
```

_Note: The path in the output can be relative or absolute depending on whether the path argument was relative or absolute_

```bash
$ cd /etc/pam.d/

$ grep 'pam_motd' ./*

./login:session    optional   pam_motd.so motd=/run/motd.dynamic
./login:session    optional   pam_motd.so noupdate

$ grep -l 'pam_motd' ./*
./login
```

</details>