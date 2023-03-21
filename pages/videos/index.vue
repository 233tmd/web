<template>
  <div class="pa-10">
    <h3>视频列表</h3>
    <!-- <div>{{ videos }}</div> -->
    <v-row>
      <v-col v-for="item in videos" :key="item._id">
        <v-card :to="`/videos/${item._id}`" class="mx-auto" max-width="344">
          <v-img :src="item.cover" height="200px"></v-img>

          <v-card-title class="linehidden"> {{ item.name }} </v-card-title>

          <v-card-subtitle> {{ item.createdAt }} </v-card-subtitle>

          <v-card-actions>
            <v-btn text>Share</v-btn>

            <v-btn color="purple" text> Explore </v-btn>

            <v-spacer></v-spacer>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  async asyncData({ $axios }) {
    // const res = await $axios.get('videos') // 获取对象
    // const videos = res.data // 把data传给videos
    const data = await $axios.$get('videos')
    return {
      videos: data.data,
    }
  },
}
</script>

<style>
.linehidden {
  display: block;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
</style>
