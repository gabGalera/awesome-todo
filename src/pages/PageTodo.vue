<template>
  <q-page class="q-pa-md">
    <q-list
      separator
      bordered>
      <task
        v-for="(task, key) in tasks"
        :key="key"
        :task="task"
        :id="key"
      >
      </task>
    </q-list>

    <div class="absolute-bottom text-center q-mb-lg">
      <q-btn
      @click="showAddTask = true"
      round
      color="primary"
      size="24px"
      icon="add"
      />
    </div>

    <q-dialog v-model="showAddTask">
      <add-task></add-task>
    </q-dialog>
  </q-page>
</template>

<script>
import { mapGetters } from 'vuex'

export default {
  data () {
    return {
      showAddTask: true
    }
  },
  computed: {
    ...mapGetters('tasks', ['tasks'])
  },
  components: {
    task: require('components/Tasks/Task.vue').default,
    'add-task': require('components/Tasks/Modals/AddTask.vue').default

  }
}
</script>

<style>

</style>
