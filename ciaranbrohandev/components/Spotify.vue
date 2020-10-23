<template>
  <div>
    <p v-if="$fetchState.pending">Fetching mountains...</p>
    <p v-else-if="$fetchState.error">An error occurred :(</p>
    <div v-else>


      <p v-if="songs.recenttracks.track[0]">
        {{songs.recenttracks.track[0]}}

      </p>
    </div>
  </div>
</template>

<script>
export default {
    data() {
      return {
        songs: []
      }
    },
    async fetch() {
      this.songs = await fetch(
        'http://ws.audioscrobbler.com/2.0/?method=user.getrecenttracks&user=ciaranbrohan&api_key=key&format=json'
      ).then(res => res.json())
    },
    fetchOnServer: false
  }
</script>
