<script setup lang="ts">

import { onMounted } from 'vue';
import { useData } from 'vitepress';
import theme from 'vitepress/theme';

const { frontmatter } = useData();

onMounted(() => {
    loadDiscussion();
});

function loadDiscussion() {
    // script src="https://giscus.app/client.js"
    //     data-repo="LYGreen/make-blog"
    //     data-repo-id="R_kgDOO_l9dQ"
    //     data-category="Article discussions"
    //     data-category-id="DIC_kwDOO_l9dc4Cr1qV"
    //     data-mapping="pathname"
    //     data-strict="0"
    //     data-reactions-enabled="1"
    //     data-emit-metadata="0"
    //     data-input-position="bottom"
    //     data-theme="preferred_color_scheme"
    //     data-lang="zh-CN"
    //     crossorigin="anonymous"
    //     async>
    // script>

    const theme = document.documentElement.getAttribute('data-theme') ?? 'light';
    const comments = document.getElementById('comments');
    const script = document.createElement('script');
    script.src = "https://giscus.app/client.js";
    script.setAttribute('data-repo', "LYGreen/make-blog");;
    script.setAttribute('data-repo-id', "R_kgDOO_l9dQ");
    script.setAttribute('data-category', "Article discussions");
    script.setAttribute('data-category-id', "DIC_kwDOO_l9dc4Cr1qV");
    script.setAttribute('data-mapping', "pathname");
    script.setAttribute('data-strict', "0");
    script.setAttribute('data-reactions-enabled', "1");
    script.setAttribute('data-emit-metadata', "0");
    script.setAttribute('data-input-position', "bottom");
    script.setAttribute('data-theme', theme);
    script.setAttribute('data-lang', "zh-CN");
    script.crossOrigin = 'anonymous';
    script.async = true;
    comments?.appendChild(script);
}

</script>

<template>
    <div id="article">
        <div class="header">
            <strong class="title">{{ frontmatter.title }}</strong>
            <span class="description">{{ frontmatter.description }}</span>
            <hr>
            <span class="time">
                📅创建时间：{{ frontmatter.createdTime }}
            </span>
            <span class="time">
                🕒修改时间：{{ frontmatter.updatedTime }}
            </span>
            <span class="time">
                📖阅读时间：{{ frontmatter.readingTime }} 分钟
            </span>
        </div>
        <hr>
        <div class="body">
            <Content />
        </div>
        <hr>
        <div class="footer">
            <span class="time">
                📅创建时间：{{ frontmatter.createdTime }}
            </span>
            <span class="time">
                🕒修改时间：{{ frontmatter.updatedTime }}
            </span>
        </div>
        <hr>
        <div id="comments"></div>
    </div>
</template>

<style scoped>

#article {
    width: 100%;
    margin-top: 16px;
    padding-left: 16px;
    padding-right: 16px;
    padding-top: 16px;
    padding-bottom: 16px;

    background-color: var(--secondary-bg-color);
    box-shadow: var(--float-component-shadow);
}

#article .header .title {
    display: flex;
    justify-content: center;
    font-size: 48px;
}

#article .header .description {
    display: flex;
    justify-content: center;
    font-size: 24px;
}

#article .time {
    font-size: 14px;
    color: grey;
}

#article .header, .footer, span {
    display: block;
}





</style>
