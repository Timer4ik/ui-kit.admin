<template>
    <aside class="aside">
        <div class="aside__logo">
            <img
                width={150}
                height={100}
                src="~/assets/img/header/logo.svg"
                alt=""
            />
        </div>
        <nav class="aside__navbar">

            <div class="navbar__item item">
                <div class="item__title">
                    <img
                        width={0}
                        height={0}
                        src="~/assets/img/icons/content.svg"
                        alt=""
                    />
                    <div>Контент</div>
                </div>
                <div class="item__list">
                    <NuxtLink
                        class="item__link"
                        to="/"
                    >
                        Подконтент
                    </NuxtLink>
                    
                </div>
            </div>
        </nav>
    </aside>
</template>
