<template>
  <div>
    <div class="card">
      <div class="card__details">
        <div class="card__title">
          <h2>Some Random Text</h2>
        </div>
        <br />
        <div class="card__form">
          <form class="form" action="">
            <label for="">Name</label>
            <input
              type="text"
              class="form-input"
              name="name"
              placeholder="Name"
            />
            <label for="">Email</label>
            <input
              type="text"
              class="form-input"
              name="name"
              placeholder="Name"
            />
            <label for="">Mobile</label>
            <input
              type="text"
              class="form-input"
              name="name"
              placeholder="Name"
            />
            <label for="">Address</label>
            <input
              type="text"
              class="form-input"
              name="name"
              placeholder="Name"
            />
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.card {
  &__details {
  }
}
.form {
  display: flex;
  flex-direction: row;
  &__input {
    padding: 10px;
  }
}

.button {
  background-color: #fc732f;
  color: white;
  padding: 10px;

  &__inverse {
    border-color: white;
    color: #fc732f;
  }
}
</style>
