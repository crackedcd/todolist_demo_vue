<template>
    <div id="doneList">
        <div id="doneListHeadText">
            {{ doneTitleText }}
        </div>
        <div id="doneListBody">
            <ul>
                <li v-for='(v, k) of this.doneList'
                    :key='v.id'
                    @click='doneClick(k)'
                >
                    {{ v.info }}
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Done",
        props: [
            'doneList'
        ],
        data: function () {
            return {
                'doneTitleText': 'DoneList'
            }
        },
        methods: {
            doneClick: function (k) {
                this.$emit('doneEmit', k);
            }
        }
    }
</script>

<style scoped>

</style>