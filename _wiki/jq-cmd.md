---
layout  : wiki
title   : jq 명령어
summary : 
date    : 2020-03-10 23:04:14 +0900
updated : 2020-03-10 23:06:24 +0900
tag     : bash command
resource: 47/66F402-E5AE-4365-9F9F-7660D7952777
toc     : true
public  : true
parent  : [[cmd]]
latex   : false
---
* TOC
{:toc}

## Examples
```sh
 # json 을 파싱해 보여준다
cat test.json | jq

 # 모든 키 값의 패스를 `.`으로 조인해 보여준다
cat test.json | jq -c 'path(..)|[.[]|tostring]|join(".")'
```
