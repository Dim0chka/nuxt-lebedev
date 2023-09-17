<template>
    <nav class="nav">
        <div class="container">
            <turnback/>
        </div>
    </nav>
    <section>
        <div class="container">
            <div class="title">
                <img src="@/assets/img/logo.svg" alt="">
                <h1 class="h2">
                    <span>
                        Скидки
                        <br class="title-gap">
                        и бонусы
                    </span>
                    <br>
                    <span>для клиентов Журналуса</span>
                </h1>
            </div>

            
        <div class="grid-container">
            <div class="item1" @click="clickPromo(0)">
                <div class="item-img-holder"></div>
                <div class="block2">
                    <div class="block-text">
                        <span>Николай Иронов</span>
                        <h2>Скидка на подписку нейросети Николай Иронов</h2>
                        <div class="line"></div>
                        <span>Мгновенно создаёт крутую айдентику, учитывая особенности каждого бизнеса.</span>
                    </div>
                    <button :disabled="Promo[0].active" class="btn">
                        <span v-if="Promo[0].active === false">SDXPD13</span>
                        <span v-else>Промо-код скопирован</span>
                    </button>
                </div>
            </div>

            <div class="item2" @click="clickPromo(1)">
                <img src="@/assets/img/card-logo-1.svg" alt="">
                <div class="block">
                    <div class="block-text">
                        <span>Интранетус</span>
                        <h2>Три бесплатных месяца на простой планировщик дел</h2>
                        <div class="line"></div>
                        <span>Простой инструмент для деловых встреч, внутреннего общения и управления процессами.</span>
                    </div>
                    <button :disabled="Promo[1].active" class="btn">
                        <span v-if="Promo[1].active === false">SDXPD13</span>
                        <span v-else>Промо-код скопирован</span>
                    </button>
                </div>
            </div>
            <div class="item3" @click="clickPromo(2)">
                <img src="@/assets/img/card-logo-2.svg" alt="">
                <div class="block">
                    <div class="block-text">
                        <span>naray.one</span>
                        <h2>10% скидка на онлайн-генератор мерча для всех точек мира</h2>
                        <div class="line"></div>
                        <span>Простой инструмент для создания уникального мерча любимого района.</span>
                    </div>
                    <button :disabled="Promo[2].active" class="btn">
                        <span v-if="Promo[2].active === false">SDXPD13</span>
                        <span v-else>Промо-код скопирован</span>
                    </button>
                </div>
            </div>
            <div class="item4" @click="clickPromo(3)">
                <img src="@/assets/img/card-logo-3.svg" alt="">
                <div class="block">
                    <div class="block-text">
                        <span>DashaMail</span>
                        <h2>Полугодовая подписка на email-рассылку</h2>
                        <div class="line"></div>
                        <span>Чудесная компания, занимающейся рассылкой электронной почты.</span>
                    </div>
                    <button :disabled="Promo[3].active" class="btn">
                        <span v-if="Promo[3].active == false">SDXPD13</span>
                        <span v-else>Промо-код скопирован</span>
                    </button>
                </div>
            </div>
        </div>

        </div>
    </section>
</template>

<script setup>
import {ref} from 'vue'

const Promo = ref([
    {promo: 'SDXPD13', to: 'https://ironov.artlebedev.com/ru', active: false},
    {promo: 'SDXPD13', to: 'https://www.artlebedev.ru/intranetus/', active: false},
    {promo: 'SDXPD13', to: 'https://naray.one/', active: false},
    {promo: 'SDXPD13', to: 'https://dashamail.ru/', active: false},
])


function toggleActive(index) {
      for (let i = 0; i < Promo.value.length; i++) {
        if (i !== index) {
          Promo.value[i].active = false;
        }
      }
      Promo.value[index].active = true
}



async function clickPromo(id) {
    try {
      toggleActive(id)
      await navigator.clipboard.writeText(Promo.value[id].promo);
      setTimeout(() => {
        if (Promo.value[id].active) {
            window.open(Promo.value[id].to, '_blank')
            Promo.value[id].active = false
        }
      }, 3000);
    } catch($e) {
        console.log($e)
      alert('Cannot copy');
    }
}

</script>


<style lang="scss">
.container {
    max-width: 1218px;
    margin: 0 auto;
    padding: 0 8px;
}

.nav {
    margin-top: 69px;
    margin-bottom: 33px;

    @media (max-width: 600px) {
        margin-top: 32px;
        margin-bottom: 32px;
    }
}

