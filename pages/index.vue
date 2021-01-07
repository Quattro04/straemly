<template>
        <div class="flex w-screen h-screen">
            <div id="twitch-embed" class="w-full"></div>
        </div>
</template>

<script>
export default {
    mounted() {
        new Twitch.Embed("twitch-embed", {
            width: "100%",
            height: "100%",
            channel: 'xqcow',
            // only needed if your site is also embedded on embed.example.com and othersite.example.com 
            // parent: ["embed.example.com", "othersite.example.com"]
        });
    }
}
</script>

<style>

</style>
