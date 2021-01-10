<template>
        <div class="flex justify-center items-center flex-wrap w-screen h-screen">
            <!-- <div v-for="(stream, idx) in streams" :key="idx" ::id="'twitch-embed-' + idx" :class="getWidth + ' ' + getHeight"></div> -->
            <div v-if="streams.length === 0" class="flex flex-col items-center">
                <div class="flex">
                    <h1 class="title">mulstream</h1><span class="title blue">.com</span>
                </div>
                <h2 class="subtitle w-3/4 text-center">select the layout by hovering the mouse to the left side of the screen<br>{{'<='}}</h2>
            </div>
            <div v-else class="flex flex-1 h-full">
                <div v-if="layout === 1" class="flex flex-1">
                    <Stream :id="0" :stream="streams[0]" extraClass="flex-1" @submit="startStream" @chatChange="chatChanged" />
                </div>
                <div v-if="layout === 2" class="flex flex-1 flex-col">
                    <Stream :id="0" :stream="streams[0]" extraClass="flex-1" @submit="startStream" @chatChange="chatChanged" />
                    <Stream :id="1" :stream="streams[1]" extraClass="flex-1" @submit="startStream" @chatChange="chatChanged" />
                </div>
                <div v-if="layout === 3" class="flex flex-1">
                    <Stream :id="0" :stream="streams[0]" extraClass="flex-1" @submit="startStream" @chatChange="chatChanged" />
                    <Stream :id="1" :stream="streams[1]" extraClass="flex-1" @submit="startStream" @chatChange="chatChanged" />
                </div>
                <div v-if="layout === 4" class="flex flex-1 flex-wrap">
                    <Stream :id="0" :stream="streams[0]" extraClass="flex-w-full" @submit="startStream" @chatChange="chatChanged" />
                    <div class="flex flex-w-full">
                        <Stream :id="1" :stream="streams[1]" extraClass="flex-1" @submit="startStream" @chatChange="chatChanged" />
                        <Stream :id="2" :stream="streams[2]" extraClass="flex-1" @submit="startStream" @chatChange="chatChanged" />
                    </div>
                </div>
                <div v-if="layout === 5" class="flex flex-1">
                    <Stream :id="0" :stream="streams[0]" extraClass="flex-w-half" @submit="startStream" @chatChange="chatChanged" />
                    <div class="flex flex-col flex-w-half">
                        <Stream :id="1" :stream="streams[1]" extraClass="flex-1" @submit="startStream" @chatChange="chatChanged" />
                        <Stream :id="2" :stream="streams[2]" extraClass="flex-1" @submit="startStream" @chatChange="chatChanged" />
                    </div>
                </div>
                <div v-if="layout === 6" class="flex flex-1 flex-wrap">
                    <Stream :id="0" :stream="streams[0]" extraClass="flex-w-half" @submit="startStream" @chatChange="chatChanged" />
                    <Stream :id="1" :stream="streams[1]" extraClass="flex-w-half" @submit="startStream" @chatChange="chatChanged" />
                    <Stream :id="2" :stream="streams[2]" extraClass="flex-w-half" @submit="startStream" @chatChange="chatChanged" />
                    <Stream :id="3" :stream="streams[3]" extraClass="flex-w-half" @submit="startStream" @chatChange="chatChanged" />
                </div>
                <div v-if="layout === 7" class="flex flex-1 flex-wrap">
                    <Stream :id="0" :stream="streams[0]" extraClass="flex-w-third" @submit="startStream" @chatChange="chatChanged" />
                    <Stream :id="1" :stream="streams[1]" extraClass="flex-w-third" @submit="startStream" @chatChange="chatChanged" />
                    <Stream :id="2" :stream="streams[2]" extraClass="flex-w-third" @submit="startStream" @chatChange="chatChanged" />
                    <Stream :id="3" :stream="streams[3]" extraClass="flex-w-third" @submit="startStream" @chatChange="chatChanged" />
                    <Stream :id="4" :stream="streams[4]" extraClass="flex-w-third" @submit="startStream" @chatChange="chatChanged" />
                    <Stream :id="5" :stream="streams[5]" extraClass="flex-w-third" @submit="startStream" @chatChange="chatChanged" />
                    <Stream :id="6" :stream="streams[6]" extraClass="flex-w-third" @submit="startStream" @chatChange="chatChanged" />
                    <Stream :id="7" :stream="streams[7]" extraClass="flex-w-third" @submit="startStream" @chatChange="chatChanged" />
                    <Stream :id="8" :stream="streams[8]" extraClass="flex-w-third" @submit="startStream" @chatChange="chatChanged" />
                </div>
                <div v-if="layout === 8" class="flex flex-1 flex-wrap">
                    <Stream :id="0" :stream="streams[0]" extraClass="flex-w-quarter" @submit="startStream" @chatChange="chatChanged" />
                    <Stream :id="1" :stream="streams[1]" extraClass="flex-w-quarter" @submit="startStream" @chatChange="chatChanged" />
                    <Stream :id="2" :stream="streams[2]" extraClass="flex-w-quarter" @submit="startStream" @chatChange="chatChanged" />
                    <Stream :id="3" :stream="streams[3]" extraClass="flex-w-quarter" @submit="startStream" @chatChange="chatChanged" />
                    <Stream :id="4" :stream="streams[4]" extraClass="flex-w-quarter" @submit="startStream" @chatChange="chatChanged" />
                    <Stream :id="5" :stream="streams[5]" extraClass="flex-w-quarter" @submit="startStream" @chatChange="chatChanged" />
                    <Stream :id="6" :stream="streams[6]" extraClass="flex-w-quarter" @submit="startStream" @chatChange="chatChanged" />
                    <Stream :id="7" :stream="streams[7]" extraClass="flex-w-quarter" @submit="startStream" @chatChange="chatChanged" />
                    <Stream :id="8" :stream="streams[8]" extraClass="flex-w-quarter" @submit="startStream" @chatChange="chatChanged" />
                    <Stream :id="9" :stream="streams[9]" extraClass="flex-w-quarter" @submit="startStream" @chatChange="chatChanged" />
                    <Stream :id="10" :stream="streams[10]" extraClass="flex-w-quarter" @submit="startStream" @chatChange="chatChanged" />
                    <Stream :id="11" :stream="streams[11]" extraClass="flex-w-quarter" @submit="startStream" @chatChange="chatChanged" />
                    <Stream :id="12" :stream="streams[12]" extraClass="flex-w-quarter" @submit="startStream" @chatChange="chatChanged" />
                    <Stream :id="13" :stream="streams[13]" extraClass="flex-w-quarter" @submit="startStream" @chatChange="chatChanged" />
                    <Stream :id="14" :stream="streams[14]" extraClass="flex-w-quarter" @submit="startStream" @chatChange="chatChanged" />
                    <Stream :id="15" :stream="streams[15]" extraClass="flex-w-quarter" @submit="startStream" @chatChange="chatChanged" />
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
                        { streamer: '', type: 'twitch', chat: true, streaming: false }
                    ]
                    break;
                case 2:
                case 3:
                    this.streams = [
                        { streamer: '', type: 'twitch', chat: true, streaming: false },
                        { streamer: '', type: 'twitch', chat: true, streaming: false }
                    ]
                    break;
                case 4:
                case 5:
                    this.streams = [
                        { streamer: '', type: 'twitch', chat: true, streaming: false },
                        { streamer: '', type: 'twitch', chat: true, streaming: false },
                        { streamer: '', type: 'twitch', chat: true, streaming: false }
                    ]
                    break;
                case 6: 
                    this.streams = [
                        { streamer: '', type: 'twitch', chat: false, streaming: false },
                        { streamer: '', type: 'twitch', chat: false, streaming: false },
                        { streamer: '', type: 'twitch', chat: false, streaming: false },
                        { streamer: '', type: 'twitch', chat: false, streaming: false }
                    ]
                    break;
                case 7: 
                    this.streams = [
                        { streamer: '', type: 'twitch', chat: false, streaming: false },
                        { streamer: '', type: 'twitch', chat: false, streaming: false },
                        { streamer: '', type: 'twitch', chat: false, streaming: false },
                        { streamer: '', type: 'twitch', chat: false, streaming: false },
                        { streamer: '', type: 'twitch', chat: false, streaming: false },
                        { streamer: '', type: 'twitch', chat: false, streaming: false },
                        { streamer: '', type: 'twitch', chat: false, streaming: false },
                        { streamer: '', type: 'twitch', chat: false, streaming: false },
                        { streamer: '', type: 'twitch', chat: false, streaming: false }
                    ]
                    break;
                case 8: 
                    this.streams = [
                        { streamer: '', type: 'twitch', chat: false, streaming: false },
                        { streamer: '', type: 'twitch', chat: false, streaming: false },
                        { streamer: '', type: 'twitch', chat: false, streaming: false },
                        { streamer: '', type: 'twitch', chat: false, streaming: false },
                        { streamer: '', type: 'twitch', chat: false, streaming: false },
                        { streamer: '', type: 'twitch', chat: false, streaming: false },
                        { streamer: '', type: 'twitch', chat: false, streaming: false },
                        { streamer: '', type: 'twitch', chat: false, streaming: false },
                        { streamer: '', type: 'twitch', chat: false, streaming: false },
                        { streamer: '', type: 'twitch', chat: false, streaming: false },
                        { streamer: '', type: 'twitch', chat: false, streaming: false },
                        { streamer: '', type: 'twitch', chat: false, streaming: false },
                        { streamer: '', type: 'twitch', chat: false, streaming: false },
                        { streamer: '', type: 'twitch', chat: false, streaming: false },
                        { streamer: '', type: 'twitch', chat: false, streaming: false },
                        { streamer: '', type: 'twitch', chat: false, streaming: false }
                    ]
                    break;
            }
            this.layout = layout
        },
        chatChanged(id) {
            this.streams[id].chat = !this.streams[id].chat
        },
        startStream(id) {
            this.streams[id].streaming = true;
            new Twitch.Embed(`twitch-embed-${id}`, {
                width: "100%",
                height: "100%",
                channel: this.streams[id].streamer,
                layout: this.streams[id].chat ? 'video-with-chat' : 'video'
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
    &.blue {
        color: #526488;
    }
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
        &:focus {
            outline: none;
        }
    }
    .switch {
        position: relative;
        display: inline-block;
        width: 60px;
        height: 34px;
    }

    .switch input { 
        opacity: 0;
        width: 0;
        height: 0;
    }

    .slider {
        position: absolute;
        cursor: pointer;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        background-color: #ccc;
        -webkit-transition: .4s;
        transition: .4s;
    }

    .slider:before {
        position: absolute;
        content: "";
        height: 26px;
        width: 26px;
        left: 4px;
        bottom: 4px;
        background-color: white;
        -webkit-transition: .4s;
        transition: .4s;
    }

    input:checked + .slider {
        background-color: #41b883;
    }

    input:focus + .slider {
        box-shadow: 0 0 1px #41b883;
    }

    input:checked + .slider:before {
        -webkit-transform: translateX(26px);
        -ms-transform: translateX(26px);
        transform: translateX(26px);
    }

    /* Rounded sliders */
    .slider.round {
        border-radius: 34px;
    }

    .slider.round:before {
        border-radius: 50%;
    }
}
</style>
