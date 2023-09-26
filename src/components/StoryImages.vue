<script setup lang="ts">
// import { ref } from "vue";
import { md } from "@/libs/markdown";

const props = defineProps<{ role:string, content: string, imageUrls:[String] }>();
</script>

<template>
    <!-- <div v-for="(choppedContent, index) in chopContent(item.content)"> -->
    <div v-for="(image, index) in this.imageUrls">
        <img v-if="this.role==='assistant'" :src="this.imageUrls[index]" alt="image">
        <div v-html="md.render(this.content)"></div>
    </div>
</template>

<style scoped>
</style>
