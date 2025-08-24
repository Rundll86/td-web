<template>
    <BackgroundImage :disable="false" :blur="bluring" />
    <FullscreenSize class="container-app">
        <div class="main" :class="{ bluring }" @mouseover="bluring = true" @mouseleave="bluring = false">
            <SelfInformation />
            <DescriptionParagraph title="关于我">
                你好！<br>
                我是<b>唐豆</b>，来自中国的<i>艺术</i>爱好者。<br>
                有梦想，但仍在学习的路上，尚无法实现。
            </DescriptionParagraph>
            <DescriptionParagraph title="技能">
                用 <b>XXX</b> 和 <b>XXX</b> 做过XXX，但XXX。<br>
                目前能熟练使用的一些前沿 <b>XXX</b>：<br>
                <BlockLabel>XXX1</BlockLabel>
                <BlockLabel>XXX2</BlockLabel>
                <VerticalLine />
                <BlockLabel>XXX3</BlockLabel>
                <BlockLabel>XXX4</BlockLabel>
            </DescriptionParagraph>
            <DescriptionParagraph title="展望">
                XXX
            </DescriptionParagraph>
            <DescriptionParagraph title="联系方式">
                邮箱：<OutLink href="mailto:3161880837@qq.com">3161880837@qq.com</OutLink><br>
                QQ：<OutLink @click="copy('3161880837')">3161880837</OutLink><br>
                <OutLink href="https://space.bilibili.com/649063815">哔哩哔哩</OutLink>
                <OutLink class="link-2" href="https://github.com/Rundll86">Github</OutLink>
            </DescriptionParagraph>
            <HorizontalLine />
            <BigTitle>development</BigTitle><br>
            <ProjectCard website="https://github.com/Rundll86/script-editor-2" image="se2.jpg" title="ScriptEditor"
                tech-stack="Vue" category="工具">
                基于界面的AVG游戏剧本设计器，让不会写代码的文案师也能组织剧本。
            </ProjectCard>
            <ProjectCard website="fs-context" image="fsc.jpg" title="FS-Context" tech-stack="TS" category="开发框架">
                一个开发上下文，使用TS类型提示和全新的脚手架开发某软件的通用拓展。
            </ProjectCard>
            <ProjectCard website="https://github.com/Rundll86/ModLoaderNew" image="mln.jpg" title="ModLoaderNew"
                tech-stack="Python" category="游戏">
                将自定义模型注入原神客户端，基于GIMI。封装更多工具，可能违法。
            </ProjectCard>
            <HorizontalLine />
            <BigTitle>友情链接</BigTitle><br>
            <OutLink href="https://vuejs.org">Vue</OutLink>
            +
            <OutLink href="https://webpackjs.com">Webpack</OutLink>
        </div>
    </FullscreenSize>
</template>
<script setup lang="ts">
import { ref, onMounted } from "vue";
import BackgroundImage from "./BackgroundImage.vue";
import FullscreenSize from "./FullscreenSize.vue";
import BlockLabel from "./BlockLabel.vue";
import DescriptionParagraph from "./DescriptionParapragh.vue";
import VerticalLine from "./VerticalLine.vue";
import OutLink from "./OutLink.vue";
import HorizontalLine from "./HorizontalLine.vue";
import ProjectCard from "./ProjectCard.vue";
import BigTitle from "./BigTitle.vue";
import SearchE621 from "./SearchE621.vue";
import SelfInformation from "./SelfInformation.vue";
const bluring = ref(false);
onMounted(() => {
    const structuredData = {
        "@context": "https://schema.org",
        "@type": "Person",
        "name": "陨落基围虾",
        "url": "https://rundll86.github.io/",
        "image": "https://rundll86.github.io/avatar.png",
        "sameAs": [
            "https://space.bilibili.com/649063815",
            "https://github.com/Rundll86"
        ],
        "jobTitle": "全栈/桌面开发爱好者",
        "worksFor": {
            "@type": "Organization",
            "name": "SolariiX"
        },
        "description": "FallingShrimp的个人网站，展示技术项目、技能和兴趣爱好。全栈/桌面开发爱好者，专注Web技术、游戏开发和福瑞文化。"
    };
    const script = document.createElement("script");
    script.type = "application/ld+json";
    script.textContent = JSON.stringify(structuredData);
    document.head.appendChild(script);
});
function copy(data: string) {
    try {
        window.navigator.clipboard.writeText(data);
    } catch {
        alert("复制失败。");
    }
};
window.mouse = ref([0, 0]);
window.addEventListener("mousemove", (e) => {
    window.mouse.value = [e.clientX, e.clientY];
});
</script>
<style scoped>
.container-app {
    text-align: center;
    width: 100%;
    height: auto;
    position: absolute;
}

.main.bluring {
    opacity: 1;
}

.main {
    padding: 50px 0;
    display: inline-block;
}

.link-2 {
    margin-left: 5px;
}

.oc-preview {
    width: 200px;
    display: block;
}

.text-left {
    text-align: left;
    width: fit-content;
    display: inline-block;
}
</style>