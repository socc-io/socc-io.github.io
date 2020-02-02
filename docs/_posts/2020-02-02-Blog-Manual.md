---
title: "SOCC Tech Blog 사용법"
categories:
  - Jekyll
tags:
  - Jekyll
  - blog


last_modified_at: 2020-02-02T14:25:52-05:00
---

Jekyll로 운영 되는 github io 홈페이지에 포스팅을 올리는 방법에 대해 알아봅니다.

## Git Repository Clone 하기

일반적인 블로그에서 글을 쓰는 것과 달리, github page는 git repository에 블로그 내용을 작성하고, 커밋한 뒤, push하는 방식으로 글을 작성할 수 있습니다. 따라서, 먼저 github 페이지 repository를 자신의 local 컴퓨터에 clone 합니다.

## Github page를 자신의 컴퓨터로 호스팅 해보기

현재 블로그는 github에서 제공하는 서버에서 호스팅을 해 주고 있습니다. 하지만 저희가 블로그 글을 작성하고 수정할때, 글이 잘 작성되었는지 확인을 할때는 자신의 컴퓨터로 간단하게 localhost에 블로그를 띄운 뒤, 제대로 작성되었는지 확인하는 것이 더 편리합니다. 확인을 한 후 push 를 통해 github 서버로 호스팅 하는 방식이 좋습니다.

따라서 아래 방식을 통해 자신의 컴퓨터로 hosting을 직접 해 봅니다.

### _config.yml 파일을 수정합니다.

remote_theme 부분을 주석 처리하고, theme 부분에 주석 처리를 해제하여, local 모드로 바꿉니다.

```yaml
theme: jekyll-theme-so-simple
# remote_theme: mmistakes/so-simple-theme
```

### bundle 명령어로 모듈들을 다운받습니다.

bundle 명령어는 ruby로 되어있는 패키지들을 다운받는 명령어 입니다.
```bash
bundle install
```

### jekyll 명령어를 통해 local 컴퓨터에 웹페이지를 호스팅 합니다.

```bash
jekyll serve
```

### 웹브라우저에서 웹 페이지가 잘 떴는지 확인합니다.

localhost:4000에 들어가서 화면이 잘 나오는지 확인 합니다.

### 새로운 글을 작성합니다.

저희 동아리가 github io page를 블로그로 사용하는 이유는 markdown 형식으로 글을 작성할 수 있기 때문입니다.
markdown은 코드나, 수식 등 여러가지 형태의 글을 작성할때 비교적 간편하게 작성할 수 있습니다.
markdown 파일의 확장자는 .md 이며, 저희는 이제 글을 작성할 때 .md 확장자를 가진 파일을 작성하면 됩니다.
블로그에 글을 작성하기 위해서 웹페이지 구조를 다 이해할 필요가 없으며, 저희가 글을 쓰기 위해 알아야 할 부분은 _posts 폴더입니다. 
``` 
  "docs/_posts"
```
다음의 경로로 들어가면 md 확장자를 가진 post들이 존재합니다. 글의 여기에 새로운 md 확장자의 글을 추가하게 되면, 자동적으로 블로그에 새로운 글이 추가가 됩니다. 또한 post 파일 윗부분에는 title, category, tag를 설정할 수 있으며, 이것을 기반으로 post들을 블로그에서 구분할 수 있습니다.

```
title: "SOCC Tech Blog 사용법"
categories:
  - Jekyll
tags:
  - Jekyll
  - blog

last_modified_at: 2020-02-02T14:25:52-05:00
```

블로그의 글을 수정한 뒤에 호스팅 된 페이지를 껏다가 jekyll serve로 다시 홈페이지를 띄워야 업데이트 됩니다. (분명 node.js의 nodemon 처럼 실시간 업데이트를 적용해 주는 방식이 있을 것 같은데 저는 잘 모르겠네요...)


### 작성한 글을 저장하고 localhost에 띄워서 글이 제대로 적혀 있는지 확인 합니다.

```bash
jekyll serve
```

### 제대로 된것을 확인 했다면 이제 github server에 제대로 호스팅이 될 수 있도록 _config.yml을 수정합니다.

```yaml
# theme: jekyll-theme-so-simple
remote_theme: mmistakes/so-simple-theme
```

### 커밋 후 push 합니다.

```bash
git add .
git commit -m "add post"
git push origin master
```

push 이후에는 github server에서 자동적으로 호스팅을 해줍니다.
커밋 오른쪽에 초록색 체크가 뜨면 제대로 페이지가 빌드 되었다는 것을 확인 할 수 있습니다.
만약에 빨간색으로 x자가 써져 있다면, 빌드가 되지 않았다는 뜻이고, local 에서 빌드가 되는지 확인을 해봐야 합니다.


