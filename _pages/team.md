---
title: "Team"
layout: gridlay
sitemap: false
permalink: /team/
---

<style>
/* 弹窗触发元素（姓名）样式 */
.member-popup {
  position: relative;
  display: inline-block;
  cursor: pointer;
  color: #fcfdff; /* 链接色，模拟可点击效果 */
  text-decoration: underline;
}

/* 弹窗内容容器 */
.popup-content {
  visibility: hidden; /* 默认隐藏 */
  opacity: 0; /* 初始透明，配合过渡动画 */
  position: absolute;
  z-index: 999; /* 确保弹窗在最上层 */
  top: 120%; /* 定位在姓名下方 */
  left: 50%;
  transform: translateX(-50%) translateY(-10px); /* 初始上移，增强动画感 */
  background-color: #fff;
  min-width: 300px;
  max-width: 500px;
  padding: 18px;
  border-radius: 8px;
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.18);
  font-size: 14px;
  line-height: 1.6;
  color: #333;
  border: 1px solid #e0e0e0;
  transition: all 0.3s ease-in-out; /* 平滑过渡动画 */
}

/* 弹窗小箭头 */
.popup-content::after {
  content: "";
  position: absolute;
  bottom: 100%; /* 箭头指向姓名 */
  left: 50%;
  margin-left: -8px;
  border-width: 8px;
  border-style: solid;
  border-color: transparent transparent #fff transparent;
  filter: drop-shadow(0 -2px 2px rgba(0,0,0,0.05));
}

/* 鼠标悬停姓名时，显示弹窗 */
.member-popup:hover .popup-content {
  visibility: visible;
  opacity: 1;
  transform: translateX(-50%) translateY(0); /* 动画到正常位置 */
}

/* 响应式适配：小屏幕下弹窗宽度自适应 */
@media (max-width: 768px) {
  .popup-content {
    min-width: 250px;
    max-width: 90vw;
    left: 0;
    transform: translateX(0) translateY(-10px); /* 适配小屏幕初始位置 */
  }
  .popup-content::after {
    left: 20px;
  }
  /* 小屏幕hover适配 */
  .member-popup:hover .popup-content {
    transform: translateX(0) translateY(0);
  }
}
</style>

## Team

**We are looking for new team members** [(see openings)]({{ site.url }}{{ site.baseurl }}/vacancies) **!**

## PI

{% for member in site.data.pi %}

<div class="jumbotron">
<div class="row">
<div class="col-sm-2">
  <img src="{{ site.url }}{{ site.baseurl }}/images/{{ member.photo }}" width="100%" style="max-width:250px"/>
</div>
<div class="col-sm-9 col-xs-12">
<h4>{{ member.name }}</h4>
<i>{{ member.info }}</i><br>

{% if member.website %}<a href="{{ member.website }}" target="_blank"><i class="fa fa-home fa-2x"></i></a> {% endif %} {% if member.email %}<a href="mailto:{{ member.email }}" target="_blank"><i class="fa fa-envelope-square fa-2x"></i></a> {% endif %} {% if member.scholar %} <a href="{{ member.scholar }}" target="_blank"><i class="ai ai-google-scholar-square ai-2x"></i></a> {% endif %} {% if member.cv %} <a href="{{ member.cv }}" target="_blank"><i class="ai ai-cv-square ai-2x"></i></a> {% endif %} {% if member.github %} <a href="{{ member.github }}" target="_blank"><i class="fa fa-github-square fa-2x"></i></a> {% endif %} {% if member.researchgate %} <a href="{{ member.researchgate }}" target="_blank"><i class="ai ai-researchgate-square ai-2x"></i></a> {% endif %}

<ul style="overflow: hidden">
<li> {{ member.education[0] }} </li>
<li> {{ member.education[1] }} </li>
</ul>
</div>
</div>
</div>

{% endfor %}

## Current Staff, Postdocs, and Students

<div class='jumbotron'>
{% assign number_printed = 0 %}
{% for member in site.data.team_members %}

{% assign even_odd = number_printed | modulo: 2 %}

{% if even_odd == 0 %}
<div class="row">
{% endif %}

<div class="col-sm-2">
<img src="{{ site.url }}{{ site.baseurl }}/images/{{ member.photo }}" width="100%" style="max-width:250px"/>
</div>
<div class="col-sm-4 col-xs-12">
  <!-- 关键修改：姓名添加弹窗触发 + 弹窗容器 -->
  <h4 class="member-popup">
    {{ member.name }}
    <!-- 弹窗内容：渲染narration，newline_to_br转换换行 -->
    <span class="popup-content">
      {{ member.narration | newline_to_br }}
    </span>
  </h4>
  <i>{{ member.info }}<br></i>

{% if member.website %}<a href="{{ member.website }}" target="_blank"><i class="fa fa-home fa-2x"></i></a> {% endif %}
{% if member.email %}<a href="mailto:{{ member.email }}" target="_blank"><i class="fa fa-envelope-square fa-2x"></i></a> {% endif %}
{% if member.scholar %} <a href="{{ member.scholar }}" target="_blank"><i class="ai ai-google-scholar-square ai-2x"></i></a> {% endif %}
{% if member.cv %} <a href="{{ member.cv }}" target="_blank"><i class="ai ai-cv-square ai-2x"></i></a> {% endif %}
{% if member.github %} <a href="{{ member.github }}" target="_blank"><i class="fa fa-github-square fa-2x"></i></a> {% endif %}
{% if member.researchgate %} <a href="{{ member.researchgate }}" target="_blank"><i class="ai ai-researchgate-square ai-2x"></i></a> {% endif %}

</div>

{% assign number_printed = number_printed | plus: 1 %}

{% if even_odd == 1 %}
</div>
{% endif %}

{% endfor %}

{% assign even_odd = number_printed | modulo: 2 %}
{% if even_odd == 1 %}
</div>
{% endif %}
</div>

## Alumni

<div class="jumbotron">
{% assign number_printed = 0 %}
{% for member in site.data.alumni %}

{% assign even_odd = number_printed | modulo: 2 %}

{% if even_odd == 0 %}
<div class="row">
{% endif %}

<div class="col-sm-2">
<img src="{{ site.url }}{{ site.baseurl }}/images/{{ member.photo }}" width="100%" style="max-width:250px"/>
</div>
<div class="col-sm-4 col-xs-12">
  <h4>{{ member.name }}</h4>
  <i>{{ member.duration }} <br> Role: {{ member.info }}</i>
  <ul style="overflow: hidden">
  </ul>
</div>

{% assign number_printed = number_printed | plus: 1 %}

{% if even_odd == 1 %}
</div>
{% endif %}
{% endfor %}

{% assign even_odd = number_printed | modulo: 2 %}
{% if even_odd == 1 %}
</div>
{% endif %}
</div>

## Administrative Support

<a href="798809392@qq.com">Tentative staff</a> is helping us with administration.