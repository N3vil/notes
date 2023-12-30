## grep

<details>
    <summary>Count the number of lines in a file using grep?</summary>
    ```sh
    grep -c '' /etc/services
    ```
</details>

<details>
    <summary>Print all lines in a file that do not start with a comment or is an empty line</summary>
    ```sh
    grep -E '^(#|$)' /etc/ssh/sshd_config
    ```
</details>

<details>
    <summary>What is the use of -E option?</summary>
    Used for passing Enhanced Regular Expression instead of a Basic Regular Expression
</details>