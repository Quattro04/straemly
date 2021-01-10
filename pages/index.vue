<template>
        <div class="flex justify-center items-center flex-wrap w-screen h-screen">
            <!-- <div v-for="(stream, idx) in streams" :key="idx" :id="'twitch-embed-' + idx" :class="getWidth + ' ' + getHeight"></div> -->
            <div v-if="streams.length === 0" class="flex flex-col items-center">
                <h1 class="title">straemly</h1>
                <h2 class="subtitle w-3/4 text-center">select the layout by hovering the mouse on the left side of the screen<br>{{'<='}}</h2>
            </div>
            <div v-else class="flex flex-1 h-full">
                <div v-if="layout === 1" class="flex flex-1">
                    <div class="stream flex-1 flex justify-center items-center " :class="[{live: streams[0].streaming}]">
                        <div v-if="streams[0].streamer.length > 0" id="twitch-embed-0" :class="[{'w-full h-full': streams[0].streaming, hidden: !streams[0].streaming}]"></div>
                        <form class="form" v-if="!streams[0].streaming" @submit.prevent="startStream(0)">
                            <input class="input" placeholder="Streamer username" v-model="streams[0].streamer"/>
                            <button v-if="streams[0].streamer.length > 0" class="button">Start</button>
                        </form>
                    </div>
                </div>
                <div v-if="layout === 2" class="flex flex-1 flex-col">
                    <div class="stream flex-1 flex justify-center items-center " :class="[{live: streams[0].streaming}]">
                        <div v-if="streams[0].streamer.length > 0" id="twitch-embed-0" :class="[{'w-full h-full': streams[0].streaming, hidden: !streams[0].streaming}]"></div>
                        <form class="form" v-if="!streams[0].streaming" @submit.prevent="startStream(0)">
                            <input class="input" placeholder="Streamer username" v-model="streams[0].streamer"/>
                            <button v-if="streams[0].streamer.length > 0" class="button">Start</button>
                        </form>
                    </div>
                    <div class="stream flex-1 flex justify-center items-center " :class="[{live: streams[1].streaming}]">
                        <div v-if="streams[1].streamer.length > 0" id="twitch-embed-1" :class="[{'w-full h-full': streams[1].streaming, hidden: !streams[1].streaming}]"></div>
                        <form class="form" v-if="!streams[1].streaming" @submit.prevent="startStream(1)">
                            <input class="input" placeholder="Streamer username" v-model="streams[1].streamer"/>
                            <button v-if="streams[1].streamer.length > 0" class="button">Start</button>
                        </form>
                    </div>
                </div>
                <div v-if="layout === 3" class="flex flex-1">
                    <div class="stream flex-1 flex justify-center items-center " :class="[{live: streams[0].streaming}]">
                        <div v-if="streams[0].streamer.length > 0" id="twitch-embed-0" :class="[{'w-full h-full': streams[0].streaming, hidden: !streams[0].streaming}]"></div>
                        <form class="form" v-if="!streams[0].streaming" @submit.prevent="startStream(0)">
                            <input class="input" placeholder="Streamer username" v-model="streams[0].streamer"/>
                            <button v-if="streams[0].streamer.length > 0" class="button">Start</button>
                        </form>
                    </div>
                    <div class="stream flex-1 flex justify-center items-center " :class="[{live: streams[1].streaming}]">
                        <div v-if="streams[1].streamer.length > 0" id="twitch-embed-1" :class="[{'w-full h-full': streams[1].streaming, hidden: !streams[1].streaming}]"></div>
                        <form class="form" v-if="!streams[1].streaming" @submit.prevent="startStream(1)">
                            <input class="input" placeholder="Streamer username" v-model="streams[1].streamer"/>
                            <button v-if="streams[1].streamer.length > 0" class="button">Start</button>
                        </form>
                    </div>
                </div>
                <div v-if="layout === 4" class="flex flex-1 flex-wrap">
                    <div class="stream flex-w-full flex-1 flex justify-center items-center " :class="[{live: streams[0].streaming}]">
                        <div v-if="streams[0].streamer.length > 0" id="twitch-embed-0" :class="[{'w-full h-full': streams[0].streaming, hidden: !streams[0].streaming}]"></div>
                        <form class="form" v-if="!streams[0].streaming" @submit.prevent="startStream(0)">
                            <input class="input" placeholder="Streamer username" v-model="streams[0].streamer"/>
                            <button v-if="streams[0].streamer.length > 0" class="button">Start</button>
                        </form>
                    </div>
                    <div class="flex flex-w-full">
                        <div class="stream flex-1 flex justify-center items-center " :class="[{live: streams[1].streaming}]">
                            <div v-if="streams[1].streamer.length > 0" id="twitch-embed-1" :class="[{'w-full h-full': streams[1].streaming, hidden: !streams[1].streaming}]"></div>
                            <form class="form" v-if="!streams[1].streaming" @submit.prevent="startStream(1)">
                                <input class="input" placeholder="Streamer username" v-model="streams[1].streamer"/>
                                <button v-if="streams[1].streamer.length > 0" class="button">Start</button>
                            </form>
                        </div>
                        <div class="stream flex-1 flex justify-center items-center " :class="[{live: streams[2].streaming}]">
                            <div v-if="streams[2].streamer.length > 0" id="twitch-embed-2" :class="[{'w-full h-full': streams[2].streaming, hidden: !streams[2].streaming}]"></div>
                            <form class="form" v-if="!streams[2].streaming" @submit.prevent="startStream(2)">
                                <input class="input" placeholder="Streamer username" v-model="streams[2].streamer"/>
                                <button v-if="streams[2].streamer.length > 0" class="button">Start</button>
                            </form>
                        </div>
                    </div>
                </div>
                <div v-if="layout === 5" class="flex flex-1">
                    <div class="stream flex-w-half flex justify-center items-center " :class="[{live: streams[0].streaming}]">
                        <div v-if="streams[0].streamer.length > 0" id="twitch-embed-0" :class="[{'w-full h-full': streams[0].streaming, hidden: !streams[0].streaming}]"></div>
                        <form class="form" v-if="!streams[0].streaming" @submit.prevent="startStream(0)">
                            <input class="input" placeholder="Streamer username" v-model="streams[0].streamer"/>
                            <button v-if="streams[0].streamer.length > 0" class="button">Start</button>
                        </form>
                    </div>
                    <div class="flex flex-col flex-w-half">
                        <div class="stream flex-1 flex justify-center items-center " :class="[{live: streams[1].streaming}]">
                            <div v-if="streams[1].streamer.length > 0" id="twitch-embed-1" :class="[{'w-full h-full': streams[1].streaming, hidden: !streams[1].streaming}]"></div>
                            <form class="form" v-if="!streams[1].streaming" @submit.prevent="startStream(1)">
                                <input class="input" placeholder="Streamer username" v-model="streams[1].streamer"/>
                                <button v-if="streams[1].streamer.length > 0" class="button">Start</button>
                            </form>
                        </div>
                        <div class="stream flex-1 flex justify-center items-center " :class="[{live: streams[2].streaming}]">
                            <div v-if="streams[2].streamer.length > 0" id="twitch-embed-2" :class="[{'w-full h-full': streams[2].streaming, hidden: !streams[2].streaming}]"></div>
                            <form class="form" v-if="!streams[2].streaming" @submit.prevent="startStream(2)">
                                <input class="input" placeholder="Streamer username" v-model="streams[2].streamer"/>
                                <button v-if="streams[2].streamer.length > 0" class="button">Start</button>
                            </form>
                        </div>
                    </div>
                </div>
                <div v-if="layout === 6" class="flex flex-1 flex-wrap">
                    <div class="stream flex-w-half flex justify-center items-center " :class="[{live: streams[0].streaming}]">
                        <div v-if="streams[0].streamer.length > 0" id="twitch-embed-0" :class="[{'w-full h-full': streams[0].streaming, hidden: !streams[0].streaming}]"></div>
                        <form class="form" v-if="!streams[0].streaming" @submit.prevent="startStream(0)">
                            <input class="input" placeholder="Streamer username" v-model="streams[0].streamer"/>
                            <button v-if="streams[0].streamer.length > 0" class="button">Start</button>
                        </form>
                    </div>
                    <div class="stream flex-w-half flex justify-center items-center " :class="[{live: streams[1].streaming}]">
                        <div v-if="streams[1].streamer.length > 0" id="twitch-embed-1" :class="[{'w-full h-full': streams[1].streaming, hidden: !streams[1].streaming}]"></div>
                        <form class="form" v-if="!streams[1].streaming" @submit.prevent="startStream(1)">
                            <input class="input" placeholder="Streamer username" v-model="streams[1].streamer"/>
                            <button v-if="streams[1].streamer.length > 0" class="button">Start</button>
                        </form>
                    </div>
                    <div class="stream flex-w-half flex justify-center items-center " :class="[{live: streams[2].streaming}]">
                        <div v-if="streams[2].streamer.length > 0" id="twitch-embed-2" :class="[{'w-full h-full': streams[2].streaming, hidden: !streams[2].streaming}]"></div>
                        <form class="form" v-if="!streams[2].streaming" @submit.prevent="startStream(2)">
                            <input class="input" placeholder="Streamer username" v-model="streams[2].streamer"/>
                            <button v-if="streams[2].streamer.length > 0" class="button">Start</button>
                        </form>
                    </div>
                    <div class="stream flex-w-half flex justify-center items-center " :class="[{live: streams[3].streaming}]">
                        <div v-if="streams[3].streamer.length > 0" id="twitch-embed-3" :class="[{'w-full h-full': streams[3].streaming, hidden: !streams[3].streaming}]"></div>
                        <form class="form" v-if="!streams[3].streaming" @submit.prevent="startStream(3)">
                            <input class="input" placeholder="Streamer username" v-model="streams[3].streamer"/>
                            <button v-if="streams[3].streamer.length > 0" class="button">Start</button>
                        </form>
                    </div>
                </div>
            </div>


            <LayoutMenu @layout="selectLayout"/>
            <!-- <Menu @action="menuAction"/> -->
            <!-- <Popup @submit="addStream" ref="popup" /> -->
        </div>
