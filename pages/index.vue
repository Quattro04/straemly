<template>
    <div class="container">
        <div>
            <div id="twitch-embed"></div>
            <div id="chat-embed">
                <iframe frameborder="200"
                        scrolling="yes"
                        src="https://www.twitch.tv/embed/xqcow/chat?parent=multistream.com"
                        height="480"
                        width="200">
                </iframe>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    mounted() {
        new Twitch.Embed("twitch-embed", {
            width: 854,
            height: 480,
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
