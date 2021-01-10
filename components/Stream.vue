<template>
    <div class="stream flex justify-center items-center" :class="[{live: stream.streaming, [extraClass]: extraClass}]">
        <div v-if="stream.streamer.length > 0" :id="'twitch-embed-' + id" :class="[{'w-full h-full': stream.streaming, hidden: !stream.streaming}]"></div>
        <form class="form flex flex-col" v-if="!stream.streaming" @submit.prevent="$emit('submit', id)">
            <div class="flex items-center mb-3">
                <input class="input" placeholder="Streamer username" v-model="stream.streamer"/>
                <span class="text-white ml-3 mr-1 text-lg">Chat:</span>
                <label class="switch">
                    <input type="checkbox" :checked="stream.chat ? true : false" @change="$emit('chatChange', id)">
                    <span class="slider round"></span>
                </label>
            </div>
            <button v-if="stream.streamer.length > 0" class="button">Start</button>
        </form>
    </div>
</template>

<script>
export default {
    props: {
        stream: Object,
        id: Number,
        extraClass: String,
    }
}
</script>