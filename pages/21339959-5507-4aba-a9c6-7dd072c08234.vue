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
        <p style="text-align: justify;"><em>У вас бывало ощущение, что все мы здесь живем очень давно? Или, иногда едешь
                где-нибудь по совершенно не знакомой местности, и вдруг Солнце высвечивает какой-то кусочек Мира и в
                этот
                момент внутри &nbsp;у тебя что-то сжимается и ты вспоминаешь, что нечто похожее ты уже видел, только
                миллионы лет назад... А иногда ты совершенно точно знаешь, что сегодня кто-то опоздал на рейс на
                какую-нибудь далекую звезду...</em></p>
        <div class="ui divider">&nbsp;</div>
        <p style="text-align: justify;">Иногда, очень редко, попадаются фотографии, на которых небо и земля выглядят
            именно
            так, какими они были еще до заселения этой планеты людьми. Я помню Землю именно такой. Это не полноценные
            воспоминания&hellip; Это обрывки. Но они очень важны для меня, потому что не дают, порой, окончательно
            свихнуться. Это воспоминания о Доме. Потому что не смотря на то, что Земля когда-то была абсолютно свободна
            от
            людей, уже тогда это был Дом.</p>
        <p style="text-align: justify;">Я помню один из обрывков воспоминаний. Я&nbsp;шла по Проспекту Мира и думала,
            что
            вот раньше тут были девственные леса и красота. И вдруг... Все исчезло, понимаешь? ВСЕ. Вокруг только
            великолепие&nbsp;неописуемое и природа неземной красоты. И воздух какой! И вот стою я среди всего
            этого&nbsp;и
            тихо обалдеваю. И даже мысли не возникло, что такого быть не может. А ведь в&nbsp;те далекие времена Солнце
            всходило на западе, бывало и такое.</p>
        <p style="text-align: justify;">&nbsp;</p>
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