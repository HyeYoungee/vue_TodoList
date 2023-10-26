<script>
  export default {
    props: {
      todo: {
        type: Object,
        required: true
      }
    },
    methods: {
      toggleCheckbox(e){
        this.$emit('toggle-checkbox',{
          id: this.todo.id,
          checked: e.target.checked
        })
      },
      clickDelete(){
        this.$emit('click-delete', this.todo.id);
      }
    }
  }
</script>

<template>
  <div class="form-check" :data-id="todo.id">
    <input 
      class="form-check-input" 
      type="checkbox" 
      value="" 
      :id="'input'+todo.id"
      @change="toggleCheckbox"
    >
    <label 
      class="form-check-label" 
      :for="`input${todo.id}`"
      :style="todo.checked ? 'text-decoration:line-through' : ''"
    >
      {{ todo.text }}
    </label>
    <button 
      type="button" 
      class="btn btn-danger ms-3"
      style="--bs-btn-padding-y: .2rem; --bs-btn-padding-x: .4rem; --bs-btn-font-size: .7rem; border-radius: 3px"
      @click="clickDelete"
    >
      Delete
    </button>
  </div>
</template>