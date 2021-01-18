[TOC]

# 搜索功能

## 找文件

1. 点击Go to file
2. 输入文件名或文件路径

## 找仓库

| Qualifier                   | Example                                                      |
| :-------------------------- | :----------------------------------------------------------- |
| `in:name`                   | [**jquery in:name**](https://github.com/search?q=jquery+in%3Aname&type=Repositories) matches repositories with "jquery" in the repository name. |
| `in:description`            | [**jquery in:name,description**](https://github.com/search?q=jquery+in%3Aname%2Cdescription&type=Repositories) matches repositories with "jquery" in the repository name or description. |
| `in:readme`                 | [**jquery in:readme**](https://github.com/search?q=jquery+in%3Areadme&type=Repositories) matches repositories mentioning "jquery" in the repository's README file. |
| `repo:owner/name`           | [**repo:octocat/hello-world**](https://github.com/search?q=repo%3Aoctocat%2Fhello-world) matches a specific repository name. |
| `user:*USERNAME*`           | [**user:defunkt forks:>100**](https://github.com/search?q=user%3Adefunkt+forks%3A>%3D100&type=Repositories) matches repositories from @defunkt that have more than 100 forks. |
| `org:*ORGNAME*`             | [**org:github**](https://github.com/search?utf8=✓&q=org%3Agithub&type=Repositories) matches repositories from GitHub. |
| `size:*n*`                  | [**size:1000**](https://github.com/search?q=size%3A1000&type=Repositories) matches repositories that are 1 MB exactly. （:n :>n :<n :n..m)[Understanding the search syntax](https://docs.github.com/en/free-pro-team@latest/github/searching-for-information-on-github/understanding-the-search-syntax). |
| `followers:*n*`             | [**node followers:>=10000**](https://github.com/search?q=node+followers%3A>%3D10000) matches repositories with 10,000 or more followers mentioning the word "node". |
| `forks:*n*`                 | [**forks:5**](https://github.com/search?q=forks%3A5&type=Repositories) matches repositories with only five forks. |
| `stars:*n*`                 | [**stars:500**](https://github.com/search?utf8=✓&q=stars%3A500&type=Repositories) matches repositories with exactly 500 stars. |
| `created:*YYYY-MM-DD*`      | [**webos created:<2011-01-01**](https://github.com/search?q=webos+created%3A<2011-01-01&type=Repositories) matches repositories with the word "webos" that were created before 2011. |
| `pushed:*YYYY-MM-DD*`       | [**css pushed:>2013-02-01**](https://github.com/search?utf8=✓&q=css+pushed%3A>2013-02-01&type=Repositories) matches repositories with the word "css" that were pushed to after January 2013. |
| `language:*LANGUAGE*`       | [**rails language:javascript**](https://github.com/search?q=rails+language%3Ajavascript&type=Repositories) matches repositories with the word "rails" that are written in JavaScript. |
| `topic:*TOPIC*`             | [**topic:jekyll**](https://github.com/search?utf8=✓&q=topic%3Ajekyll&type=Repositories&ref=searchresults) matches repositories that have been classified with the topic "jekyll." |
| `topics:*n*`                | [**topics:5**](https://github.com/search?utf8=✓&q=topics%3A5&type=Repositories&ref=searchresults) matches repositories that have five topics. |
| `license:*LICENSE_KEYWORD*` | [**license:apache-2.0**](https://github.com/search?utf8=✓&q=license%3Aapache-2.0&type=Repositories&ref=searchresults) matches repositories that are licensed under Apache License 2.0. |
| `mirror:true`               | [**mirror:true GNOME**](https://github.com/search?utf8=✓&q=mirror%3Atrue+GNOME&type=) matches repositories that are mirrors and contain the word "GNOME." |
| `archived:true`             | [**archived:true GNOME**](https://github.com/search?utf8=✓&q=archived%3Atrue+GNOME&type=) matches repositories that are archived and contain the word "GNOME. |

## 找主题

| Qualifier              | Example                                                      |
| :--------------------- | :----------------------------------------------------------- |
| `is:curated`           | [**is:curated javascript**](https://github.com/search?utf8=✓&q=javascript+is%3Acurated&type=Topics) matches topics that are curated and contain the word "javascript." |
| `is:featured`          | [**is:featured javascript**](https://github.com/search?utf8=✓&q=javascript+is%3Afeatured&type=Topics) matches topics that are featured on https://github.com/topics/ and contain the word "javascript." |
| `is:not-curated`       | [**is:not-curated javascript**](https://github.com/search?utf8=✓&q=javascript+is%3Anot-curated&type=Topics) matches topics that don't have extra information, such as a description or logo, and contain the word "javascript." |
| `is:not-featured`      | [**is:not-featured javascript**](https://github.com/search?utf8=✓&q=javascript+is%3Anot-featured&type=Topics) matches topics that aren't featured on https://github.com/topics/ and contain the word "javascript." |
| `repositories:n`       | [**repositories:>5000**](https://github.com/search?q=repositories%3A>5000) matches topics that have more than 5000 repositories. |
| `created:*YYYY-MM-DD*` | [**Serverless created:>2019-01-01**](https://github.com/search?q=Serverless+created%3A>2019-01-01&type=Topics) matches topics with the word "serverless" that were created after 2018. |

## 找代码

| Qualifier | Example                                                      |
| :-------- | :----------------------------------------------------------- |
| `in:file` | [**octocat in:file**](https://github.com/search?q=octocat+in%3Afile&type=Code) matches code where "octocat" appears in the file contents. |
| `in:path` | [**octocat in:path**](https://github.com/search?q=octocat+in%3Apath&type=Code) matches code where "octocat" appears in the file path. |
|                              |                                                              |
| `user:*USERNAME*`            | [**user:defunkt extension:rb**](https://github.com/search?q=user%3Agithub+extension%3Arb&type=Code) matches code from @defunkt that ends in *.rb*. |
| `org:*ORGNAME*`              | [**org:github extension:js**](https://github.com/search?utf8=✓&q=org%3Agithub+extension%3Ajs&type=Code) matches code from GitHub that ends in *.js*. |
| `repo:*USERNAME/REPOSITORY*` | [**repo:mozilla/shumway extension:as**](https://github.com/search?q=repo%3Amozilla%2Fshumway+extension%3Aas&type=Code) matches code from @mozilla's shumway project that ends in *.as*. |
| `path:/` | [**octocat filename:readme path:/**](https://github.com/search?utf8=✓&q=octocat+filename%3Areadme+path%3A%2F&type=Code) matches *readme* files with the word "octocat" that are located at the root level of a repository. |
| `path:*DIRECTORY*` | [**form path:cgi-bin language:perl**](https://github.com/search?q=form+path%3Acgi-bin+language%3Aperl&type=Code) matches Perl files with the word "form" in a *cgi-bin* directory, or in any of its subdirectories. |
| `path:*PATH/TO/DIRECTORY*` | [**console path:app/public language:javascript**](https://github.com/search?q=console+path%3A"app%2Fpublic"+language%3Ajavascript&type=Code) matches JavaScript files with the word "console" in an *app/public* directory, or in any of its subdirectories (even if they reside in *app/public/js/form-validators*). |
| `language:*LANGUAGE*` | [**element language:xml size:100**](https://github.com/search?q=element+language%3Axml+size%3A100&type=Code) matches code with the word "element" that's marked as being XML and has exactly 100 bytes. |
| `size:*n*` | [**function size:>10000 language:python**](https://github.com/search?q=function+size%3A>10000+language%3Apython&type=Code) matches code with the word "function," written in Python, in files that are larger than 10 KB. |
| `filename:*FILENAME*` | [**filename:linguist**](https://github.com/search?utf8=✓&q=filename%3Alinguist&type=Code) matches files named "linguist."                                    [filename:.vimrc commands](https://github.com/search?q=filename%3A.vimrc+commands&type=Code) matches *.vimrc* files with the word "commands." |
| `extension:*EXTENSION*` | [**form path:cgi-bin extension:pm**](https://github.com/search?q=form+path%3Acgi-bin+extension%3Apm&type=Code) matches code with the word "form," under *cgi-bin*, with the *.pm* file extension. |
|  | [** icon size:>200000 extension:css**](https://github.com/search?utf8=✓&q=icon+size%3A>200000+extension%3Acss&type=Code) matches files larger than 200 KB that end in .css and have the word "icon." |



## 找提交

## 找issues和pull requests
按id搜索issues
https://github.com/axios/axios/issues/:id

## 找讨论

## 找用户

## 找pageages

## 找wikis

## 参考
- [github Docs](https://docs.github.com/en/free-pro-team@latest/github/searching-for-information-on-github/searching-issues-and-pull-requests#search-for-linked-issues-and-pull-requests)
