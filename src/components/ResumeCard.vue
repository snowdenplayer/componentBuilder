<template>
  <div className="card card-w70">
    <template v-if="blocks.length">
      <component
          v-for="item in blocks"
          :key="item.id"
          :is="item.type"
          :data="item.value"
      />
    </template>
    <h3 v-else>Добавьте первый блок, чтобы увидеть результат</h3>
  </div>
</template>

<script>
import Header from "@/components/UI/Header";
import Text from "@/components/UI/Text";
import SubTitle from "@/components/UI/SubTitle";
import Avatar from "@/components/UI/Avatar";
export default {
  name: "ResumeCard",
  props: ['blocks'],
  components:{
    title: Header,
    text: Text,
    subtitle: SubTitle,
    avatar: Avatar
  },
  computed:{
    componentName(){
      return this.blocks.type
    }
  }
}
</script>

<style scoped>

</style>