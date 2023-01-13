<template>
  <base-dialog v-if="inputIsInvalid" title="Warning" @close="confirmError">
    <template #default>
        <p>Lütfen boş alanları doldurunuz.. </p>
    </template>
   <template #actions>
        <base-button @click="confirmError">Okay</base-button>
   </template>
</base-dialog>
  <base-card>
    <form @submit.prevent="submitData">
      <div class="form-control">
        <label>Title</label>
        <input id="title" type="text" name="title" ref="titleInput" />
      </div>
      <div class="form-control">
        <label for="descpriction">Description</label>
        <textarea
          id="descpriction"
          name="descpriction"
          rows="3"
          ref="descInput"
        ></textarea>
      </div>
      <div class="form-control">
        <label for="link">Link</label>
        <input id="link" type="url" name="link" ref="linkInput" />
      </div>
      <base-button type="submit">Add Source</base-button>
    </form>
  </base-card>
</template>

<script>
import BaseButton from '../UI/BaseButton.vue';
import BaseDialog from '../UI/BaseDialog.vue';
export default {
  components: { BaseDialog, BaseButton },
  inject: ["addResource"],
  data(){
    return{
        inputIsInvalid: false,
    }
  },
  methods: {
    submitData() {
      const enteredTitle = this.$refs.titleInput.value;
      const enteredDescriotion = this.$refs.descInput.value;
      const enteredLinkInput = this.$refs.linkInput.value;
      if(enteredTitle.trim() === '' || enteredDescriotion.trim() === '' || enteredLinkInput.trim() === ''){
        this.inputIsInvalid = true;
        return;
      }
      this.addResource(enteredTitle, enteredDescriotion, enteredLinkInput);
    },
    confirmError(){
        this.inputIsInvalid = false;
    }
  },
};
</script>

<style scoped>
label {
  font-weight: bold;
  display: block;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}
</style>