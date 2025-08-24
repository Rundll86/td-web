<template>
    <div class="info">
        <AvatarImage />
        <NameLabel>TangDo158</NameLabel>
        <div>
            <BlockLabel>摄影</BlockLabel>
            <BlockLabel>平面设计</BlockLabel>
            <BlockLabel>FPS重度爱好者</BlockLabel>
            <BlockLabel>福瑞控</BlockLabel>
        </div>
        <CatcherText>也许是情绪不够稳定，不会Sc。</CatcherText>
    </div>
</template>
<script setup lang="ts">
import AvatarImage from "./AvatarImage.vue";
import NameLabel from "./NameLabel.vue";
import BlockLabel from "./BlockLabel.vue";
import CatcherText from "./CatcherText.vue";
</script>
<style scoped>
.info {
    display: flex;
    flex-direction: column;
    align-items: center;
}
</style>