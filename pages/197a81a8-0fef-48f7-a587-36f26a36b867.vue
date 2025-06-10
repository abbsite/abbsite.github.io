<template>
    <p>&nbsp;</p>
    <div class="ui horizontal centered stackable basic segments">
        <div class="ui segment" v-for="({url, alt}, index) in page.images">
            <figure class="ui rounded medium centered image">
            <el-image :src="url" :preview-src-list="srcList" :initial-index="index" fit="cover"></el-image>
            <figcaption class="content" style="text-align: center;">{{ alt }}</figcaption>
            </figure>
        </div>
    </div>
    <p>&nbsp;</p>
</template>

<script setup>
import { inject } from "vue";

const { id } = defineProps(["id"]),
    page = inject("pages")[id],
    srcList = page.images.map(({url})=> url);
</script>