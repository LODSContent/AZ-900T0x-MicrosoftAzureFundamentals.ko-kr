---
title: 온라인 호스팅 지침
permalink: index.html
layout: home
ms.openlocfilehash: c8816b7d9de9c19fbd4c6b3f373d6e4336c6ca5a
ms.sourcegitcommit: 26c283fffdd08057fdce65fa29de218fff21c7d0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/27/2022
ms.locfileid: "137908665"
---
# <a name="content-directory"></a>콘텐츠 디렉터리

각 연습에 대한 하이퍼링크. 강사는 연습을 데모 또는 학생 랩으로 사용할 수 있습니다. 

## <a name="walkthroughs"></a>연습

{% assign wts = site.pages | where_exp:"page", "page.url contains '/Instructions/Walkthroughs'" %}
| 모듈 | 연습 |
| --- | --- | 
{% for activity in wts %}| {{ activity.wts.module }} | [{{ activity.wts.title }}{% if activity.wts.type %} - {{ activity.wts.type }}{% endif %}]({{ site.github.url }}{{ activity.url }}) |
{% endfor %}

