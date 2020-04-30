<template>
    <transition-group  name="list" tag="ul">
        <item v-for="i in alphabetical_items" :key="i.nombre" :item="i"></item>
    </transition-group>
</template>

<script>
    import Item from './Item.vue' // La extensión es opcional

    export default {
//  template: '#item-list-tmpl',
        components: {
            Item // OJO !! Notación ES6 --> Item: Item
        },
        props: ['items'],
        computed: {
            alphabetical_items: function () {
                var arrAux = this.items.slice()
                return arrAux.sort((a, b) => a.nombre > b.nombre)
            }
        },

    }
</script>
```
#### Añadir estilos en `ItemList.vue`
Añade al final de `ItemList.vue`
```
<style scoped>
    .list-enter-active {
        transition: all 1s;
    }
    .list-enter {
        opacity: 0;
        transform: translateX(30px);
    }
    .list-leave-active {
        transition: opacity 0.5s;
    }
    .list-leave-to {
        opacity: 0;
    }


</style>