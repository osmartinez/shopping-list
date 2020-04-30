<template>
    <div class="footer">
        <hr/>
        <em>Cambia el título aquí:</em>
        <input v-model="titleAux" @input="propagaNuevoTitulo">
    </div>
</template>

<script>
    export default {
        name: "ChangeTitle",
        // template: '#change-title-tmpl',
        props: ['newTitle'], // ojo camel case
        data() {
            return {titleAux: this.newTitle}
        },
        methods: {
            propagaNuevoTitulo: function (evt) {
                this.$emit('update:newTitle', evt.target.value)
            }
        },
        filters: {
            capitalize: function (value) {
                if (!value) return ''
                value = value.toString()
                return value.charAt(0).toUpperCase() + value.slice(1)
            }
        }
    }
</script>

<style scoped>

</style>