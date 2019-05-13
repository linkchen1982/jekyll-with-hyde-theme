---
layout: page
title: Liquid語法測試
date: 2019-05-08 11:17 +0800
permalink: /only-for-debug
---

### 查看`site`與`page`的value ###

Variables|Results
:---|:---
{% raw %}site.url{% endraw %}|{{ site.url }}
{% raw %}site.baseurl{% endraw %}|{{ site.baseurl }}
{% raw %}page.url{% endraw %}|{{ page.url }}

---
### 如何在Jekyll裡使用Vue.js ###

由於Jekyll和Vue.js的delimiter相同，都是使用{% raw %}{{}}{% endraw %}，所以Jekyll會優先忽略Vue.js的語法。

若要使用`Vue.js`，必須藉助Liquid語法raw，讓Jekyll跳過指定區段不處理，就可以接著Vue.js接手處理{% raw %}{{}}{% endraw %}。舉例：
~~~html
<p id="app">你好，我的名字是 <span style="background-color: yellow;">{% raw %}{{ myName }}{% endraw %}</span></p>

<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
<script>
  var app = new Vue ({
    el: "#app",
    data: {
      myName: "陳正昇"
    }
  })
</script>
~~~
結果如下：
<p id="app">你好，我的名字是 <span style="background-color: yellow;">{% raw %}{{ myName }}{% endraw %}</span></p>

<script src="https://cdn.jsdelivr.net/npm/vue"></script>
<script>
  var app = new Vue ({
    el: "#app",
    data: {
      myName: "陳正昇"
    }
  })
</script>

進階的做法，更改Jekyll或Vue.js其中一方的delimiter，似乎是更有效率的做法。

---