---
title: オンライン ホステッド インストラクション
permalink: index.html
layout: home
ms.openlocfilehash: f4e2e1489e1997cfd064aa74eb5345e302bb2424
ms.sourcegitcommit: ef58c858463b890e923ef808b1d43405423943fd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/27/2022
ms.locfileid: "137898887"
---
# <a name="content-directory"></a>コンテンツ ディレクトリ

各ラボの演習とデモへのハイパーリンクを以下に示します。

## <a name="labs"></a>ラボ

{% assign labs = site.pages | where_exp:"page", "page.url contains '/Instructions/Labs'" %}
| モジュール | ラボ |
| --- | --- | 
{% for activity in labs  %}| {{ activity.lab.module }} | [{{ activity.lab.title }}{% if activity.lab.type %} - {{ activity.lab.type }}{% endif %}]({{ site.github.url }}{{ activity.url }}) |
{% endfor %}

## <a name="demos"></a>デモ

{% assign demos = site.pages | where_exp:"page", "page.url contains '/Instructions/Demos'" %}
| モジュール | デモ |
| --- | --- | 
{% for activity in demos  %}| {{ activity.demo.module }} | [{{ activity.demo.title }}]({{ site.github.url }}{{ activity.url }}) |
{% endfor %}
