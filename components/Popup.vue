<template>
    <div class="backdrop absolute top-0 left-0 w-full h-full flex justify-center items-center" :class="opened ? 'flex' : 'hidden'">
        <div class="popup flex flex-col">
            <div class="header flex justify-between p-5 bg-light">
                <p class="text-blue text-xl font-bold">Add stream</p>
                <font-awesome-icon class="text-3xl text-blue cursor-pointer" :icon="['fa', 'times']" @click="opened=false" />
            </div>
            <div class="body flex flex-col p-5 bg-light">
                <form @submit.prevent="submit">
                    <input class="input" placeholder="Streamer username" v-model="username" />
                    <button class="button p-5 mt-3 bg-green">Add</button>
                </form>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            opened: false,
            username: ''
        }
    },
    methods: {
        open() {
            this.opened = true
        },
        submit() {
            this.opened = false
            this.$emit('submit', this.username)
        }
    }
}
</script>

<style lang="scss">
    .backdrop {
        background: rgba(0,0,0,0.7);
    }
    .popup {
        width: 400px;
        font-family: 'Raleway', sans-serif;
        .header {
            border-radius: 20px 20px 0 0;
            border-bottom: 1px solid #f9f9fa;
        }
        .body {
            border-radius: 0 0 20px 20px;
            .input {
                width: 100%;
                padding: 12px 16px;
                border-radius: 10px;
                background-color: #f9f9fa;
                color: #526488;
                &:focus {
                    outline: none;
                }
            }
            .button {
                border-radius: 10px;
                padding: 12px 16px;
                color: white;
                &:focus {
                    outline: none;
                }
            }
        }
    }
</style>