.title {
    display: flex;
    padding-top: 2px;
    align-items: flex-start;
    gap: 20px;
    margin-bottom: 45px;

    @media (max-width: 800px) and (min-width: 600px)  {
        align-items: center;
    }

    @media (max-width: 600px) {
        flex-direction: column;
        gap: 24px;
        padding-top: 0;
    }

    img {
        @media (max-width: 800px) {
            width: 85px;
            height: 78px;
        }
    }

    .h2 {
        margin-top: 7px;
        font-weight: 900;
        line-height: 48px;
        text-align: left;
        font-size: 48px;
    
        @media (min-width: 1200px) {
            margin-left: 5.5rem;
            transform: scaleX(1.3);
        }

        .title-gap {
            display: none;
    
            @media (max-width: 410px) {
                display: inline;
            }
        }
        
        @media (max-width: 800px) {
            margin-left: 0;
            transform: none;
            margin-top: 4px;
    
            font-size: 32px;
            line-height: 28px;
        }

        & > span:first-child {
            font-stretch: 150%;
            background-color: color(display-p3 0 1 0.098);
            color: color(display-p3 0 0 0);
            padding-right: 2.5px;
            -webkit-box-decoration-break: clone;
            box-decoration-break: clone;  

            @media (min-width: 410px) {
                padding-top: 2px;
            }
        }
    
            & > span:last-child {
                font-stretch: 150%;
                padding-top: 4px;
                background-color: white;
    
                @media (max-width: 800px) {
                    padding: 0;
                }
            }
    }

}



