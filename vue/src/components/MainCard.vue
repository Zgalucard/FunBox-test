<template>
    <div class="main__card" :class="card.disable ? 'main__card-disable' : card.selected ? 'main__card-selected' : ''">
        <div class="img-main__card">
            <img :src="[card.disable ? card.imgDisabled : card.selected ? card.imgSelected : card.img]" alt="">
        </div>
        <div class="text-main__card" @click="cardSelect" @mouseleave="cardSelectHover" :class="card.selected && card.hover ? 'main__card-hover' : ''">
        <div class="top-main__card">
            <p v-show="!card.hover">Сказочное заморское явство</p>
            <p v-show="card.hover">Котэ не одобряет?</p>
        </div>
        <div class="body-main__card">
            <h1>{{ card.title }}</h1>
            <h2>{{ card.subtitle }}</h2>
            <p>{{ card.text }}</p>
        </div>
        <div class="bottom-main__card">
            <h1>{{ card.weight }}</h1>
            <h1>кг</h1>
        </div>
        </div>
        <div class="out-main__card">
            <p>Чего сидишь? Порадуй котэ, <span @click="cardSelect">купи.</span></p>
            <p v-show="card.selected && !card.disable">{{ card.subtext }}</p>
            <p v-show="card.disable">Печалька, {{ card.subtitle }} закончился.</p>
        </div>
    </div>
</template>

<script>
    export default {
        name: "MainCard",
        props: {
            card: Object
        },
        data() {
            return {}
        },
        methods:{
            cardSelect(){
                this.card.selected = !this.card.selected
            },
            cardSelectHover(){
                if(this.card.selected) setTimeout(() => this.card.hover = !this.card.hover, 500)
            }
        }
    }
</script>

<style lang="scss" scoped>
    .main__card {
        position: relative;
        max-width: 320px;
        width: 100%;
        margin: 0 10px;

        .img-main__card{
            position: relative;

            img{
                max-width: 100%;
            }
        }

        .text-main__card{
            position: absolute;
            top: 0px;
            padding: 20px 16px 20px 50px;
            width: 100%;
            display: flex;
            flex-direction: column;
            max-height: 480px;
            height: 100%;
        }

        .top-main__card {
            p{
                font-family: Trebuchet MS;
                font-style: normal;
                font-weight: normal;
                font-size: 16px;
                line-height: 19px;
                color: #666666;
            }
            /*position: absolute;*/
        }

        .body-main__card {
            flex: 1 1 auto;
            h1{
                font-family: Trebuchet MS;
                font-style: normal;
                font-weight: bold;
                font-size: 48px;
                line-height: 56px;
                color: #000000;

                margin: 15px 0;
            }
            h2{
                font-family: Trebuchet MS;
                font-style: normal;
                font-weight: bold;
                font-size: 24px;
                line-height: 28px;
                color: #000000;

                margin-bottom: 18px;
            }
            p{
                font-family: Trebuchet MS;
                font-style: normal;
                font-weight: bold;
                font-size: 14px;
                line-height: 16px;
                color: #666666;

                max-width: 130px;
            }
            /*position: absolute;*/
        }

        .bottom-main__card {
            width: 80px;
            height: 80px;
            background: #2EA8E6;
            border-radius: 50%;

            margin-left: auto;

            display: flex;
            text-align: center;
            flex-direction: column;
            justify-content: flex-end;
            padding: 0 0 12px 0;

            h1{
                font-family: Trebuchet MS;
                font-style: normal;
                font-weight: normal;
                font-size: 42px;
                line-height: 22px;
                color: #FFFFFF;

                width: 60px;
                margin: 0 auto;

                &:first-child{
                    margin-bottom: 6px;
                }

                &:last-child{
                    font-size: 21px;
                }
            }
            /*position: absolute;*/
        }

        .out-main__card {
            margin-top: 15px;
            p{
                font-family: Trebuchet MS;
                font-style: normal;
                font-weight: normal;
                font-size: 13px;
                line-height: 15px;
                text-align: center;
                color: #FFFFFF;
            }

            span{
                color: #2EA8E6;
                border-bottom: 1px dashed #2EA8E6;
            }

        }
    }

    .main__card-disable{
        .bottom-main__card{
            background: #B3B3B3;
        }

        .out-main__card{
            p{
                color: #FFFF66;

                &:first-child{
                    display: none;
                }
            }
        }
    }
    .main__card-selected{
        .bottom-main__card{
            background: #E52E7A;
        }

        .out-main__card{
            p{
                &:first-child{
                    display: none;
                }
            }
        }
    }

    .main__card-hover{
        .top-main__card{
            p{
                color: #E52E7A;

                &:first-child{
                    /*display: none;*/
                }
            }
        }
    }
</style>