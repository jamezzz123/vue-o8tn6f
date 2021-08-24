<template>
  <div>
    <div class="card">
      <div class="card__details">
        <div class="card__title">
          <h2>{{ eventDetail.title }}</h2>
          <p>Ticket Available {{ eventDetail.ticket_available }}</p>
          <p>{{ eventDetail.date }}</p>
        </div>
        <br />
        <div class="card__form">
          <ul
            v-for="(error, index) in errors"
            :key="index"
            style="color: brown"
          >
            <li>{{ error }}</li>
          </ul>
          <form class="form" action="" @submit.prevent="confirmSumbit()">
            <div class="form__block">
              <label class="form__block__label" for="">Name</label>
              <input
                type="text"
                class="form__block__input"
                v-model="attandee.name"
                placeholder="Name"
              />
            </div>
            <div class="form__block">
              <label class="form__block__label" for="">Email</label>
              <input
                type="text"
                class="form__block__input"
                v-model="attandee.email"
                placeholder="Email"
              />
            </div>

            <div class="form__block">
              <label class="form__block__label" for="">Mobile</label>
              <input
                type="text"
                class="form__block__input"
                v-model="attandee.mobile"
                placeholder="Name"
              />
            </div>
            <div class="form__block">
              <label class="form__block__label" for="">Attendee</label>
              <div
                style="display: flex"
                v-for="(item, index) in attandee.attandee"
                :key="index"
              >
                <div class="" style="width: 20%">
                  <p>{{ index + 1 }}</p>
                </div>

                <input
                  type="text"
                  class="form__block__input"
                  name="name"
                  style="width: 80%"
                  v-model="attandee.attandee[index].firstName"
                  placeholder="Name"
                />
              </div>
              <div style="display: flex; flex-direction: row-reverse">
                <button
                  style="width: 30%"
                  class="button button--noborder"
                  @click.prevent="addAttandee()"
                >
                  + Add attendee
                </button>
              </div>
            </div>
            <div
              class="form__block"
              style="display: flex; justify-content: space-around"
            >
              <input type="submit" value="Book" class="button" />
              <input
                type="button"
                value="Close"
                class="button button--inverse"
              />
            </div>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import data from "../assets/data.json";
export default {
  data() {
    return {
      eventDetail: {},
      errors: [],
      attandee: {
        name: "",
        email: "",
        mobile: "",
        attandee: [
          {
            firstName: "",
          },
        ],
      },
    };
  },
  methods: {
    confirmSumbit() {
      // console.log("HEHEH")
      let errors = [];
      var pattern = /^\w+@[a-zA-Z_]+?\.[a-zA-Z]{2,3}$/;
      if (this.attandee.name === "") {
        console.log("HEH");
        errors.push("Please enter your name");
      }
      if (!pattern.test(this.attandee.email)) {
        // regex express
        errors.push("Invalid email");
      }
      if (!this.attandee.mobile) {
        // regex express
        errors.push("please enter mobile number");
      }
      this.attandee.attandee.forEach((item, index) => {
        if (!item.firstName) {
          errors.push(`Please enter the name of Attendee ${index + 1}`);
        }
      });
      console.log(errors);
      this.errors = errors;
      if (errors.length === 0) {
        this.submitForm();
      }
    },
    submitForm() {
      console.log("HEHE");
    },
    addAttandee() {
      this.attandee.attandee.push({ firstName: "" });
    },
  },
  mounted() {
    this.eventDetail = data.find((item) => item.id == this.$route.params.id);
    console.log(this.eventDetail);
  },
};
</script>

<style lang="scss" scoped>
.card {
  width: 50%;
  margin: 20px auto;
  &__title {
    text-align: center;
  }
}
.form {
  display: flex;
  flex-direction: column;
  // &__label {
  //   width: 100%;
  //   margin-bottom: 5px;
  //   display: block;
  // }
  &__block {
    margin: 10px;
    &__label {
      width: 100%;
      display: block;
      margin-bottom: 5px;
    }
    &__input {
      // padding: 10px;
      padding: 8px 5px;
      display: block;
      width: 100%;
    }
  }
}

.button {
  background-color: #fc732f;
  color: white;
  padding: 0.375rem 0.75rem;
  font-size: 1rem;
  line-height: 1.5;
  border-radius: 0.25rem;
  border: none;
  margin: 0px 10px;
  display: block;
  width: 100%;
  &--inverse {
    background-color: white !important;
    color: #fc732f !important;
    border: 2px solid #fc732f;
  }
  &--noborder {
    background-color: white !important;
    color: #fc732f !important;
  }
}
</style>
