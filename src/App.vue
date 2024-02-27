<script setup>
import { reactive, ref } from "vue";
import EditPopup from "./components/EditPopup.vue";

const tasks = ref([
  {
    name: "Task 1",
    time: 30,
  },
  {
    name: "Task 2",
    time: 40,
  },
  {
    name: "Task 3",
    time: 60,
  },
  {
    name: "Task 4",
    time: 45,
  },
  {
    name: "Task 5",
    time: 50,
  },
]);

const currentlyEditingIndex = ref(null);
const currentlyEditing = ref({
  name: "",
  time: null,
});
const popup = ref(false);

const editTaskPop = (index) => {
  popup.value = !popup.value;
  currentlyEditingIndex.value = index;
};

const updateTask = () => {
  tasks.value.splice(currentlyEditingIndex.value, 1, currentlyEditing.value);
  currentlyEditing.value = {
    name: "",
    time: null,
  };
  popup.value = !popup.value;
};
</script>

<template>
  <div class="conatiner position-relative">
    <div class="tasks text-center">
      <h1 class="heading p-3 bg-danger">Tasks</h1>
      <ul
        v-for="(task, index) in tasks"
        :key="index"
        class="task-list list-group"
      >
        <li
          class="task list-group-item d-flex justify-content-around align-items-center"
        >
          <p class="">{{ index + 1 }}.</p>
          <h3>{{ task.name }}</h3>
          <p>{{ task.time }} min</p>
          <button @click="editTaskPop(index)" class="btn btn-success">
            Edit
          </button>
        </li>
      </ul>
    </div>
    <EditPopup
      v-if="popup"
      :currentlyEditing="currentlyEditing"
      @update="updateTask()"
    />
  </div>
</template>

<style scoped></style>
