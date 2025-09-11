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
        <p style="text-align: justify;"><em>Это целая серия снов, которые снились мне на протяжении многих лет в разных
                интерпретациях, но всегда с одним сюжетом - город, уходящий под землю... Когда-то давно эти сны меня так
                вымотали, что один из них я все-таки кратко записала. Последний такой кошмар снился году примерно в
                2007.</em></p>
        <div class="ui divider">&nbsp;</div>
        <p style="text-align: justify;">Распадающееся на куски Солнце последний раз отразилось в окнах домов,
            погружающихся
            в бездну навечно, исчезающих, превращающихся в прах, чтобы когда-нибудь, возможно, возродиться вновь. Воздух
            пропитался ужасом. Крики всего живого потонули в пыли и грохоте стихии. Земля жадно поглощала все, что
            мешало ей
            долгие годы, не оставляя ничего. Люди метались в хаосе кошмара избегая одной смерти, чтобы тут же принять
            другую, еще более страшную.</p>
        <p style="text-align: justify;">Анна в этот момент находилась на станции метро Молодежная. Одуревшие от ужаса
            люди&nbsp;ничего не понимали. Зато хорошо понимала Анна. Она давно видела во сне этот страшный день и теперь
            все
            происходило именно так. Но ей никогда не снилось того, что происходило, когда она выбиралась из метро. Она
            помнила только ощущение тихого отчаяния и невыносимую боль.</p>
        <p style="text-align: justify;">Анна как белый призрак продвигалась сквозь толпу к выходу. От сотрясавших землю
            толчков трудно было устоять на ногах. Ледяными руками она прижимала к себе маленькую девочку, которая
            потерялась. С девочкой на руках она шла вдоль дороги подчиняясь скорее интуиции, чем разуму. Вдруг что-то
            страшно ухнуло у нее за спиной. Анна обернулась и увидела растущую трещину метрах в пяти от себя. Она
            бросилась
            бежать с ребенком на руках. Сзади раздался дикий крик отчаявшейся женщины, потерявшей кого-то. Шестым
            чувством
            Анна поняла, что это мать девочки, с которой она убегала. Имени девочки она не разбирала, но слышала крик
            этой
            женщины где-то внутри своего подсознания. Крепче прижав девочку она обернулась. Ее глаза и женщины
            встретились.
            Увидев свою дочку в безопасности, женщина как-то устало остановилась.&nbsp;</p>
        <p style="text-align: justify;">&hellip;Анна запомнила только благодарность в глазах и произнесенное одними
            губами
            имя девочки&hellip; Машенька&hellip;</p>
        <p style="text-align: justify;">&hellip;Солнце садилось.&nbsp; В его уходящих лучах еще виден был не
            закончившийся
            кошмар. Анна в этот момент брела где-то за пределами города. Ни одной живой души. Впереди, казалось, тоже
            погуляла смерть.</p>
        <p style="text-align: justify;">&nbsp;</p>
        <p style="text-align: justify;"><em>1998</em></p>
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