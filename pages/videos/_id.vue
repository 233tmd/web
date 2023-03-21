<template>
  <div class="pa-10">
    <h3 class="video-linehidden">{{ videos.name }}</h3>
    <video width="100%" :src="videos.file" controls></video>
  </div>
</template>
<script>
export default {
  async asyncData({ params, $axios }) {
    const { id } = params
    const videos = await $axios.$get(`videos/${id}`)
    return {
      id,
      videos,
    }
  },
}
</script>
<style>
.video-linehidden {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
</style>
