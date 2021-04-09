<template>
  <p>
    <button
        className="btn primary"
        v-if="comments.length === 0"
        @click="$emit('load')"
    >
      Загрузить комментарии
    </button>
  </p>
  <div className="card" v-if="comments.length">
    <div style="display: flex; justify-content: space-between; ">
      <h2>Комментарии</h2>
      <span @click="$emit('close')">
        <img
            style="width: 25px; height: 25px; cursor: pointer;"
            src="https://upload.wikimedia.org/wikipedia/commons/thumb/a/a0/OOjs_UI_icon_close.svg/1200px-OOjs_UI_icon_close.svg.png"
            alt="">
      </span>
    </div>
    <ul className="list">
      <li
          v-for="comment in comentsToShow"
          :key="comment.id"
          className="list-item"
      >
        <div>
          <p><strong>{{ comments[comment].email }}</strong></p>
          <small>{{ comments[comment].body }}</small>
        </div>
      </li>
    </ul>
    <button
        class="btn"
        @click="comentsToShow += 5"
        style="margin: 10px 0"
    >Load more</button>
  </div>
</template>

<script>
export default {
  name: "ResumeComments",
  props: ['comments'],
  emits: ['load', 'close'],
  data() {
    return {
      comentsToShow: 5
    }
  },
}
</script>

<style scoped>

</style>