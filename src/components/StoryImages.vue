<template>
    <!-- <div v-for="(choppedContent, index) in chopContent(item.content)"> -->
    <div v-for="(image, index) in this.imageUrls">
        <img v-if="this.role === 'assistant'" :src="this.imageUrls[index]" alt="image">
        <div v-html="md.render(this.content)"></div>
    </div>
</template>

<script setup lang="ts">
// import { ref } from "vue";
import { md } from "@/libs/markdown";

const props = defineProps<{ role: string, content: string, imageUrls: [String] }>();

const chopContent = (content) => {
    console.log('content :>> ', content);
    const maxLen = content.length > 100 ? 25 : content.length / 4;
    const choppedContent = [];
    for (let i = 0; i < content.length; i += maxLen) {
        choppedContent.push(content.slice(i, i + maxLen));
    }
    return choppedContent;
}
</script>

<style scoped>
</style>
