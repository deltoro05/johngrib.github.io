---
layout  : wiki
title   : git index
summary : 
date    : 2020-04-06 23:05:14 +0900
updated : 2022-01-16 13:49:51 +0900
tag     : git
toc     : true
public  : true
parent  : [[/git]]
latex   : true
---
* TOC
{:toc}

## git index란 무엇인가?

Git 사용자 매뉴얼을 읽어보자.[^user-manual-3370]

>
The index is a binary file (generally kept in `.git/index`) containing a sorted list of path names,
each with permissions and the SHA-1 of a blob object; git-ls-files can show you the contents of the index:

- 인덱스는 하나의 바이너리 파일이다
    - 보통 `.git/index`.
- 인덱스는 다음 항목을 포함한다.
    - 각 파일과 디렉토리의 정렬된 path name들
    - 각 파일과 디렉토리의 permission
    - blob 객체의 SHA-1 값

`git ls-files` 명령을 사용하면 인덱스의 내용물을 볼 수 있다.

```
$ git ls-files --stage | tail
100644 d344d060ac0c5db0f9bb01c4f1ce7e0d156598b9 0	search.html
100644 f259c5a08dd5d121a34a000017cd197ea02dc90b 0	sitemap.xml
100755 764df0355bdab53e2362b2f821e6c649162694d5 0	start.sh
100644 c9712bd9af8e82846391e82f7c50077b095f87fc 0	tag.html
100755 bdfb10641d93f265a382b3014341a15c68e4b139 0	tool/find-orphan-post-img.sh
100755 537c62c2bb5465d7594f085f8cf4935cf07ac4c4 0	tool/fix-image-references.sh
100755 01433e92888c8ce58bb79792ef786aa58d1acfc9 0	tool/pre-commit
100755 95b19d9863b6ad564bf6208f719a2bcc657a9ffc 0	tool/save-images.sh
100755 e36c4a696d2e351dc0efcd40db81d87e7ef1fb11 0	tool/to-skeleton.sh
100644 50fe65a76cb17611bb041bd5d2cc517ec863323f 0	utterances.json
```

- 첫 번째 필드의 `100644`, `100755`는 타입과 권한을 의미한다.
    - `100644`: 일반 파일
    - `100755`: 실행 가능한 일반 파일
- 두 번째 필드는 SHA-1 값이다.
- 세 번째 필드는 stage number 이다.
    - 이 값은 보통 `0` 이며, 컨플릭트가 발생했을 경우 각 스테이지 넘버를 표현한다.
- 네 번째 필드는 path name 이다.

`ls-files`에 대한 자세한 내용은 `git ls-files --help`를 참고할 것.

## git index 의 세 가지 중요한 특성
### 인덱스를 통해 tree 객체를 만들 수 있다

>
$$1.$$ The index contains all the information necessary to generate a single (uniquely determined) tree object.  
For example, running git-commit generates this tree object from the index, stores it in the object database, and uses it as the tree object associated with the new commit.

- 인덱스에는 하나의 유니크한 tree 객체를 생성하는 데에 필요한 모든 정보가 들어있다.
- `git commit`명령을 실행하면 인덱스를 통해 tree 객체를 생성하고, 생성한 tree 객체를 object database에 저장하고, 새로운 commit 의 tree object로 사용한다.

### 인덱스는 tree 객체와 working tree 를 빠르게 비교할 수 있다

>
$$2.$$ The index enables fast comparisons between the tree object it defines and the working tree.  
It does this by storing some additional data for each entry (such as the last modified time).
This data is not displayed above, and is not stored in the created tree object, but it can be used to determine quickly which files in the working directory differ from what was stored in the index, and thus save Git from having to read all of the data from such files to look for changes.

- 인덱스는 각각의 엔트리에 대한 추가 정보를 저장해두고 있다.
- 이러한 데이터는 생성된 tree object에 저장되지 않지만 인덱스에 저장된 파일과 변경된 파일을 빠르게 판별할 수 있다.
    - 변경 사항을 찾아내기 위해 모든 파일을 다 찾지 않아도 된다.

### merge conflicts 정보를 효율적으로 표현할 수 있다

>
$$3.$$ It can efficiently represent information about merge conflicts between different tree objects, allowing each pathname to be associated with sufficient information about the trees involved that you can create a three-way merge between them.  
We saw in `<<conflict-resolution>>` that during a merge the index can store multiple versions of a single file (called "stages").  The third column in the git-ls-files output above is the stage number, and will take on values other than 0 for files with merge conflicts.  
The index is thus a sort of temporary staging area, which is filled with a tree which you are in the process of working on.  
If you blow the index away entirely, you generally haven't lost any information as long as you have the name of the tree that it described.

- 서로 다른 tree object 간의 merge conflicts에 대한 정보를 효율적으로 표시 할 수 있다.
- 따라서 각 pathname과 관련 트리에 대한 정보와 연결하여 3 way merge를 생성할 수 있다.
- `<<conflict-resolution>>`에서, 머지 과정 중에 인덱스가 하나의 파일의 여러 버전을 저장할 수 있음을 보았다.
- `git ls-files` 명령의 출력에서 3번째 열은 스테이지 번호이고, conflict가 있는 경우 0 이 아닌 값을 사용한다.
- 인덱스는 임시 스테이징 공간이며, 작업중인 tree 로 채워져 있다.
- 만약 index를 완전히 날려버려도, tree 이름만 갖고 있다면 어떤 정보도 손실되지는 않는다.

## 참고문헌

- [Git 사용자 매뉴얼][user-manual-3370]

## 주석

[^user-manual-3370]: [Git 사용자 매뉴얼][user-manual-3370]
[user-manual-3370]: https://github.com/git/git/blob/9fadedd637b312089337d73c3ed8447e9f0aa775/Documentation/user-manual.txt#L3370

