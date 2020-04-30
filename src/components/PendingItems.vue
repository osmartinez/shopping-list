<template>
    <div>
        <p></p>
        <div v-if="sinComprar!=0" class="text-center alert alert-info">Quedan {{sinComprar}} items por comprar</div>
        <div v-else class="text-center alert alert-warning">No quedan items sin comprar</div>
    </div>
</template>

<script>
    export default {
//    template: '#pending-items-tmpl',
        props: ['items'],
        computed: {
            sinComprar: function () {
                return this.items.reduce(function (s, i) {
                    s += !i.comprado
                    return s
                }, 0)
            }
        }
    }
</script>