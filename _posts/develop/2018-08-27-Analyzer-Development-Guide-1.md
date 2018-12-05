---
title: 프로젝트 생성
permalink: /workbench/analyzerguide1/
author_profile: false
image:
  cover: true
  path: &image /assets/images/analyzerguide1/1.png
  feature: *image
  teaser: /assets/images/analyzerguide1/1.png
  thumbnail: /assets/images/analyzerguide1/14.png
  caption: "Post-Processor Development Guide"
categories: [workbench]
tags: [edisonworkbench, analyzer]
support: true
date: 2018-08-27 09:00:00 +0900
comments: true
order: 10
support: true
classes: wide
redirect_from:
  - /theme-setup/
sidebar:
  title: "워크벤치 분석기 개발"
  nav: workbench
---

[EDISON](https://edison.re.kr) 워크벤치 기반 분석기(Post-Processor) 개발 매뉴얼 입니다.

Liferay 6.2.5 포틀릿 기반으로 개발 하는 방법에 대해 순차적으로 설명 되어 있습니다.


## Liferay 6.2 기반 프로젝트 구성
개발 환경은 아래와 같습니다.

- `이클립스 Neon 3 Release (4.6.3)`
- `liferay-portal-6.2-ce-ga6`
- `liferay-plugins-sdk-6.2`




## 1. Liferay plugin Project  생성
이클립스 환경에서 `Liferay Plugins Projects`를 생성합니다.
<br>이클립스 환경에서 New -> Liferay Plugin Project를 선택합니다.<br>
![imagetestYejin](/assets/images/analyzerguide1/1.png "프로젝트 생성")
<br><br>프로젝트 이름을 작성하고 include sample code 체크를 해지합니다.<br>
![imagetestYejin](/assets/images/analyzerguide1/2.png "프로젝트 생성")
<br><br>프로젝트 이름을 작성하고 Liferay MVC를 선택하여 최종적으로 프로젝트 생성을 마무리 합니다.<br>
![imagetestYejin](/assets/images/analyzerguide1/3.png "프로젝트 생성")
<br><br>생성이 완료된 플러그인 프로젝트의 구성은 다음과 같습니다.
![imagetestYejin](/assets/images/analyzerguide1/4.png "프로젝트 생성")<br><br>

## 2. EDISON 워크벤치 연동을 위한 Analyzer 포틀릿 생성
EDISON 플랫폼의 워크벤치 연동을 위한 포틀릿을 생성합니다.
<br>생성된 Liferay Plugins Projects 내에 Liferay Portlet을 생성합니다.<br>
![imagetestYejin](/assets/images/analyzerguide1/5.png "포틀릿 생성")
<br><br>포틀릿 클래스명, 패키지명은 자유롭게 원하는 형태로 생성합니다.<br>
![imagetestYejin](/assets/images/analyzerguide1/6.png "포틀릿 생성")
<br><br>포틀릿 클래스 명에 따라 자동으로 설정되는 값입니다.<br> 나중에 수정할 수 있으니 현재는 Next를 누르고 넘어갑니다.<br>
![imagetestYejin](/assets/images/analyzerguide1/7.png "포틀릿 생성")
<br><br>마찬가지로 자동으로 설정되는 값입니다. <br>나중에 수정할 수 있으니 현재는 Next를 누르고 넘어갑니다.<br>
![imagetestYejin](/assets/images/analyzerguide1/8.png "포틀릿 생성")
<br><br>특별히 추가할 인터페이스가 없다면 Finish를 선택하고 포틀릿 생성을 완료합니다.
![imagetestYejin](/assets/images/analyzerguide1/9.png "포틀릿 생성")<br><br>

## 3. 포틀릿 리소스 접근 설정
EDISON 플랫폼에서 워크벤치와 연동을 위해서는 각 포틀릿간의 외부 접근이 가능하도록 권한 설정을 해 주어야 합니다. <br>
따라서 외부(다른 포틀릿)에서 개발하려는 포틀릿으로 접근하기 위해서는 포틀릿의 외부 권한을 설정하여야 합니다.
설정하는 방법은 아래와 같습니다.<br>
`liferay-portlet.xml` 파일 내부에 아래 코드를 추가합니다.

```xml
<add-default-resource>true</add-default-resource>
```
아래의 그림과 같이 xml 파일 내부에 생성한 포틀릿 내 해당 코드를 추가합니다.
![imagetestYejin](/assets/images/analyzerguide1/11.png "포틀릿 설정")<br>


## 4. 기본 플러그인 추가 설정
현재 Liferay Plugin Project에서 기본적으로 필요한 플러그인들을 추가합니다.<br>
3번과 마찬가지로 xml 파일을 변경하는 것으로, liferay-plugin-package.properties 파일을 수정합니다.<br>
기본적으로 이클립스에서 제공해주는 UI 환경에서 플러그인을 추가합니다. 해당 화면은 아래와 같습니다.<br>
![imagetestYejin](/assets/images/analyzerguide1/12.png "플러그인 설정")<br>

Portal Dependency Jars 섹션에서 Add...버튼을 클릭한 후, jstl 을 검색해서 나오는 jstl-api.jar, jstl-impl.jar파일 두개를 추가합니다.<br>
![imagetestYejin](/assets/images/analyzerguide1/13.png "플러그인 설정")<br>


## 5. 워크벤치 연동을 위한 플러그인 추가 설정
워크벤치 연동을 위해 필요한 라이브러리들을 현재 생성한 프로젝트 내 WEB-INF/lib 내 추가합니다.
![imagetestYejin](/assets/images/analyzerguide1/14.png "플러그인 설정")<br>

필요 라이브러리들을 추가합니다.<br>
[commons-beanutils.jar](/assets/OSPLibrary/commons-beanutils.jar)<br>
[commons-collections.jar](/assets/OSPLibrary/commons-collections.jar)<br>
[commons-exec-1.1.jar](/assets/OSPLibrary/commons-exec-1.1.jar)<br>
[commons-fileupload.jar](/assets/OSPLibrary/commons-fileupload.jar)<br>
[commons-io.jar](/assets/OSPLibrary/commons-io.jar)<br>
[commons-lang.jar](/assets/OSPLibrary/commons-lang.jar)<br>
[SciencePlatform-hook-service.jar](/assets/OSPLibrary/SciencePlatform-hook-service.jar)
{: .notice--info}
