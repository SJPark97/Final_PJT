<template>
  <div class="notice">
    <font-awesome-icon icon="fa-solid fa-xmark" class="x-mark" @click="popExit" />
    <b-card no-body class="storage">
      <b-tabs 
        card 
        content-class="mt-3 bg-transparent" 
        align="center"
        active-nav-item-class="bg-transparent border-bottom-0"
        active-tab-class="font-weight-bold success"
      >
        <b-tab avtive>
          <template v-slot:title>
            <span>
            <font-awesome-icon icon="fa-solid fa-bell"/>
            </span>
          </template>
          <b-card-text>
            <NoticeNew @close-notice="closeNotice"/>
          </b-card-text>
        </b-tab>
        <b-tab >
          <template v-slot:title>
            <span>
            <font-awesome-icon icon="fa-regular fa-bell"/>
            </span>
          </template>
          <b-card-text>
            <NoticeOld @close-notice="closeNotice"/>
          </b-card-text>
        </b-tab>
      </b-tabs>
    </b-card>
  </div>
</template>

<script>
import NoticeNew from '@/components/NoticeNew'
import NoticeOld from '@/components/NoticeOld'

export default {
  name: 'Notice',
  components: {
    NoticeNew,
    NoticeOld,
  },
  computed: {
    token() {
      return this.$store.state.token
    }
  },
  methods: {
    popExit() {
      this.$emit('pop-exit')
    },
    closeNotice() {
      this.$emit('close-notice')
    }
  },
}
</script>

<style scoped>
.notice {
  display: inline-block;
  width: 350px;
  height: 500px;
  position: absolute;
  /* object-fit: contain; */
  top: 100px;
  left: 180px;
  padding-top: 40px;
  padding-left: 60px;
  padding-right: 60px;
  border: 1px solid rgba(128, 128, 128, 0.123);
  box-shadow: 1px 1px 1px 1px rgb(136, 136, 136);
  z-index: 99;
  background-color: rgb(218, 210, 210);
}

.x-mark {
  position: absolute;
  top: 10px;
  left: 317px;
  color: white;
  font-size: 25px;
}

.storage {
  position: absolute;
  /* overflow: auto; */
  top: -20px;
  left: -20px;
  bottom: 100px;
  display: flex;
  width: 280px;
  height: 435px;
  margin-top: 15%;
  margin-left: 15%;
  /* margin-right: 15%; */
  padding-bottom: 10vh;
  background-color: rgb(221, 221, 221);
  border: none;
  box-shadow: 1px 1px 1px 1px rgb(196, 196, 196);
  /* height: 80%; */
}

/* .storage::-webkit-scrollbar {
  display: none;
} */

svg {
  text-decoration: none;
  color: black;
  text-shadow: 2px 2px gray;
}
</style>