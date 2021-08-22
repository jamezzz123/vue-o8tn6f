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
          <h6 class="card__content__title">
            Lorem, ipsum dolor sit amet consectetur adipisicing elit.
          </h6>
          <div class="card__content__description">
            <p>Location</p>
            <p>Ticket Available <span>4</span></p>
          </div>
        </div>
      </div>
      <a class="card__button text-uppercase">Sold out</a>
      <img :src="img" class="card__button__sm" alt="" srcset="" />
    </div>
  </div>
</template>

<script>
import text from "../assets/event-icon.svg";
export default {
  data() {
    return {
      img: text,
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
    // @media (max-width: 780px) {
    //   flex-direction: row;
    // }

    &__title {
      font-size: 22px;
      text-align: center;
      margin-top: 0px;
      margin-bottom: 15px;
      line-height: 1;
      font-weight: bold;

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
    border: 2px solid #fc732f;
    border-radius: 4px;
    width: 100%;
    background: #fff;
    font-size: 20px;
    font-weight: 600;
    padding: 5px;
    text-align: center;

    @media (max-width: 780px) {
      display: none;
    }
    &__sm {
      display: none;
      @media (max-width: 780px) {
        display: block;
      }
    }
  }
}
</style>
