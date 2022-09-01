---
title: Jekyll Blog에 멀티미디어 첨부 해보자
tags: blog
layout: article
sidebar:
  nav: wiki
article_header:
  type: overlay
  theme: dark
  background_color: '#222'
---
# Multimedia 를 Jekyll에...
<!--more-->
지금은 어떻게 해야 하는지 하나도 모르는 상태이다.  
그리고 다 알고 난 다음에 글을 쓰려면 뭐가 문제인지 모르기에  
지금 배우면서 기록을 해놓으려 한다.  
새로 블로그를 시작하는 누군가에게 도움이 되기를  

# Insert Multimedia  

## Image  

### Image from internet  
- 먼저 쉬운 것부터 해보자. 이건 지금도 알고 있다
- ```Markdown (Kramdown)``` 에서의 문법은 아래와 같다
- ```![Image alt text 이미지 없을때 표시]($url_for_image)```
- 위 문법은 두가지로 나뉘어져 있다
  - **느낌표** : 이 뒤의 링크는 이미지임!
  - ```[표시할 텍스트](주소)``` : _표시할 텍스트_ 에 _주소_ 로 하이퍼 링크를 만듬 > 링크 만드는 문법
  - 두개가 합쳐져서 주소의 이미지를 이미지로 렌더링을 하면서 alt text 로 _표시할 텍스트_
  - ```https://myoctocat.com/assets/images/base-octocat.svg``` 라는 이미지를 뿌려보자
  - ```![옥토캣!](https://myoctocat.com/assets/images/base-octocat.svg)```
  - ![옥토캣!](https://myoctocat.com/assets/images/base-octocat.svg){:style="max-height:200px"}


### Image from my git repository
- 언제나 웹 사이트에 올라가 있는 그림만 보여줄 수는 없는 법
- 나의 사진, 그리고 캡쳐 등등 의 리소스도 보여줘야 하는데?
- 이제 이미지를 Markdown 으로 불러 오는 문법을 배웠으니 간단하다.
  1. 먼저 이미지를 웹에 올린다.
  2. 업로드한 이미지의 Url 을 얻는다.
  3. 위 Url 을 복사해서 MarkDown 으로 이미지를 표시 한다!


#### 실전!
- 이미지를 웹에 올린다. 
- 아무데나 올려도 됩니다. 웹상이면. 하지만 우린 Git에서 놀고 있으니까 
- 그리고 블로그의 리소스를 올리고 싶은 거니까
- 블로그 어딘가에 올려봅시다.
- 어디가 좋을까?
  - ```/assets/images/post``` 라는 폴더가 좋을을 거 같습니다.
  - 같은 Repo 에 같은 Branch 라면 md file 에서는 아래와 같이 접근이 가능하다고 함
  - ```/assets/images/post/assets_images_path.png```
  - 그러면 한번 markdown으로 써 볼까요?
  - ```![path](/assets/images/post/assets_images_path.png)``` 라고 하면~
  - ![path](/assets/images/post/assets_images_path.png){:style="max-height:100px"}
  - 짜잔~!


## Youtube  

### Requirement
- Youtube 는 Plugin 이 필요 한 것 같다.
- 다행히 TeXt 테마는 여러 Plugin들을 이미 가지고 있는데
- 플러그인 설치도 나중에 다룰 수 있으면 좋겠네  
- Youtube `플러그인`은 아래 코드가 다네....ㅋㅋ
{% raw %}
~~~ html
<div class="extensions extensions--video">
  <iframe src="https://www.youtube.com/embed/{{ include.id }}?rel=0&showinfo=0"
    frameborder="0" scrolling="no" allowfullscreen></iframe>
</div>
~~~
{% endraw %}
### embed youtube  
- Youtube 에서 원하는 비디오를 고른다
  - 우리집 고양이 동영상을 골라 봤어요.
  - 주소는 ```https://www.youtube.com/watch?v=4c0ERQDYA2A```
  - ![youtube id](/assets/images/post/youtube_video_id.png){:max-height="36px"}
  - 여기서 ```4c0ERQDYA2A``` 부분이 필요한 id! 
- 아래와 같이 적으면 된다. 
{% raw %}
- ```<div>{%- include extensions/youtube.html id='4c0ERQDYA2A' -%}</div>```
{% endraw %}
<div>{%- include extensions/youtube.html 
id='4c0ERQDYA2A' -%}</div>
- 잘 보이나요? ㅎ
<!-->
# Post Background Resource
이제 좀더 심화 과정으로 들어가 보자.  
새로운 이미지를 넣을 때는 그저 하나하나 만들면 되겠지만...  
Post의 Header image 라던가  
자주 쓰게 되는 리소스의 경우  
매번 주소를 모두 타이핑 하기 힘들고 귀찮은 일!  
자고로 엔지니어라면 귀찬은 일을 없애야만 하는 법!!  
-->