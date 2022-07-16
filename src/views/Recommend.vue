<template>
  <div class="recommend">
    <div class="recommend-wrapper">
      <ScrollView>
        <div>
          <Banner :banners="banners"></Banner>
          <Personalized :personalized="personalized" :title="'推荐歌单'" @select="fatherSelectItem" :type="'personalized'"></Personalized>
          <Personalized :personalized="albums" :title="'最新专辑'" @select="fatherSelectItem" :type="'albums'"></Personalized>
          <SongList :songs="songs" :title="'最新音乐'"></SongList>
        </div>
      </ScrollView>
    </div>
    <transition>
      <router-view></router-view>
    </transition>
  </div>
</template>

<script>
import { getBanner, getPersonalized, getNewAlbum, getNewSong } from '../api/index'
import Banner from '../components/Recommend/Banner'
import Personalized from '../components/Recommend/Personalized'
import SongList from '../components/Recommend/SongList'
import ScrollView from '../components/ScrollView'

export default {
  name: 'Recommend',
  components: {
    Banner,
    Personalized,
    SongList,
    ScrollView
  },
  methods: {
    fatherSelectItem (id, type) {
      this.$router.push({
        path: `/recommend/detail/${id}/${type}`
      })
    }
  },
  data () {
    return {
      banners: [],
      personalized: [],
      albums: [],
      songs: []
    }
  },
  created () {
    getBanner()
      .then((data) => {
        // console.log(data)
        this.banners = data.banners
      })
      .catch(function (err) {
        console.log(err)
      })
    getPersonalized()
      .then((data) => {
        this.personalized = data.result
      })
      .catch(function (err) {
        console.log(err)
      })
    getNewAlbum()
      .then((data) => {
        // console.log(data.albums.splice(0, 6))
        this.albums = data.albums.splice(0, 6)
      })
      .catch(function (err) {
        console.log(err)
      })
    getNewSong()
      .then((data) => {
        this.songs = data.result
      })
      .catch(function (err) {
        console.log(err)
      })
  }
}
</script>

<style scoped lang="scss">
.recommend {
  position: fixed;
  top: 184px;
  left: 0;
  right: 0;
  bottom: 0;
  //overflow: hidden;
  .recommend-wrapper {
    width: 100%;
    height: 100%;
    overflow: hidden;
  }
}

</style>
