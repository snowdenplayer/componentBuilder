<template>
  <form class="card card-w30" @submit.prevent="submit">
    <div class="form-control">
      <label for="type">Тип блока</label>
      <select id="type" v-model="type">
        <option value="title">Заголовок</option>
        <option value="subtitle">Подзаголовок</option>
        <option value="avatar">Аватар</option>
        <option value="text">Текст</option>
      </select>
    </div>

    <div class="form-control">
      <label for="value">Значение</label>
      <textarea v-model="value" id="value" rows="3"></textarea>
    </div>

    <button class="btn primary" :disabled="isDisabled">Добавить</button>
  </form>
</template>

<script>
export default {
  name: "ResumeForm",
  emits: ['addBlock'],
  data(){
    return{
      type: 'title',
      value: '',
    }
  },
  computed:{
    isDisabled(){
      return this.value.length < 4
    }
  },
  methods:{
    submit(){
      this.$emit('addBlock',{
        type: this.type,
        value: this.value,
        id: parseInt(Math.random()*100)
      })
      this.value = ''
      this.type = 'title'
    }
  }
}
</script>

<style scoped>

</style>