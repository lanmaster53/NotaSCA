Right now this is just an idea. While I have some local files that I use for this, the repo itself is a placeholder until I determine whether or not it is a useful idea given the existence of YASCA.

# NotaSCA

Not Another SCA (NotaSCA) is a set of lists containing interesting regular expressions for searching code for security issues. Think FuzzDB for SCA. Like FuzzDB, which claims to be an "application security scanner, without the scanner," NotaSCA aims to be a "source code security scanner, without the scanner." Although, I will more than likely develop and include a Python scanning engine as well for those that don't want to take the time to wrap the lists in something of their own. But that's the beauty of it. Flexibility.

## Why Not YASCA?

Yes, I know YASCA does this too (and pretty well I might add), but here are a couple reasons why I'm not a fan of YASCA:

1. Creating/using plugins is too complex.
2. Hosted on sourceforge. (Ick.)
3. Written in PHP. (Come on now. It's 2016.)
4. Last code update was in 2013. (That's like 7 eons in appsec.)
5. Last official release was in 2010. (That pretty much makes it a dead project.)

## Usage

General guidelines for using the lists:

1. Account for comments (inline and complete-line).
2. Process each rule (line) as a regex.

Each line can contain a comment after the regular expression. This comment should be used to comment on the purpose of the given regex. This allows the scanning engine to use this comment as metadata, while not complicating how signatures are created and used.

Some options for usage:

```
for i in $(cat general.txt | egrep -v "(^#.*|^$)" | cut -d"#" -f1 | tr -d " \t"); do grep -IR $i .; done
```
