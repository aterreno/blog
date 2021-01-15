---
title: "Bash Leanings"
description: ""
date: "2014-01-10T17:42:18.000Z"
categories: []
published: true
canonical_link: https://javame.netlify.app//bash-learnings-7728c7169141
redirect_from:
  - /bash-learnings-7728c7169141
---

I recently refactored a pretty large and complex set of bash scripts.

I think Ruby influenced my Bash coding style quite a lot.

Here’s a list of some of the patterns I’ve followed.

#### Have a basedir variable available

```bash
script\_base="\`dirname "$0"\`"  
```

**S**eparation of concerns

Write loosely couple bash code in separate files, import them by doing:

```bash
. $script\_base/utils/colors.sh  
```

#### Avoid global state

Limit as much as possible global state (variables), they are evil in any language  

```bash
export PATH=/usr/pkg/sbin:/usr/pkg/bin:$PATH  
```  
Is my one and only export and ‘public’ variable in the script

#### Separation of concerns

Write independent, small functions

```bash  
\# Utility function to retrive configuration properties, uses jq   
function get\_config {   
 local environment=$1 local config=$2  
 jq -r ".$environment.$config" config.json  
}  
```

#### Documentation

Document your functions, sadly Bash doesn’t allow named params, so it’s pretty hard to figure out what a function takes.

#### Scope

Leverage local scope: Use [local variables](http://tldp.org/LDP/abs/html/localvar.html)

#### Principle Of Least Astonishment

Check error codes often and offer meaningful log messages

```bash  
\# Checks the return code of the last command run and outputs error / exit if not nil  
function check\_error {   
 if [ $? -ne 0 ];   
 then   
 error "[ERR] $1"   
 exit 1   
 fi   
}  
```

#### User interaction

Use colours, Bash is fun with colours  

```bash  
function error {   
 echo "$(tty -s &amp;&amp; tput setaf 1)$1$(tty -s &amp;&amp; tput sgr0)"   
}

function ok {   
 echo "$(tty -s &amp;&amp; tput setaf 2)$1$(tty -s &amp;&amp; tput sgr0)"   
}

function warn {   
 echo "$(tty -s &amp;&amp; tput setaf 3)$1$(tty -s &amp;&amp; tput sgr0)"   
}  
```

#### Defensive coding

Check error codes properly also when you run remote scripts

```bash  
\# Runs a command on remote ssh  
function ssh\_exec {   
 local remote\_user=$1   
 local remote\_command=$2   
 local results

results=$(ssh -T -q "$remote\_user" "$remote\_command")  
 if [ $? -ne 0 ];   
 then   
 log "remote code execution return: $?"   
 log "remote code execution output: $results"  
 error "[ERR] Failed running remote command: $remote\_command"  
 exit 1  
 fi   
}  
```

#### In Conclusion

Don’t underestimate Bash, it’s an awesome, Turing Complete language and requires no installation.

When the code starts to get too nasty, use your favourite scripting language!