</template>

<script>
export default {
    data() {
        return {
            streamWidth: "100%",
            streamHeight: "100%",
            streams: [],
            layout: 0
        }
    },
    computed: {
        getWidth() {
            if (this.streams.length === 1) return 'w-full'
            else return 'w-1/2'
        },
        getHeight() {
            if (this.streams.length < 3) return 'h-full'
            else return 'h-1/2'
        }
    },
    methods: {
        selectLayout(layout) {
            switch (layout) {
                case 1: 
                    this.streams = [
                        {
                            streamer: '',
                            type: 'twitch',
                            streaming: false
                        }
                    ]
                    break;
                case 2:
                case 3:
                    this.streams = [
                        {
                            streamer: '',
                            type: 'twitch',
                            streaming: false
                        },
                        {
                            streamer: '',
                            type: 'twitch',
                            streaming: false
                        }
                    ]
                    break;
                case 4:
                case 5:
                    this.streams = [
                        {
                            streamer: '',
                            type: 'twitch',
                            streaming: false
                        },
                        {
                            streamer: '',
                            type: 'twitch',
                            streaming: false
                        },
                        {

                            streamer: '',
                            type: 'twitch',
                            streaming: false
                        }
                    ]
                    break;
                case 6: 
                    this.streams = [
                        {
                            streamer: '',
                            type: 'twitch',
                            streaming: false
                        },
                        {
                            streamer: '',
                            type: 'twitch',
                            streaming: false
                        },
                        {
                            streamer: '',
                            type: 'twitch',
                            streaming: false
                        },
                        {
                            streamer: '',
                            type: 'twitch',
                            streaming: false
                        }
                    ]
                    break;
            }
            this.layout = layout
        },
        startStream(id) {
            console.log(JSON.stringify(this.streams))
            this.streams[id].streaming = true;
            console.log(JSON.stringify(this.streams))

            new Twitch.Embed(`twitch-embed-${id}`, {
                width: "100%",
                height: "100%",
                channel: this.streams[id].streamer,
                // only needed if your site is also embedded on embed.example.com and othersite.example.com 
                // parent: ["embed.example.com", "othersite.example.com"]
            });
        }
        // menuAction(action) {
        //     switch (action) {
        //         case 'add':
        //             this.$refs.popup.open();
        //             break;
        //     }
        // },
        // addStream(username) {
        //     this.streams = this.streams.concat([{streamer: username, type: 'twitch'}])
        //     console.log(this.streams)
        //     setTimeout(() => {
        //         new Twitch.Embed(`twitch-embed-${this.streams.length - 1}`, {
        //             width: this.streamWidth,
        //             height: this.streamHeight,
        //             channel: this.streams[this.streams.length - 1].streamer,
        //             // only needed if your site is also embedded on embed.example.com and othersite.example.com 
        //             // parent: ["embed.example.com", "othersite.example.com"]
        //         });
        //     }, 100)
        // }
    },
    // watch: {
    //     streams(oldStreams, newStreams) {
    //         console.log('NEW: ', newStreams)
    //         setTimeout(() => {
    //             new Twitch.Embed(`twitch-embed-${newStreams.length - 1}`, {
    //                 width: this.streamWidth,
    //                 height: this.streamHeight,
    //                 channel: newStreams[newStreams.length - 1].streamer,
    //                 // only needed if your site is also embedded on embed.example.com and othersite.example.com 
    //                 // parent: ["embed.example.com", "othersite.example.com"]
    //             });
    //         }, 100)
    //     }
    // }
}
</script>

<style lang="scss">
.title {
    font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
    display: block;
    font-weight: 300;
    font-size: 100px;
    letter-spacing: 1px;
    color: #41b883;
}
.subtitle {
    font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
    font-weight: 300;
    font-size: 42px;
    color: #526488;
    word-spacing: 5px;
    padding-bottom: 15px;
}
.stream {
    border: 3px solid #41b883;
    &.live {
        border: none;
    }
}
.form {
    width: 400px;
    display: flex;
    .input {
        flex: 1 1 0;
        padding: 12px 16px;
        border-radius: 10px;
        background-color: #102938;
        color: white;
        &:focus {
            outline: none;
        }
    }
    .button {
        border-radius: 10px;
        padding: 12px 25px;
        color: white;
        background-color: #41b883;
        margin-left: 10px;
        &:focus {
            outline: none;
        }
    }
}
</style>
