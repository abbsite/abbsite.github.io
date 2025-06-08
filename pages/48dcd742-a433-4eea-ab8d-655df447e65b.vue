<template>
    <div class="ui container free">
        <div ref="jarallaxRef" class="ui basic vertical fitted segment jarallax mceNonEditable min-h-[70vh]"
            :style="`background-image:url(${url})`">
            <div class="ui active light dimmer">
                <div class="content"><a class="ui header hvr-icon-wobble-vertical massive inverted icon"
                        style="font-family: Arsenal, sans-serif;"><i class="hvr-icon !h-28 icon mx-auto"
                            :class="page.i"></i><span class="ui">{{ page.title }}<span class="sub header">{{ page.description
                            }}</span></span></a></div>
            </div>
        </div>
    </div>
    <p>&nbsp;</p>
    <div class="ui container">
        <div class="ui three column centered stretched padded grid mceNonEditable stackable doubling">
            <div v-for="(child,i) in page.$children" class="column animate__animated" :class="{ animate__flipInY: flip[i], animate__flipOutY: !flip[i], }" v-intersection-observer="[([{ isIntersecting }]) => { flip[i] = isIntersecting }, { threshold: 0.3 }]">
                <div class="ui fluid raised link card">
                    <div class="ui image" ref="cards">
                        <div class="ui inverted dimmer"><router-link :to="child.to"
                                class="ui circular inverted secondary icon button"><i class="icon !h-3"
                                    :class="child.i"></i></router-link></div>
                        <img class="ui image" loading="eager" :src="child.images[0]?.url">
                    </div>
                    <div class="content"><router-link :to="child.to" class="ui header hvr-icon-wobble-vertical"
                            style="font-family: Arsenal, sans-serif;"><i class="hvr-icon icon !inline-block"
                                :class="child.i"></i><span class="ui">{{ child.title }}<span
                                    class="sub header"></span></span></router-link></div>
                </div>
            </div>
        </div>
    </div>
</template>

<script setup>
import { useScriptTag, tryOnMounted } from "@vueuse/core";
import { inject, onMounted, useTemplateRef, ref } from "vue";
import { jarallax } from "jarallax";
import { vIntersectionObserver } from "@vueuse/components";

const { id } = defineProps(["id"]),
    page = inject("pages")[id],
    [{ url }] = page.images,
    jarallaxRef = useTemplateRef("jarallaxRef"),
    cardRefs = useTemplateRef("cards"),
    flip = ref([]);

useScriptTag("./node_modules/jquery/dist/jquery.min.js", () => {
    useScriptTag("./node_modules/fomantic-ui-css/semantic.min.js", () => {
        tryOnMounted(() => {
            $(cardRefs.value).dimmer({
                transition: "fade up",
                on: "hover",
            });
        });
    })
});

onMounted(() => {
    jarallax(jarallaxRef.value, {});
});
</script>