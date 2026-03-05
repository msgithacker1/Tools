---
description: A how-to for bash scripting to help automate processes in Linux.
---

# Bash Scripting

## Intro:

* Bash means "Bourne Again Shell" and is a Linux command interpreter. It executes Linux commands when typed in a terminal.&#x20;
* A bash script is just a text file full of those commands that runs in one go instead of one-by-one typing.&#x20;
* Bash scripting is used in Linux to help automate repetitive processes for improved efficiency of pentesting.
* This page will go over syntax for .sh scripting, how to execute with parameters, benefits and more.

***

## Core Syntax:

* The Shebang:

```bash
#!/bin/bash
```

{% hint style="info" %}
This is always the first line. It tells the kernel to use the Bash interpreter to run the file - readable even with the comment sign (#).
{% endhint %}

* Variables:

```bash
name="target"
ip="192.168.0.1"
```

{% hint style="info" %}
You just create a variable name following naming conventions and assign it to a value.
{% endhint %}

* Printing:

```bash
echo $name
echo "Scanning $ip"
```

{% hint style="info" %}
Prints information to the console whilst the script is running. The use of the ($) sign means it's a variable and the variable is being **read (not created)**. it will be interpreted as a variable because bash allows variable expansion with double quotes so it won't literally be interpreted as part of the string.
{% endhint %}

* User Input:

<pre class="language-bash"><code class="lang-bash"><strong>read -p "Enter user input: " ip
</strong>
read -sp "Enter hidden user input: " pass


# The -s switch hides the input from being seen on the screen.
# In the script, use the variables as $ip or $pass, for example.
</code></pre>

{% hint style="info" %}
The words after the user input part become the variable that the user input is assigned to. These variables are being created/set so they don't require a ($) sign before them.&#x20;
{% endhint %}

* Conditionals:

```bash
if [[ $ip == "192.168.0.1" ]]; then
    echo "That's the gateway"
elif [[ $ip == "10.0.0.1" ]]; then
    echo "That's a different subnet"
else 
    echo "Unknown"
fi

# bash requires spaces after [[ and before ]].
# Use [[ and ]] when you're doing a comparison. E.g., when checking if a variable is equal to a string.

# && is the AND operator. || would be the OR operator.
# You can use a command that would evaluate to True/False as a conditional.
# Don't put [[]] around these kinds of commands. 
# -q was used here to prevent the output of the grep command being printed to the console (explained later).
```

{% hint style="info" %}
This is an example of an if statement in bash scripting. The conditional clause starts and ends with \[]. The comparison operator (==) is used. The conditional ends with a (;) sign. The whole if statement ends with "fi" to signal the end.&#x20;
{% endhint %}

* Loops:

```bash
# A for loop example
for i in {1..254}; do
    echo "192.168.0.$i"
done

# A while loop example
while true; do
    echo "running..."
done
```

{% hint style="info" %}
For the for loop, the range is given like {\[start value] .. \[end value]} and again ends with a (;) (also after the condition for the while loop). A "do" keyword is used to decide the action to undertake in the loops. Both loops end with a "done" keyword to signify the end of the loop.
{% endhint %}

* Functions:

```bash
scan() {
    echo "Scanning $1"
    nmap -sV $1
}
scan 192.168.0.1

# Define the function at the start or bash won't know it exists when you call it later
```

{% hint style="info" %}
The passing of $1 here signifies that whatever value was assigned to the $1 variable was the first argument passed to the function. The value for this variable can be set elsewhere in the code.&#x20;
{% endhint %}

* Command output into a variable:

```bash
result=$(whoami)
ip=$(hostname -I)
echo "Running as: $result"
```

{% hint style="info" %}
The commands are written in () brackets and whatever result they return is stored inside the variables on the LHS. Again, these variables are being created so they don't need a ($) sign before them. The ($) sign before the commands tells bash to run the commands and then use its output as the value.&#x20;
{% endhint %}

* Command arguments passed to the script:

```bash
$0 # script name itself
$1 # first argument to the script
$2 # second argument to the script
$# # number of arguments

./script.sh 192.168.0.1 88

# $1 = 192.168.0.1, $2 = 80
```

* Store results to file:

```bash
nmap 192.168.0.1 > results.txt # > saves to the file and suppresses code output to console
nmap 192.168.0.1 >> results.txt # >> appends to the file and doesn't suppress code output to console
nmap 192.168.0.1 2> /dev/null # suppress errors 
```

* String tricks:

```bash
echo "hello" | tr 'a-z' 'A-Z' 

# | is a pipe. It takes the output of the LHS command and feeds it as input to the RHS command.
# tr - translate/replace characters. The output for above would be HELLO.

echo "192.168.0.1" | cut -d'.' -f1 
# Outputs 192
# -d specifies the delimiter (what to split on).
# -f specifies the field(s) to grab. Numbered from 1 onwards. This is saying keep the first field (i.e., the part before the first ".").
# This is basically saying cut the string at the decimal points and set each component to the fields.

grep "open" results.txt
# grep is used for searching for patterns. This command searches for and prints lines containing "open" inside the file. 
# -i switch with grep means case-sensitive searching.
# -v means inverted search. Return lines that don't contain "open".

grep -r "password" /var/www/
# -r means search recursively through a directory.
# It looks for the word "password" in every file inside the specified directory recursively.

sed 's/old/new/g' file.txt
# sed is used to find and replace in strings.
# This command replaces all occurrences.
# 's' means substitute and the 'g' means global - replace all occurrences not just the first.
# Here it means substitute all occurrences of "old" with "new" in file.txt and return it.
# The file itself doesn't actually change. You only see the modified output. 

grep -q "string" file.txt
# This is a condition that can be used within an if statement.
# The -q flag means "quiet" and doesn't return anything like grep usually would.
# Instead, this condition evaluates to True if the string "string" is found within file.txt.
# If you use this, or any other command, as a conditional in a conditional statement, don't put [] around it.
# Square brackets only apply for conditions not commands within conditions.

sed 's/old/new/g' file.txt > new_file.txt
# Same thing as above but it stores the output into new_file.txt 

# If you want to actually edit the file, use the -i flag. 

```
