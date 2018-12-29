<template>
    <div>
        <!--<transition name="fade" appear>-->
        <transition :css="false" @enter="enter" @leave="leave" mode="out-in">
            <div class="ui message success" v-if="visible" key="visible">
                Quod si rectum statuerimus vel concedere amicis, quidquid velint, vel impetrare ab iis, quidquid velimus, perfecta quidem sapientia si simus, nihil habeat res vitii; sed loquimur de iis amicis qui ante oculos sunt, quos vidimus aut de quibus memoriam accepimus, quos novit vita communis. Ex hoc numero nobis exempla sumenda sunt, et eorum quidem maxime qui ad sapientiam proxime accedunt.
            </div>
            <div class="ui message success" v-else key="invisible">
                si rectum statuerimus vel concedere amicis, quidquid velint, vel impetrare ab iis, quidquid velimus, perfecta quidem sapientia si simus, nihil habeat res vitii; sed loquimur de iis amicis qui ante oculos sunt, quos vidimus aut de quibus memoriam accepimus, quos novit vita communis. Ex hoc numero nobis exempla sumenda sunt, et eorum quidem maxime qui ad sapientiam proxime accedunt.
            </div>
        </transition>

        <button @click="toggle">Toggle</button>


        <transition-group name="fade" tag="ul">
            <li v-for="item in items" :key="item">{{ item }}</li>
        </transition-group>

        <button class="ui button" @click="add">Ajouter</button>
        <button class="ui button error" @click="shuffle">Shuffle</button>

    </div>
</template>

<script>

    let slides = {
        methods: {
            enter: function (el, done) {
                $(el).hide().slideDown(500, done);
            },
            leave: function (el, done) {
                $(el).show().slideUp(500, done);
            }
        }
    }

    export default {
        name: "Alert",
        mixins: [slides],
        data: function () {
            return {
                visible: true,
                items: [1, 2, 3, 4]
            }
        },
        methods: {
            add: function () {
                this.items.push(Math.floor(Math.random() * 10))
            },
            shuffle: function(){
                this.items = [2,3,1,4,6]
            },
            toggle: function () {
                this.visible = !this.visible
            }
        }
    }
</script>

<style scoped>

    .fade-move {
        transition: transform 2s;
    }

    /* état que l'on va avoir en début et en fin d'animation */
    .fade-enter-active, .fade-leave-active {
        transition: opacity 1s, transform 1s;
    }

    /* au début : .fade-enter --> .fade-enter-active */
    /* à la fin : .fade-leave --> .fade-leave-active */

    /* lorsque tu commences, et lorsque tu finis l'activation du leave*/
    .fade-enter, .fade-leave-active {
        opacity: 0;
        transform: translateX(20px);
    }

</style>