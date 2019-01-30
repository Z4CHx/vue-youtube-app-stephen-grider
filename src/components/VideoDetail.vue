<template>
  <div v-if="video">
    {{ title }}
    <div class="embed-responsive embed-responsive-16by9">
      <iframe
        id="ytplayer"
        type="text/html"
        width="720"
        height="405"
        :src="this.videoURL"
        frameborder="0"
        allowfullscreen
      >
      </iframe>
    </div>
  </div>
</template>

<script>
export default {
  name: "VideoDetail",
  props: ["title", "videoId", "video"],
  computed: {
    videoURL() {
      const url = "https://www.youtube.com/embed/" + this.videoId;
      console.log(url);
      return url;
    }
  }
};
</script>

<style scoped></style>
