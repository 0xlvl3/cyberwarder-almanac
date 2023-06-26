# FFUF cheatsheet

Links:

https://github.com/ffuf/ffuf
https://github.com/ffuf/ffuf/wiki

--

## Use case:

- FFUF (Fast web fuzzer) used for web application fuzzing. Fuzzing is aa technique that involves sending a large number of varied inputs
  to a target application to identify potential vulnerabilities or uncover hidden information.

--

## Common flags:

| Flag         | Meaning                                                 |
| ------------ | ------------------------------------------------------- |
| -u           | Target URL to fuzz                                      |
| -w           | Wordlist containing fuzzing payloads                    |
| -H           | Set custom header in request                            |
| -c           | Enables colourized output                               |
| -t           | Sets number of concurrent threads (default 40)          |
| -o           | specifies the output file to save the results           |
| -timout      | Sets the request timeout duration (default: 10 seconds) |
| -fs          | Filters responses based on the HTTP status code         |
| -maxfilesize | Sets the maximum allowed response size to save          |

--

## Common Word Lists:

OneListForAll: https://github.com/six2dez/OneListForAll
Specific wordlists: https://github.com/danielmiessler/SecLists

### 1. Subdomains and Virtual Hosts:

    - subdomains-top1million-500.txt
    - subdomains-top1million-20000.txt
    - namelist.txt
    - small.txt

### 2. Common Web Paths and Directories

    - directory-list-2.3-medium.txt
    - directory-list-2.3-small.txt

### 3. Usernames and Passwords

    - usernames-top100.txt
    - passwords-top100.txt
    - rockyou.txt

--

## Commands:

### Basic Fuzzing

```
ffuf -u $TARGETURL -w $WORDLIST

```

### Virtual Host Fuzzing Command

- Should use vhosts list

```
ffuf -w ./vhosts -u http://$IPADDRESS -H "HOST: FUZZ.$TARGET" -fs $CODE

```

###
