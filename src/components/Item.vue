<template>
    <li :class="{removed: item.comprado}">
        <div class="checkbox">
            <label>
                <input type="checkbox" v-model="item.comprado"> {{ item.nombre }}</label>
        </div>
    </li>
</template>
<script>
    import mixin from '../mixins'


    export default {
//    template: '#item-tmpl',
        props: ['item'],
        mixins: [mixin]
    }
</script>

<style scoped>
    .removed { color: gray; }
    .removed label { text-decoration: line-through; }
    ul li { list-style-type: none; }
</style>