<template>
    <div id="title" @click="titleClick">
        <div id="titleStr">
            {{ realTitle }}
            {{ newTitle }}
        </div>
        <div id="titleSlot">
<!--            https://cn.vuejs.org/v2/guide/components-slots.html-->
            <slot name="w" :wSlot="wStr"></slot>
            <slot name="b" :bSlot="bStr"></slot>
        </div>
    </div>
</template>

<script>
    import { EventBus as eb } from '../utils/EventBus'

    export default {
        name: "Title",
        props: ['titleContent'],
        data: function() {
            return {
                'realTitle': this.titleContent,
                'newTitle': this.titleContent,
                'wStr': 'whiteSlot',
                'bStr': 'blackSlot'
            }
        },
        methods: {
            titleClick: function () {
                // 将这个Title的this先传递到self, 因为eb里面的this是eb自己, 没法用到Title了, 下面接收的地方也是一样
                const this_ = this;
                // 这里的$emit里的就不再视作一个给上级组件调用的方法了, 而是可以视作消息传递的topic, 给接收消息的$on订阅使用
                eb.$emit('titleClickEmit', this_.realTitle);
            },
            getEventData: function () {
                const this_ = this;
                eb.$on('titleClickEmit', function (v) {
                    this_.newTitle = v;
                })
            }
        },
        mounted: function () {
            this.getEventData();
        }
    }
</script>

<style scoped>

</style>