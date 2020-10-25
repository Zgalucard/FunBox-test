<template>
    <div class="main">
        <div class="main__title">
            <h1>Ты сегодня покормил кота?</h1>
        </div>
        <div class="main__cards">
            <MainCard :card="card" v-for="card of cards"></MainCard>
        </div>
    </div>
</template>

<script>
    const MainCard = () => import('@/components/MainCard.vue')

    const card = (img, imgSelected, imgDisabled, title, subtitle, text, weight, subtext, selected, disable, hover) => ({
        img,
        imgSelected,
        imgDisabled,
        title,
        subtitle,
        text,
        weight,
        subtext,
        selected,
        disable,
        hover
    });

    const img = require('@/assets/Back.png');
    const imgSelected = require('@/assets/BackSelected.png');
    const imgDisabled = require('@/assets/BackDisabled.png');
    const cards = [
        card(img,
            imgSelected,
            imgDisabled,
            'Нямушка',
            'с фуа-гра',
            '10 порций мышь в подарок',
            '0,5',
            'Печень утки разварная с артишоками.',
            false,
            false,
            false),
        card(img,
            imgSelected,
            imgDisabled,
            'Нямушка',
            'с рыбой',
            '40 порций 2 мыши в подарок',
            '2',
            'Головы щучьи с чесноком да свежайшая сёмгушка.',
            false,
            false,
            false),
        card(img,
            imgSelected,
            imgDisabled,
            'Нямушка',
            'с курой',
            '100 порций 5 мышей в подарок заказчик доволен',
            '5',
            'Филе из цыплят с трюфелями в бульоне.',
            false,
            true,
            false),
    ]

    export default {
        name: "Main",
        components: {
            MainCard
        },
        data() {
            return {
                cards: cards
            }
        }
    }
</script>

<style lang="scss">
    .main {
        background: url("~@/assets/Pattern.png");
        width: 100%;
        min-height: 100vh;
        overflow: hidden;

        display: flex;
        align-items: center;

        flex-direction: column;
        justify-content: center;

        &__title {
            margin-bottom: 30px;

            h1 {
                font-family: Exo2 .0;
                font-size: 36px;
                line-height: 44px;
                text-align: center;
                color: #FFFFFF;
                text-shadow: 0px 1px 1px #000000;
            }
        }

        &__cards {
            max-width: 1280px;
            margin: 0 auto;
            display: flex;
            width: 100%;
            justify-content: space-around;

            padding: 0 10px;
            flex-wrap: wrap;
        }
    }
</style>