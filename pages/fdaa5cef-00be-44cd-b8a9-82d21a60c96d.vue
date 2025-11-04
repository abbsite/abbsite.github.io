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
        <p style="text-align: justify;"><em><span class="s1">Это сон наяву. Причем очень короткий. Но я&nbsp;до сих пор
                    не
                    могу его&nbsp;дописать... В 1999 году я стала невольным свидетелем ужасного: на полном ходу машина
                    сбила
                    собаку. Обычную такую собаку... Не буду подробно описывать весь этот ужас. С собакой на руках я
                    приехала
                    в ветеринарку. Собака была спокойна. Ее осмотрел ветеринар, но&nbsp;диагноз его был неутешителен:
                    собака
                    не сможет ходить никогда. Еще он сказал, что собака старая и что лучшего все для нее, ее усыпить...
                    Решение должна была принимать я. Я же с ней приехала. Денег на ее лечение у меня не было, я не знала
                    что
                    делать. Ветеринар еще раз сказал, что это лучший выход. И я дала добро. Господи... Как она не хотела
                    умирать... А я теперь живу с этим. И вот как-то раз мне приснилась наяву
                    история,&nbsp;она&nbsp;виделась
                    мне глазами собаки. Вот ее приносят щенком в новый дом. Вот она растет. Она любит своих хозяев. Но
                    что-то происходит и она оказывается на улице. Одна, ей страшно. Она не понимает, что с ней
                    происходит,
                    куда ей идти. А потом страшный удар. И когда мир начинает терять свои очертания, она снова слышит:
                    Донна! Мы назовем ее Донна!</span></em></p>
        <div class="ui divider">&nbsp;</div>
        <p><span class="s1">&mdash; Донна! Мы назовем ее Донна! &ndash; источником шума оказался человеческий ребенок.
                Судя
                во всему девочка, я еще плохо умела определять пол этих существ. Девочка повизгивала почти как мы,
                щенки,
                когда играем друг с другом. Но мне было не до нее, меня с самого утра мучили странные
                предчувствия&hellip;</span></p>
        <p style="text-align: justify;"><span class="s1">Я проснулась со странным ощущением, что мир переворачивается.
                Не
                хотелось даже материнского молока&hellip; Хотя я уже довольно взрослый щенок, иногда люблю прижаться
                носом к
                материнскому животу. В этот момент весь мир становится теплым и уютным. Но не сегодня.</span></p>
        <p style="text-align: justify;"><span class="s1">Моя мать &ndash; лабрадор. У нее есть награды, которыми ее
                хозяева
                почему-то страшно гордятся. Может это и правда хорошо, для нас собак, но я пока не знаю. Возможно если
                есть
                эти штуки, то тогда кормят вкуснее&hellip; Надо будет это выяснить. Только где их берут, эту штуки?
                Когда
                меня выводили на улицу, я вроде не заметила мест, где бы ими пахло&hellip; Сколько еще всего надо
                узнать&hellip;</span></p>
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