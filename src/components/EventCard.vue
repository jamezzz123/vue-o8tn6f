<template>
  <div class="card">
    <img
      src="https://source.unsplash.com/collection/9537244/200x200"
      alt=""
      class="card__image"
    />
    <div class="card__body">
      <div class="card__content">
        <div class="card__info">
          <h6 class="card__content__title">{{ eventDetails.title }}.</h6>
          <div class="card__content__description">
            <p>{{ eventDetails.date }}</p>
            <p>
              Ticket Available <span>{{ eventDetails.ticket_available }}</span>
            </p>
          </div>
        </div>
      </div>
      <div class="card__button">
        <router-link
          class="card__button__link text-uppercase"
          :class="{ 'card__button__link--disabled': eventDetails.sold_out }"
          style="width: 100%"
          :to="{ name: 'book', params: { id: eventDetails.id } }"
          >{{ eventDetails.sold_out ? "SOLD OUT" : "BOOK EVENT" }}</router-link
        >
        <a
          href=""
          class="card__button__sm"
          :class="{ 'card__button__link--disabled': eventDetails.sold_out }"
          ><eventIcon class="card__button__link__sm"></eventIcon
        ></a>
      </div>
      <!-- <img :src="img" class="card__button__sm" alt="" srcset="" /> -->
    </div>
  </div>
</template>

<script>
import eventIcon from "./EventIcon";
export default {
  components: {
    eventIcon,
  },
  props: {
    eventDetails: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      // img: text,
    };
  },
  setup() {
    return {};
  },
};
</script>

<style lang="scss" scoped>
.card {
  width: 100%;
  border: 1px solid #e5e5e5;
  border-radius: 4px;
  display: flex;
  flex-direction: column;
  align-items: center;
  box-shadow: rgba(0, 0, 0, 0.1) 0px 10px 15px -3px,
    rgba(0, 0, 0, 0.05) 0px 4px 6px -2px;
  //   margin: 20px;

  @media (max-width: 780px) {
    display: flex;
    flex-direction: row;
    // align-content: center;
  }

  &__body {
    padding: 20px;
    display: flex;
    flex-direction: column;
    display: flex;
    width: 100%;
    justify-content: space-between;

    @media (max-width: 780px) {
      flex-direction: row;
      // align-content: center;
    }
  }
  &__info {
    display: flex;
    flex-direction: column;
  }
  &__image {
    width: 100%;
    height: 200px;
    border-radius: 4px;
    @media (max-width: 400px) {
      display: none;
      visibility: hidden;
    }
    @media (max-width: 780px) {
      margin: 20px;
      width: 120px;
      height: 120px;
    }
  }
  &__content {
    // display: flex;
    // flex-direction: column;
    padding: 10px;
    @media (max-width: 780px) {
      width: 90%;
    }
    &__title {
      font-size: 22px;
      text-align: center;
      margin-top: 0px;
      margin-bottom: 15px;
      line-height: 1;
      font-weight: bold;
      text-transform: capitalize;
      @media (max-width: 780px) {
        text-align: left;
        font-size: 20px;
        font-size: 16px;
      }
    }

    &__description {
      display: flex;
      justify-content: space-between;
      //   margin: 4px 0px;

      @media (max-width: 780px) {
        flex-direction: column;
      }
    }
  }
  &__button {
    align-self: center;
    width: 100%;
    @media (max-width: 780px) {
      width: auto;
    }
    &__link {
      border: 2px solid #fc732f;
      border-radius: 4px;
      width: 100%;
      background: #fff;
      text-decoration: none;
      color: #fc732f;
      font-size: 20px;
      font-weight: 600;
      padding: 5px;
      text-align: center;
      align-self: center;
      display: block;

      @media (max-width: 780px) {
        display: none;
      }
      &__sm {
        align-self: center;
        display: none;
        @media (max-width: 780px) {
          display: block;
        }
      }
      &--disabled {
        border-color: #e5e5e5;
        color: #e5e5e5;
      }
    }
  }
}
</style>
