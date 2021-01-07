<template>
        <div class="flex w-screen h-screen">
            <div id="twitch-embed" class="w-full"></div>
            <div id="chat-embed">
                <iframe frameborder="0"
                        scrolling="yes"
                        src="https://www.twitch.tv/embed/xqcow/chat?parent=straemly.netlify.app"
                        height="100%"
                        width="340">
                </iframe>
            </div>
        </div>
</template>

<script>
export default {
    mounted() {
        new Twitch.Embed("twitch-embed", {
            width: "100%",
            height: "100%",
            channel: 'xqcow',
            layout: 'video'
            // only needed if your site is also embedded on embed.example.com and othersite.example.com 
            // parent: ["embed.example.com", "othersite.example.com"]
        });
    }
}
</script>

<style>
/* Sample `apply` at-rules with Tailwind CSS
.container {
@apply min-h-screen flex justify-center items-center text-center mx-auto;
}
*/
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
