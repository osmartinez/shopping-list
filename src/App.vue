<template>
  <div class="container" id="app"> <!-- Se puede quitar id="app" (ahora está en index.html)-->
    <h2>{{ title || capitalize}}</h2>
    <add-item v-on:nuevoitem="aniadeItem"></add-item>
    <pending-items :items="items"></pending-items>
    <item-list :items="items"></item-list>
    <change-title :new-title.sync="title"></change-title>
  </div>
</template>

<script>
    import ChangeTitle from './components/ChangeTitle'
    import ItemList from './components/ItemList'
    import PendingItems from './components/PendingItems'
    import AddItem from './components/AddItem'
    import mixin from './mixins'

    export default {
        components: {
            ChangeTitle, // OJO !! Notación ES6
            ItemList,
            PendingItems,
            AddItem
        },
        mixins: [mixin],
        data: function () {  // OJO UNA FUNCION
            return {
                title: 'Mi lista de la compra',
                items: [{nombre: 'Pan', comprado: false},
                    {nombre: 'Leche', comprado: false}]
            }
        },
        methods: {
            aniadeItem: function (nuevoItem) {
                var name = this.$options.filters.capitalize(nuevoItem)
                this.items.push({nombre: name, comprado: false})
            }
        }
    }
</script>

<style scoped>
  .container {
    width: 40%;
    margin: 20px auto 0px auto;
  }
  .footer {
    font-size: 0.7em;
    margin-top: 20vh;
  }
</style>