<template>

    <div class="counter">
        {{ count }}
    <button class="btn-counter" @click="increment">+</button>
    </div>

</template>

<script>
    import store from './store/NotificationsStore'
    export default {
        name: "Counter",
        data: function() {
            return {
                state: store.state
            }
        },
        computed: {
            count: function () {
                return this.state.count
            }
        },
        methods: {
            increment: function () {
                store.increment()
            }
        }
    }
</script>

<style scoped>
    .counter {
        font-weight: bold;
        width: 20px;
        text-align: center;
    }
</style>