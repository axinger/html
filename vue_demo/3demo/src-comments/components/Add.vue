<template>
  <div class="col-md-4">

    <from class="form-horizontal">

      <div class="form-group">
        <label>用户名</label>
        <input type="text" class="form-control" placeholder="用户名" v-model="name">
      </div>


      <div class="form-group">
        <label>评论内容</label>
        <textarea class="form-control" rows="6" placeholder="评论内容" v-model="content"></textarea>
      </div>

      <div class="form-group">
        <div class="col-sm-offset-2 col-sm-10">
          <button type="button" class="btn btn-default pull-right" @click="add">提交</button>
        </div>
      </div>

    </from>

  </div>
</template>

<script>
export default {
  name: "Add",
  props: {
    //定义属性
    addComment: {
      type: Function,
      required: true,
    },

  },
  data() {
    return {
      name: '',
      content: '',
    }
  },
  methods: {
    add() {
      // 1.检查有效性
      const name = this.name.trim()
      const content = this.content.trim()
      if (!name || !content) {
        alert('无效内容')
        return
      }
      // 2.根据输入的数据,封装对象
      const comment = {
        name,
        content,
      }

      //3,添加到comments中
      this.addComment(comment)
      //  4.清除输入
      this.name = ''
      this.content = ''

    },

  },
}
</script>

<style scoped>

</style>
