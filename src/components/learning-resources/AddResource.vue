<template>
  <base-card>
    <form>
      <div class="form-control">
        <label>Title</label>
        <input id="title" type="text" name="title" />
      </div>
      <div class="form-control">
        <label for="descpriction" >Description</label>
        <textarea id="descpriction" name="descpriction" rows="3"></textarea>
      </div>
      <div class="form-control">
        <label for="link" >Link</label>
        <input id="link" type="url" name="link" />
      </div>
      <base-button type="submit" >Add Source</base-button>
    </form>
  </base-card>
</template>

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