<template>
    <div class="table">
        <div class="table__header">
            <div class="header__title">
                Название
            </div>
        </div>
        <div class="table__body">
            <table class='table__block'>
                <thead>
                    <tr>
                        <slot name="thead" />
                    </tr>
                </thead>

                <tbody>
                    <slot name="tbody" />
                </tbody>
            </table>
        </div>
        <div class="table__footer">
            <div class="footer__total">
                Итого 20 из 20
            </div>
        </div>
    </div>
</template>

<script setup lang="ts">


</script>

<style lang="scss" >

</style>