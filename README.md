# Bash Snippets

> A collection of code snippets I found useful while coding in bash.

- [Array](#array)
- [Cli Flags](#cli-flags)
- [If Statements](#if-statements)
- [String](#string)

## Array

```bash
#!/bin/bash

declare -a FRUITS

# Declare an array as a space seperated list.
FRUITS=(grapefruit pineapple avocado)

echo "${FRUITS[@]}"

printf "There are %i fruits in the array." "${#FRUITS[@]}"

for FRUIT in "${FRUITS[@]}"
do

	echo "${FRUIT}"

done

SENTENCE="This is a sample sentence."

# Split string on spaces.
WORDS=("${SENTENCE// / }")

echo "${SENTENCE}"

for WORD in "${WORDS[@]}"
do

	echo "${WORD}"

done
```

## Cli Flags

```bash
#!/bin/bash

args=("${@// /}")

for arg in "${args[@]}"
do

    case $arg in

        -v | --version ) echo "Version flag."; exit;;
        -h | --help ) echo "Help flag."; exit;;

        ?* ) printf "Invalid option %s\n\n" "${arg}"; exit;;

    esac

done
```

## If Statements

```bash
#!/bin/bash

EMPTY=""

if [ -z "${EMPTY}" ]; then

    echo "Variable is empty."

fi

NUMBER=10

if [ "${NUMBER}" -gt 0 ]; then

    echo "Number is greater than 0."

fi

if [ "${NUMBER}" -lt 100 ]; then

    echo "Number is less than 100."

fi
```

## String

```bash
#!/bin/bash

# Replace a word in a string.
echo "This is just a test." | sed s/just/only/

# Replace a pattern in a string.
echo "1 is the loneliest number there will ever be." | sed s/[0-9]/One/

# Return pattern match in a string.
echo "There are (6) new items." | grep -o '[0-9]'
```
