---
title: Domain 연결하기
tags: blog
sidebar:
  nav: wiki
article_header:
  type: overlay
  theme: dark
  background_color: '#252525'
---
# Git Pages 에 Custom Domain 연결 해 보자
<!-- more -->
> 도메인은 GoDaddy 를 통해 구입 했으니 참고 바랍니다.  

## Domain 이란?
- 네트워크의 모든 디바이스는 기본적으로 IP Address 로 자신을 나타냅니다.
- IP Address 란 `192.168.0.1` 처럼 숫자로 이루어진 주소 입니다. 
- 근데 외우기가 너무 어려우니 Human readable 한 Domain 이란 것을 씁니다.
- `google.com` 이나 `github.com` 처럼요

## Custom Domain 이란?
- 기본적인 Git Pages 의 주소는 `username.github.io` 입니다. 
- 물론 이 주소도 사용하는데 아무 문제 없지만
- 기본적으로 호스팅 서버에서 주어지는 sub domain 이 아닌 
- 개인의 도메인을 쓰고 싶은 마음이 들 때도 있죠! 
- 가격은 `.com` 같은 경우 1년에 3만원 정도 내는 것 같습니다 ㅎ
- 싸지는 않아서 크게 필요 없다면 별로 추천 드리지 않습니다. 
---
# Git 이 요구하는 사항
- Git 은 두가지 타입의 Domain 을 지원 합니다. 
  
  |type|example|  
  |:--------:|:------:|
  |subdomain| www.example.com|
  |         | blog.example.com|
  |apex| example.com|

- apex 를 github pages 에 설정을 하려면, www subdomain 도 같이 설정 하는 것을 추천 합니다.
- 브라우저가 redirect 하게 되는 경우가 있어서 두가지 모두 같은 곳을 보는 것이 좋습니다.

## 그러면 계획을 짜 봅시다. 
- 제가 구매한 도메인은 `fotogrammer.com` 입니다. 
  - 아마도 이 글을 보시는 시점에서는 저 도메인으로 셋팅이 되어 있기를 희망합니다 ㅎ 
  - 귀차니즘에 잠식되지 않기를...
- 먼저 apex domain 
  - `https://fotogrammer.com`
- 그다음은 www subdomain
  - `https://www.fotogrammer.com`
- 이렇게 두개의 도메인을 github pages site 에 연결을 해보도록 하죠~!

## 어떻게 하면 될까?
- Sub Domain 은 `CNAME` 이라는 DNS Record type 으로 매핑이 되며 
- Apex Domain 은 `A`, `ALIAS` 라는 DSN Record type 으로 매핑이 된다고 합니다. 
- 그럼 CNAME, A 라는게 뭘까
  - CNAME record
  - A record
    - 직접적으로 IP 에 할당
    - `fotogrammer.com` -> `github IP`
        ``` 
        185.199.108.153
        185.199.109.153
        185.199.110.153
        185.199.111.153
        ```


# 참고자료
- [List of DNS Record types](https://en.wikipedia.org/wiki/List_of_DNS_record_types)
- [About custom domains and github pages](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/about-custom-domains-and-github-pages)
- [Using an apex domain for your github pages site](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/about-custom-domains-and-github-pages#using-an-apex-domain-for-your-github-pages-site)
- [Managing a custom domain for your github pages site](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site#configuring-an-apex-domain)