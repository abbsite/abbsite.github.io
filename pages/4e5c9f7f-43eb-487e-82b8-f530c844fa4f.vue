<template>
    <div ref="jarallaxRef" class="ui basic vertical fitted segment jarallax mceNonEditable  min-h-[60vh]"
        :style="`background-image:url(${url})`">
        <div class="ui active light dimmer">
            <div class="content"><a class="ui header hvr-icon-wobble-vertical massive inverted icon"
                    style="font-family: Arsenal, sans-serif;"><i class="hvr-icon !h-28 icon mx-auto"
                        :class="page.i"></i><span class="ui">{{ page.title }}<span class="sub header">{{
                            page.description
                        }}</span></span></a></div>
        </div>
    </div>
    <p>&nbsp;</p>
    <div class="ui container">
        <p style="text-align: justify;"><em>Это тот самый случай, когда от собственного бессилия ты чуть не плачешь...
                Все,
                что я помню, что это была невероятно яркая, фантастическая история, наполненная до краев сюжетом,
                персонажами, действием. И это было настолько захватывающе, что проснувшись с твердым намерением уж на
                этот
                раз точно запомнить, я схватила ноутбук и начала записывать. И тут снова возник Некто, и прямо у меня на
                глазах начал стирать сон... Мазок за мазком картина стиралась, уходя безвозвратно в небытие...</em></p>
        <div class="ui divider">&nbsp;</div>
        <p style="text-align: justify;">Если Мир не проветривать, не чистить, не убирать за собой грязь, то рано или
            поздно
            может произойти очень странная история. А именно, могут перехлестнуться совершенно разные измерения и тогда
            не
            угадаешь, чем все закончится... Так произошло и на этот раз. Мир устал. Очень устал. И решил устроить
            небольшую
            встряску.</p>
        <p style="text-align: justify;">В тот день 52-ая, как обычно, на своем гроупеде летела по городу. Гроупед был
            старый, но 52-ая...</p>
        <p>&nbsp;</p>
        <p><em>30 июня 2012</em></p>
        <router-link :to="page.parent.to" class="ui labeled icon blue button mceNonEditable"
            style="font-family: Arsenal, sans-serif;"><i class="left arrow icon"></i>назад</router-link>
    </div>
</template>

<script setup>
import { inject, useTemplateRef, onMounted } from "vue";
import { jarallax } from "jarallax";

const { id } = defineProps(["id"]),
    page = inject("pages")[id],
    [{ url }] = page.images,
    jarallaxRef = useTemplateRef("jarallaxRef");

onMounted(() => { jarallax(jarallaxRef.value, {}) });
</script>