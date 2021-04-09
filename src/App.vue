<template>
  <div className="container column">
    <ResumeForm @addBlock="addBlock"></ResumeForm>
    <ResumeCard :blocks="block"></ResumeCard>
  </div>
  <div className="container">
    <AppLoader v-if="loading"></AppLoader>
    <ResumeComments
        v-else
        @load="loadComments"
        :comments="comments"
        @close="closeComments"
    ></ResumeComments>
  </div>
</template>

<script>
import ResumeForm from "@/components/ResumeForm";
import ResumeCard from "@/components/ResumeCard";
import ResumeComments from "@/components/ResumeComments";
import AppLoader from "@/components/AppLoader";
import axios from 'axios'
export default {
  data(){
    return{
      block: [],
      loading: false,
      comments: []
    }
  },
  components:{
    ResumeForm,
    ResumeCard,
    ResumeComments,
    AppLoader
  },
  methods:{
    addBlock(block){
      this.block.push(block)
    },
    async loadComments(){
      this.loading = true
      await axios.get('https://jsonplaceholder.typicode.com/comments?_limit=42').then(res => {
        this.comments = res.data
      })
      this.loading = false
    },
    closeComments(){
      this.comments = []
    }
  }

}
</script>

<style>
.avatar {
  display: flex;
  justify-content: center;
}

.avatar img {
  width: 150px;
  height: auto;
  border-radius: 50%;
}
</style>
