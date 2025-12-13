```shell
export, env, $PATH, source, set, ($(())), 
arr=(a b c), ${arr[@]}, ${arr[*]}, $?
which
#!/usr/bin/bash
seq
[[ -n -z "$STRING"]]

```
- bash(1) PROMPTING, EXPANSION, errno, test
- shebang, variable , {shell/env} var,, types {string/numeric/array}
- , common substitution, arithmetic expansion, 
- {single/double} string, suppress [globbing, shell expansion], suppress [command, variable] substitution
* **Parameter expansion** (`${variable}`).
* **Command substitution** (`$(command)`).
* **Arithmetic expansion** (`$((expression))`).
* **Brace expansion** (`{A,B,C}`).
* **Array indexing** (`${array[index]}`).
TODO: 30
- `/etc/profile`, `/etc/bash.bashrc`
- exit code, [numeric comparison, string comparison, string unary]
---

Bash arrays are just a list of individual variables. This means there are no optimizations like memory resizing or pre-allocating space, which you might find in more sophisticated data structures in other languages. As a result, arrays in Bash are simple and not as flexible or efficient as in other languages.

arr=("apple" "banana" "cherry")

# Using [@]
for element in "${arr[@]}"; do
  echo "$element"
done

# Using [*]
for element in "${arr[*]}"; do
  echo "$element"
done
