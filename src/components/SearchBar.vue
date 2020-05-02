<template>
    <div class='header'>
        <div class="ui container">
            <div class="ui segment">
                <form class="ui form" @submit.prevent="onSubmit">
                    <div class="field">
                        <label>Search on YouTube</label>
                        <input type="text" placeholder="What are you looking for?" v-model="inputField">
                    </div>
                </form>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                inputField: '',
            }
        },
        methods: {
            onSubmit() {
                this.$emit('onInputChange', this.inputField);
                this.inputField = '';
            }
        }
    }
</script>

<style>
.header {
    margin: 20px 0;
}
</style>