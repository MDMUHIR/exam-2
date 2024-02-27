<script setup>
const props = defineProps(["currentlyEditing", ""]);
const emit = defineEmits(["update"]);
</script>

<template>
  <div
    class="edit-popup p-3 bg-secondary-subtle position-absolute top-0 w-100 vh-100 d-flex flex-column justify-content-center"
  >
    <form>
      <div class="mb-3">
        <label for="name-inp" class="form-label">Task name:</label>
        <input
          v-model="currentlyEditing.name"
          type="text"
          class="form-control"
          id="name-inp"
          aria-describedby="emailHelp"
        />
      </div>
      <div class="mb-3">
        <label for="time-inp" class="form-label">Time:</label>
        <input
          v-model="currentlyEditing.time"
          type="number"
          class="form-control"
          id="time-inp"
        />
      </div>

      <button
        @click="$emit('update')"
        type="submit"
        class="btn btn-primary w-100"
      >
        Submit
      </button>
    </form>
  </div>
</template>

<style scoped></style>
