<template>
    <div class="min-h-dvh" un-cloak>
        <div class="sticky top-0 z-50 pa-4 border-b bg-neutral-50 border-slate-200 opacity-0 md:hover:opacity-100 transition-opacity duration-1000"
            :class="{ 'opacity-100': !ready }" ref="pageHeader">
            <el-page-header icon="" :content="pages[$route.name].title">
                <template #breadcrumb>
                    <el-breadcrumb separator="/">
                        <el-breadcrumb-item v-for="item in pages[$route.name].branch.slice(1)" :to="item.to">
                            {{ item.name }}
                        </el-breadcrumb-item>
                    </el-breadcrumb>
                </template>
                <template #title>
                    <router-link to="/" class="whitespace-nowrap flex items-center max-sm:hidden">
                        <el-avatar size="small"><i :class="the.i"></i></el-avatar>
                    </router-link>
                </template>
                <template #extra>
                    <el-button circle @click="drawer = true">
                        <icon icon="mdi:menu" class="size-5"></icon>
                    </el-button>
                </template>
            </el-page-header>
        </div>
        <router-view></router-view>
    </div>
    <div data-static="" class="ui fluid container pt-10" style="z-index: 2;">
        <div id="bottom" class=""
            style="margin: 0px; flex: 1 1 auto; padding-top: 30px; padding-bottom: 5px; border-style: none; opacity: 1; background-color: rgb(94, 94, 94); background-position: 0% 0%; background-repeat: repeat; background-attachment: scroll; background-size: auto;">
            <div class="ui container">
                <div class="ui horizontal basic segments">
                    <div class="ui segment" style="width: 50%; background-color: rgb(94, 94, 94);">
                        <p><i class="envelope large icon" style="color: lightskyblue;"></i></p>
                        <p style="color: rgb(220, 220, 220);">Вопросы об использовании или приобретении материалов, Ваши
                            предложения, отзывы, а также другие вопросы присылайте мне на почту:<br><a
                                href="mailto:abb44@mail.ru"
                                style="text-decoration: none; color: lightskyblue;">abb44@mail.ru</a><br><br>Согласие на
                            обработку данных не требуется, я ничего не обрабатываю.</p>
                    </div>
                    <div class="ui segment" style="width: 50%; background-color: rgb(94, 94, 94);">
                        <p><i class="info circle large icon" style="color: lightskyblue;"></i></p>
                        <p style="color: rgb(220, 220, 220);">© Все права защищены. Копирование материала возможно
                            только с
                            моего согласия. Использование любой медицинской информации в личных целях требует
                            дополнительной
                            консультации врача. Все данные, опубликованные на сайте приведены исключительно для
                            ознакомления, носят информационный характер и не являются публичной офертой, определяемой
                            положениями ч. 2 ст. 437 Гражданского кодекса РФ.</p>
                    </div>
                </div>
                <p>&nbsp;</p>
                <p style="font-size: 10pt; text-align: center; color: rgb(220, 220, 220); padding-bottom: 5px;"><a
                        class="hvr-wobble-skew" title="KosmoS3 удобный и гибкий инструмент для управления сайтом на S3"
                        href="https://kosmos3.ru/" target="_blank" rel="noopener"
                        style="color: rgb(220, 220, 220); font-family: Arsenal, sans-serif; font-size: 12px;">KosmoS3 <i
                            class="hvr-icon icon rocket"></i>удобный и гибкий инструмент для управления сайтом на S3</a>
                </p>
            </div>
        </div>
    </div>
    <div id="drawer" un-cloak>
        <el-drawer v-model="drawer" :title="the.header" class="w-full sm:w-96" size="">
            <el-menu :router="true">
                <template v-for="({ name, $children, icon, id }, index) in the.$children[0].$children">
                    <el-sub-menu :index="index" v-if="$children.length">
                        <template #title>
                            <icon :icon="icon" class="icon-box"></icon><span>{{ name }}</span>
                        </template>
                        <el-menu-item v-for="(child, index2) in $children" :route="{ name: child.id }" :index="index2">
                            <icon :icon="child.icon" class="icon-box"></icon><span>{{ child.name }}</span>
                        </el-menu-item>
                    </el-sub-menu>
                    <el-menu-item :index="index" :route="{ name: id }" v-else>
                        <icon :icon="icon" class="icon-box"></icon><span>{{ name }}</span>
                    </el-menu-item>
                </template>
            </el-menu>
        </el-drawer>
    </div>
    <el-backtop></el-backtop>
</template>
<script setup>
import { useRoute } from "vue-router";
import { ref, inject, useTemplateRef, onMounted, watch, getCurrentInstance } from "vue";
import { get, set } from "@vueuse/core";
import ElementPlus from "element-plus";
import { Icon } from "@iconify/vue";


const { appContext: { app } } = getCurrentInstance();
app.component("Icon", Icon);
app.use(ElementPlus);
const { id } = defineProps(["id"]),
    pages = inject("pages"),
    the = pages[id],
    ready = ref(true),
    pageHeaderRef = useTemplateRef("pageHeader"),
    drawer = ref(false),
    route = useRoute();
onMounted(() => {
    let timeoutID;
    const scroll = () => {
        set(ready, false);
        if (timeoutID) clearTimeout(timeoutID);
        if (window.scrollY > get(pageHeaderRef, "offsetHeight")) timeoutID = setTimeout(() => {
            set(ready, true);
        }, 2000);
    };
    document.addEventListener("scroll", scroll);
    scroll();
});
watch(() => route.name, () => { drawer.value = false });
</script>
<style>
@import "./node_modules/animate.css/animate.min.css";
@import "./node_modules/hover.css/css/hover-min.css";
@import "./node_modules/element-plus/dist/index.css";
@import "./node_modules/fomantic-ui-css/semantic.min.css";

.el-drawer .el-menu {
    border-right: none;
}

#drawer :deep(.el-drawer__body) {
    padding: 0;
}

.icon-box {
    margin-right: 1rem;
    width: 2rem;
    height: 2rem;
}

A {
    color: OrangeRed;
}

#content {
    font-family: 'Arsenal', sans-serif;
    font-size: 16px;
}

#bottom {
    font-family: 'Arsenal', sans-serif;
}

#top {
    font-family: 'Arsenal', sans-serif;
}

H1 {
    font-family: 'Arsenal', sans-serif;
}

H2 {
    font-family: 'Arsenal', sans-serif;
}

H3 {
    font-family: 'Arsenal', sans-serif;
}

H4 {
    font-family: 'Arsenal', sans-serif;
}

H5 {
    font-family: 'Arsenal', sans-serif;
}
</style>