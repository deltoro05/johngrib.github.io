---
layout  : wiki
title   : MacTeX를 설치해 보자
summary : 
date    : 2019-05-25 09:42:51 +0900
updated : 2021-07-24 14:55:02 +0900
tag     : 
resource: CA/A7F899-FE40-4E63-B530-027EC3FC4FCF
toc     : true
public  : true
parent  : [[index]]
latex   : false
---
* TOC
{:toc}

MacTeX는 다음 경로에서 다운로드받을 수 있다.

<https://tug.org/mactex/ >

필요한 용량은 6.9GB 정도.

이후 다음과 같이 KTUG 사설 저장소를 추가해 준다.

```sh
$ sudo tlmgr repository add http://ftp.ktug.org/KTUG/texlive/tlnet ktug
$ sudo tlmgr pinning add ktug "*"
```

잘 추가됐는지 다음과 같이 확인할 수 있다.

```
$ tlmgr pinning show
```


TeXLive를 업데이트한다.

```sh
$ sudo tlmgr update --all --self
```

시키는대로 폰트도 다운받는다.

```sh
$ sudo tlmgr install nanumttf hcr-lvt
```


## 참고

* [설치하기MacOSX/Mac TeX](http://wiki.ktug.org/wiki/wiki.php/%EC%84%A4%EC%B9%98%ED%95%98%EA%B8%B0MacOSX/MacTeX )
