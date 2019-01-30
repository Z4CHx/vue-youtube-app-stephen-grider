<template>
  <div id="App" class="container">
    <SearchBar @termChange="onTermChange"></SearchBar>
    <div class="row">
      <div class="col-md-7">
        <VideoDetail
          v-if="selectedVideo"
          :video="selectedVideo.snippet.title"
          :videoId="selectedVideo.id.videoId"
        />
      </div>
      <div class="col-md-4 col-md-offset-1">
        <VideoList @videoSelect="onVideoSelect" :videos="videos"></VideoList>
      </div>
    </div>
  </div>
</template>

<script>
import Axios from "axios";
import SearchBar from "./components/SearchBar";
import VideoList from "./components/VideoList";
import VideoDetail from "./components/VideoDetail";
// import API_KEY from "../KEY_YOUTUBE";

export default {
  name: "App",
  data() {
    return {
      videos: [],
      selectedVideo: null
    };
  },
  components: {
    SearchBar,
    VideoList,
    VideoDetail
  },
  methods: {
    onVideoSelect(video) {
      this.selectedVideo = video;
    },
    onTermChange(searchTerm) {
      Axios.get("https://www.googleapis.com/youtube/v3/search", {
        params: {
          key: "AIzaSyBFjzdSU-qJfO7COWM3FCITOwJvgF8Y88I",
          type: "video",
          part: "snippet",
          q: searchTerm
        }
      }).then(response => {
        this.videos = response.data.items;
        console.log(this.videos[0]);
      });
    }
  }
};
</script>

<style></style>
