---
layout  : wiki
title   : vim quickfix
summary : 
date    : 2022-04-15 22:20:55 +0900
updated : 2022-04-15 23:48:40 +0900
tag     : vim quickfix clojure
toc     : true
public  : true
parent  : [[/vim]]
latex   : false
---
* TOC
{:toc}

## help

`:help quickfix` 로 볼 수 있다.

## 커스터마이즈

[vim-togglelist]( https://github.com/milkypostman/vim-togglelist )를 사용해 다음과 같이 토글하고 있다.

```viml
" quickfix 열기/닫기 토글
nnoremap <Tab>ql :call ToggleLocationList()<CR>
nnoremap <Tab>qq :call ToggleQuickfixList()<CR>
```

`:cnext`, `:cprevious` 입력은 귀찮은 일이기 때문에 이렇게 설정해 뒀다.

```viml
" quickfix 다음/이전 이동
nnoremap <Tab>qn :cnext<CR>
nnoremap <Tab>qN :cprevious<CR>
```

## 응용

### Clojure clj-kondo lint report

[[/clojure/vim-setting#clj-kondo로-lint-하기]]

### 프로젝트 bookmark

아이디어는 다음과 같았다.

- 각 파일에 대한 즐겨찾기를 개별 파일로 저장하고 싶다.
    - `${pwd}/.bookmark` 같은 파일을 만들어서 vim 세션별로 관리하도록 하자.
- quickfix 기능을 사용하자.
    - 버퍼/윈도우 관리용 코드를 안 짜도 된다.
    - `.bookmark`는 `파일명:행번호:열번호 메모` 형식의 행들로 이루어진 순수한 텍스트 파일이 되도록 한다.
    - 따라서 `:cfile .bookmark`로 열면 퀵픽스 창으로 열리고, 퀵픽스 기능을 사용할 수 있다.
- plain text 파일로 저장한다.
    - 그러므로 그냥 열어서 편집도 가능하다.
    - `gF`, `gf`로 파일을 쉽게 열 수 있다.
    - url이면 `gx`로 웹 브라우저도 바로 열 수 있다.

#### 구현

[QuickFixBookMark 작업]( https://github.com/johngrib/dotfiles/commit/8c792ea4ea094019ffc59a08daf38d426d18657c )

```viml
" 현재 커서가 있는 라인을 북마크 파일에 저장합니다.
function! AddQuickfixBookmarkFile()
    let l:pwd = getcwd()
    let l:file = l:pwd . '/.quickfix-bookmark'
    let l:bookmark = expand("%:p").":".line(".").": ".expand("<cword>")
    echom l:bookmark
    call system("echo '" . l:bookmark . "' >> " . l:file)
endfunction

nnoremap <Tab>qm :call AddQuickfixBookmarkFile()<CR>
```

- 북마크 파일에 내용을 추가하는 기능.
    - PWD에 `.quickfix-bookmark` 파일을 생성한다.
    - vim session이 자동으로 PWD를 관리해주므로 이렇게 하면 프로젝트 루트에 생성된다.
    - 새로운 내용은 `quickfix-bookmark` 파일의 마지막 줄에 추가된다.
- `<Tab>qm`을 순서대로 입력해 사용할 수 있다. (`m`: mark)
    - `m`은 `normal m`을 의식한 것이다.

```viml
" 북마크 파일을 편집합니다. 메모를 추가하는 등의 용도로 사용하세요.
" 편집 화면에서도 gf, gF 를 사용해 해당 파일의 해당 라인으로 점프할 수 있습니다.
function! EditQuickfixBookmarkFile()
    let l:pwd = getcwd()
    let l:file = l:pwd . '/.quickfix-bookmark'
    execute "vs " . l:file
endfunction

nnoremap <Tab>qe :call EditQuickfixBookmarkFile()<CR>
```

- 북마크 파일을 편집할 수 있게 열어주는 기능.
    - 메모를 추가하거나, 삭제하거나, 직접 적어 추가하거나, 수정할 수 있다.
    - `gf`, `gF`, `gX`도 사용할 수 있다.
- `<Tab>qe`를 순서대로 입력해 사용할 수 있다. (`e`: edit)
    - `e`은 `:edit`를 의식한 것이다.

```viml
" 북마크 파일을 퀵픽스 창에 열어줍니다.
" 퀵픽스 기능을 사용해 다음 파일, 이전 파일로 이동할 수 있습니다.
function! OpenQuickfixBookmarkFile()
    let l:pwd = getcwd()
    let l:file = l:pwd . '/.quickfix-bookmark'
    execute "cfile " . l:file
    copen
endfunction

nnoremap <Tab>q' :call OpenQuickfixBookmarkFile()<CR>
nnoremap <Tab>q` :call OpenQuickfixBookmarkFile()<CR>
```

- 북마크 파일을 소스로 삼아 퀵픽스 창을 열어준다.
- `<Tab>q'`를 순서대로 입력해 사용할 수 있다. (`'`: Jump to the mark)

## 함께 읽기

- [[/clojure/vim-setting]]

