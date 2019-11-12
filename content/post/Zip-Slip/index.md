---
title: 'What is Zip Slip?'
subtitle: ''
summary: Create a beautifully simple website in under 10 minutes.
authors:
- admin
tags:
- security
- vulnerability 
- exploit 

categories:

date: "2018-09-20T10:00:00Z"
lastmod: "2019-10-17T00:00:00Z"
featured: false
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Placement options: 1 = Full column width, 2 = Out-set, 3 = Screen-width
# Focal point options: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight
image:
  placement: 2
  caption: 'Zip Slip'
  focal_point: ""
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []
---



Zip Slip was a vulnerability found in the file extraction mechanism employed in programming languages. It was discovered and responsibly disclosed by the Snyk Security team ahead of a public disclosure on 5th June 2018, and affected thousands of projects, including ones from HP, Amazon, Apache, Pivotal. The vulnerability is prevalent in Java, where there is no central library offering high level processing of archives. It was also observed in Go & Python. Zip slip caused havoc on its public disclosure. Zip Slip allowed for remote code execution, thereby granting shell privileges to an adversary. The vulnerability can affect other formats like `tar`, `jar`, `war`,`cpio`,`apk`,`rar` etc.

Consider a zip file (`foo.zip`) with two files bundled in it - `foo.text` and `bar.text`

```
chaitanya@zipslip$ zip -sf foo.zip
Archive contains:
  foo.text
  bar.text
Total 2 entries (100 bytes)
```

The -sf flag scans for files and lists the contents of the archive. However, if a maliciously crafted file is bundled in the zip, and if it is improperly handled during extraction then it may lead to severe problem like remote code execution.

Consider a zip file (`malicious.zip`) with two files (one is the RCE shell script and the other is an ordinary text file)

```
chaitanya@zipslip$ zip -sf malicious.zip 
Archive contains:
  foo.text
  ../../../../../../../../../tmp/rce.sh
Total 2 entries (560 bytes)
```

As soon as this zip is extracted, foo.text would be extracted within the same folder as of the zip file. However, `rce.sh` would be extracted to the tmp folder. The `../../` part before the file name ensures that the file path eventually hits / if it is within a subdirectory of high depth, and then stores the rce.sh file to the tmp folder. Now, a simple mechanism to execute this shell script would lead to remote code execution. This can overwrite configuration files on the system as well. Usually web applications that deal with zip file uploads rely on the file handling APIs native to a programming language.

Consider this Java code snippet,

```
1   Enumeration<ZipEntry> entries = zip.getEntries();
2   while (entries.hasMoreElements()) {
3      ZipEntry e = entries.nextElement();
4      File f = new File(destinationDir, e.getName());
5      InputStream input = zip.getInputStream(e);
6      IOUtils.copy(input, write(f));
7   }
```

On line 4, `e.getName()` is concatenated with the target directory, `dir`, without being validated. At this point, when the zip archive gets to `rce.sh`, it will append the full path (including every `../`) of the zip entry to the target directory resulting in `rce.sh` being written outside of the target directory.