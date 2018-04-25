<template>
  <div>
    <b-button @click="showModal">
      Add Kanban
    </b-button>
     <b-modal ref="myModalRef" hide-footer title="Add Kanban">
        <div class='ui form'>
          <div class='field'>
            <label>Title</label>
            <input v-model="kanbanTitle" type='text'>
          </div>
          <div class='textform'>
            <label>Content</label>
            <input v-model="kanbanContent" type='text'>
          </div>
          <div class='field'>
            <label>Point</label>
            <input v-model="kanbanPoint" type='text'>
          </div>
        </div>
        <b-btn class="mt-3" variant="outline-danger" block @click="sendForm()">Create Kanban</b-btn>
      <b-btn class="mt-3" variant="outline-danger" block @click="hideModal">Cancel</b-btn>
    </b-modal>
  </div>
</template>

<script>
import { mapActions } from 'vuex'
export default {
  data () {
    return {
      kanbanTitle: '',
      kanbanContent: '',
      kanbanPoint: '',
      isCreating: false
    }
  },
  methods: {
    ...mapActions([
      'addTask'
    ]),
    openForm () {
      this.isCreating = true
    },
    closeForm () {
      this.isCreating = false
    },
    sendForm () {
      if (this.kanbanTitle.length > 0 && this.kanbanContent.length > 0) {
        let obj = {
          title: this.kanbanTitle,
          content: this.kanbanContent,
          point: this.kanbanPoint,
          status: 'BackLog'
        }
        this.addTask(obj)
        this.hideModal()
      }
    },
    showModal () {
      this.$refs.myModalRef.show()
    },
    hideModal () {
      this.$refs.myModalRef.hide()
    }
  }
}
</script>
