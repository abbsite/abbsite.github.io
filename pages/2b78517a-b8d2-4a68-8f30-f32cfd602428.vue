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
        <p style="text-align: justify;">Возлюби эту жизнь, которая бывает порой слишком жестокой и непредсказуемой к
            тебе.
            Возлюби дома, которые порой внушают тебе тревогу, возлюби эту грязь, которую люди не в состоянии убирать.
        </p>
        <p style="text-align: justify;">Возлюби людей, ибо ты один из них и ни чем не лучше их, а если хорошо подумаешь,
            то
            убедишься в этом сразу.</p>
        <p style="text-align: justify;">Возлюби Солнце, которое порой бывает слишком безжалостным и готово тебя
            буквально
            изжарить в своих лучах, а порой исчезает и небо поливает тебя холодной водой и к тебе приходит чувство
            одиночества в этом промозглом мокром мире.</p>
        <p style="text-align: justify;">Возлюби птиц, парящих над тобою и смотрящих на тебя гордо.</p>
        <p style="text-align: justify;">Возлюби змей, ползающих у твоих ног и грозящих одним укусом отнять твою жизнь.
        </p>
        <p style="text-align: justify;">Возлюби все, что способно дышать и двигаться в этом мире, ибо оно подобно тебе
            живет.</p>
        <p style="text-align: justify;">Возлюби и камень, который веками омывают волны, сулящие как блаженство в жаркий
            день, так и смерть, которая приходит также внезапно, как и шторм, возлюби этот камень, ибо он также как и ты
            сотворен Богом.</p>
        <p style="text-align: justify;">Возлюби Бога, ибо не тебе судить о его мудрости.</p>
        <p style="text-align: justify;">Возлюби и самого себя и живи в мире и согласии со своей душой и своей совестью.
        </p>
        <p style="text-align: justify;">&nbsp;</p>
        <p><em>09.07.1995</em></p>
        <router-link :to="page.parent.to" class="ui labeled icon blue button mceNonEditable"
            style="font-family: Arsenal, sans-serif;"><i class="left arrow icon"></i>назад</router-link>
    </div>
</template>

<script setup>
import { inject, useTemplateRef, onMounted } from "vue";
import { jarallax } from "jarallax";

const { pid: id } = defineProps(["pid"]),
    page = inject("pages")[id],
    [{ url }] = page.images,
    jarallaxRef = useTemplateRef("jarallaxRef");

onMounted(() => { jarallax(jarallaxRef.value, {}) });
</script>