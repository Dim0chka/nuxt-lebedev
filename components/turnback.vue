<template>
    <NuxtLink to="https://www.artlebedev.ru/express-design/" class="wrapper">
        <svg width="32" height="32" viewBox="0 0 32 32" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path d="M14 6L5 15.5L14 25" stroke-width="3"/>
        </svg>
        <span>
            К профилю
        </span>    
    </NuxtLink>
</template>

<style lang="scss" scoped>
.wrapper {
    display: inline-flex;
    align-items: self-end;
    text-decoration: none;
    

    & svg {
        width: 32px;
        height: 32px;
        stroke: $primary;
        transition: all 1s;

        @media (max-width: 600px) {
            width: 16px;
            height: 16px;
        }
    }

    & span {
        color: $primary;
        font-size: 20px;
        font-weight: 400;
        line-height: 130%; 
        transition: all 1s;

        @media (max-width: 600px) {
            font-size: 12px;
            line-height: 100%;
        }

    }

    &:hover {
        & span {
            color: $hover;
        }

        & svg {
            stroke: $hover;
        }
    }
}

    
</style>