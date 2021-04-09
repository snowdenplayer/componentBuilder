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
          v-for="comment in comments"
          :key="comment.id"
          className="list-item"
      >
        <div>
          <p><strong>{{ comment.email }}</strong></p>
          <small>{{ comment.body }}</small>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "ResumeComments",
  props: ['comments'],
  emits: ['load', 'close'],
}
</script>

<style scoped>

</style>