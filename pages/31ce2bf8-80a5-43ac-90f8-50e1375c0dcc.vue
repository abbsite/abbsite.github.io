<template>
    <p>&nbsp;</p>
    <p><img class="ui centered medium rounded image" :src="url"></p>
    <div class="ui container">
        <h3 class="pt-8">
            <div class="ui basic fitted segment mceNonEditable">
                <div class="content">
                    <div style="font-family: Arsenal, sans-serif;"
                        class="ui header hvr-icon-wobble-vertical massive dividing fluid container"><i
                            style="vertical-align:top;padding-top:0.3em;" class="hvr-icon icon"
                            :class="page.i"></i><span class="ui content">{{ page.title }}<span
                                class="sub header"></span></span></div>
                </div>
            </div>
        </h3>
        <p>&nbsp;</p>
        <p style="text-align: justify;">Однажды жители деревни Константиново, что в витебской области<span
                class="Apple-converted-space">&nbsp;</span>глубокского района, столкнулись с удивительной проблемой...
            Их
            предки, давно погребённые на местном кладбище, нашли способ выкапываться и устраивать себе каникулы. Предки,
            надо отдать им должное, нрава были доброго и никого не доставали. Их любимым и единственным занятием на
            подобных
            каникулах были обильные застолья. Жители деревни и их потусторонние гости не сразу нашли общий язык. Но зато
            после долгих переговоров решено было в определённые дни пускать гостей в местное кафе, где они пили-ели, а
            потом
            обнявшись, разбредались парами обратно в сторону кладбища, распевая при этом старые песни.</p>
        <p style="text-align: justify;">И всё было бы хорошо, но давно погребённые гуляки никак не могли привыкнуть к
            современным трассам. Для них было дикостью скоростное шоссе и несущиеся по нему машины. Поэтому, как ни
            пытались
            образумить их современные жители, а всё равно довольно часто неспешное шествование через дорогу
            заканчивалось
            печально... Очередной подвыпивший покойник становился причиной ДТП.</p>
        <p style="text-align: justify;">Но как объяснить водителю, перепуганному насмерть, что сбитый им пешеход итак
            мёртв
            уже несколько десятилетий, а то и столетий? Долго деревенские жители ломали голову...</p>
        <p style="text-align: justify;">И наконец они придумали, как поступить. У дороги, как раз рядом с кладбищем, в
            месте, где обычно подвыпившие покойники возвращались к свои могилам, жители деревни поставили большущий
            дорожный
            знак, на котором изобразили обнявшуюся навеселе пару силуэтов и надпись: Внимание! Невнимательные пешеходы!*
        </p>
        <p style="text-align: justify;">* оригинальное фото отсутствует, взято фото из сети</p>
        <p><em>Витебск, 2012</em></p>
        <router-link :to="page.parent.to" class="ui labeled icon blue button mceNonEditable"
            style="font-family: Arsenal, sans-serif;"><i class="left arrow icon"></i>назад</router-link>
    </div>
</template>

<script setup>
import { inject } from "vue";

const { id } = defineProps(["id"]),
    page = inject("pages")[id],
    [{ url }] = page.images;

</script>