.grid-container {
    display: grid;
    grid-template-columns: repeat(2, 1fr); 
    grid-gap: 24px;

    @media (max-width: 1200px) {
        grid-template-columns: 1fr; 
        justify-content: center;
        grid-gap: 12px;
    }

    .item1 {    
        cursor: pointer;
        display: flex;
        justify-content: center;
        align-items: flex-end;
        flex-shrink: 0;
    
        border-radius: 24px;
        width: auto;
        height: 534px;
        overflow: hidden;
        position: relative;

        @media (min-width: 1200px) {
            grid-row-start: 1;
            grid-row-end: 3;
            width: 589px;
            height: 998px;
        }
    
        .item-img-holder {
            width: 100%;
            height: 100%;
            background: linear-gradient(180deg, color(display-p3 0 0 0 / 0.00) 63.67%, color(display-p3 0 0 0 / 0.75) 77.26%), url("assets/img/layout.png");
            background-position: center;
            background-size: cover;
            background-repeat: no-repeat;
            transition: all 1s;
        }
    
        &:hover > .item-img-holder {
            transform: scale(1.2);
        }
        
        &:hover > .block2 .btn {
            background: $hover;
        
            span {
                color: $bg-card;
            }
        
            &:disabled {
                background: $primary2;
        
                span {
                    color: $primary;
                }
            }
        }
    
        .block2 {
            position: absolute;
        
            padding: 24px 24px 32px 24px;
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 32px;
            flex: 1 0 0;
            justify-content: center;
            
            @media (max-width: 1200px) {
                padding: 12px 12px 24px 12px;
                gap: 24px;
            }
            
            .block-text {
                display: flex;
                flex-direction: column;
                justify-content: center;
                align-self: stretch;
                gap: 10px;
        
                span:first-child {
                    color: $span2;
                    font-size: 16px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: 26.429px; 

                    @media (max-width: 1200px) {
                        font-size: 14px;
                    }
                }
        
                .line {
                    background-color: $line;
                    height: 1px;
                    align-self: stretch;
                }
        
                h2 {
                    color: $primary2;
                    font-size: 28px;
                    font-style: normal;
                    font-weight: 500;
                    line-height: 28px; 

                    @media (max-width: 1200px) {
                        font-size: 24px;
                    }
                }
        
                span:last-child {
                    color: $primary2;
                    font-size: 21px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: 28px;

                    @media (max-width: 1200px) {
                        font-size: 16px;
                    }
                }
            }
        
            .btn {
                display: flex;
                padding: 16px 32px 8px 32px;
                justify-content: center;
                align-items: center;
                gap: 10px;
                border-radius: 8px;
                background: $primary2;
                transition: all 1s;
        
                span {
                    color: #000;
                    color: $primary;
                    font-size: 28px;
                    font-style: normal;
                    font-weight: 500;
                    line-height: 26.429px; 

                    @media (max-width: 1200px) {
                        font-size: 24px;
                    }
                }

            }
        }
    }
    


    .item3 {
        img {
            width: 174px;
            height: 136px;
        }
    }

    .item2 {
        img {
            width: 137px;
            height: 137px;
        }
    }

    .item2, .item3 {
        cursor: pointer;

        display: flex;
        flex-direction: column;
        justify-content: flex-end;
        gap: 32px;
        align-items: center;
        flex-shrink: 0;
        padding: 12px 12px 24px 12px;
        border-radius: 24px;

        border-radius: 24px;
        background: $bg-card;
        width: auto;
        height: 534px;


        @media (min-width: 1200px) {
            width: 589px;
            height: 516px;
            padding: 24px 24px 32px 24px;
        }

        &:hover > img {
            transform: scale(1.2);
        }

        &:hover > .block .btn {
            background: $hover;
        
            span {
                color: $bg-card;
            }
        
            &:disabled {
                background: $primary;
        
                span {
                    color: $bg-card;
                }
            }
        }

        img {
            transition: all 1s;
        }

        .block {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 32px;
            justify-content: center;
    
            .block-text {
                display: flex;
                flex-direction: column;
                justify-content: center;
                align-self: stretch;
                gap: 10px;
    
                span:first-child {
                    color: $span1;
                    font-size: 16px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: 26.429px; 

                    @media (max-width: 1200px) {
                        font-size: 14px;
                    }
                }
    
                .line {
                    background-color: $line2;
                    height: 1px;
                    align-self: stretch;
                }
    
                h2 {
                    color: $primary;
                    font-size: 28px;
                    font-style: normal;
                    font-weight: 500;
                    line-height: 28px; 

                    @media (max-width: 1200px) {
                        font-size: 24px;
                    }
                }
    
                span:last-child {
                    color: $primary;
                    font-size: 21px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: 28px;

                    @media (max-width: 1200px) {
                        font-size: 16px;
                    }
                }
            }
    
            .btn {
                display: flex;
                padding: 16px 32px 8px 32px;
                justify-content: center;
                align-items: center;
                gap: 10px;
                border-radius: 8px;
                background: $primary;
                transition: all 1s;
    
                span {
                    color: $bg-card;
                    font-size: 28px;
                    font-style: normal;
                    font-weight: 500;
                    line-height: 26.429px; /* 94.39% */

                    @media (max-width: 1200px) {
                        font-size: 24px;
                    }
                }
            }
        }
    }

    .item4 {
        cursor: pointer;
    
        display: flex;
        flex-direction: column;
        justify-content: flex-end;
        align-items: center;
        flex-shrink: 0;
        padding: 12px 12px 24px 12px;
    
        border-radius: 24px;
    
        border-radius: 24px;
        background: $bg-card;
        width: auto;
        height: 534px;
    
        @media (min-width: 1200px) {
            gap: 208px;
            padding: 24px 24px 32px 24px;
            width: 589px;
            height: 998px;
            grid-row-start: 2;
            grid-row-end: 4;
        }
    
    
        &:hover > img {
            transform: scale(1.2);
        }
    
        &:hover > .block .btn {
            background: $hover;
        
            span {
                color: $bg-card;
            }
        
            &:disabled {
                background: $primary;
        
                span {
                    color: $bg-card;
                }
            }
        }
    
        img {
            width: 360px;
            height: 265px;
            mix-blend-mode: darken;
            flex-shrink: 0;
            transition: all 1s;
    
            @media (max-width: 1200px) {
                width: 221px;
                height: 162px;
            }
        }
    
        .block {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 32px;
            justify-content: center;
    
            .block-text {
                display: flex;
                flex-direction: column;
                justify-content: center;
                align-self: stretch;
                gap: 10px;
    
                span:first-child {
                    color: $span1;
                    font-size: 16px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: 26.429px; 
    
                    @media (max-width: 1200px) {
                        font-size: 14px;
                    }
                }
    
                .line {
                    background-color: $line2;
                    height: 1px;
                    align-self: stretch;
                }
    
                h2 {
                    color: $primary;
                    font-size: 28px;
                    font-style: normal;
                    font-weight: 500;
                    line-height: 28px; 
    
                    @media (max-width: 1200px) {
                        font-size: 24px;
                    }
                }
    
                span:last-child {
                    color: $primary;
                    font-size: 21px;
                    font-style: normal;
                    font-weight: 400;
                    line-height: 28px;
    
                    @media (max-width: 1200px) {
                        font-size: 16px;
                    }
                }
            }
    
            .btn {
                display: flex;
                padding: 16px 32px 8px 32px;
                justify-content: center;
                align-items: center;
                gap: 10px;
                border-radius: 8px;
                background: $primary;
                transition: all 1s;
    
                span {
                    color: $bg-card;
                    font-size: 28px;
                    font-style: normal;
                    font-weight: 500;
                    line-height: 26.429px; /* 94.39% */
    
                    @media (max-width: 1200px) {
                        font-size: 24px;
                    }
                }
            }
        }
    }
}
  

  

</style>