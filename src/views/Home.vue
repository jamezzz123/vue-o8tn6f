<template>
  <my-header></my-header>
  <SearchBar @input="filter($event.target.value)"></SearchBar>

  <div class="container-fluid">
    <h1 class="text-uppercase">Event ({{ events.length }})</h1>
    <div class="grip container-fluid">
      <EventCard
        v-for="(item, index) in events"
        :key="index"
        :eventDetails="item"
      ></EventCard>
    </div>
  </div>
</template>

<script>
import SearchBar from "@/components/SearchBar.vue";
import MyHeader from "@/components/MyHeader.vue";
import EventCard from "@/components/EventCard.vue";
import data from "@/assets/data.json";

export default {
  name: "App",
  data() {
    return {
      events: data,
    };
  },
  components: {
    MyHeader,
    SearchBar,
    EventCard,
  },
  methods: {
    filter(title) {
      if (title) {
        this.events = this.events.filter((item) => item.title.includes(title));
      } else {
        this.events = data;
      }
    },
  },
};
</script>

<style lang="scss">
* {
  margin: 0px;
  padding: 0px;
  font-family: "Almarai", sans-serif;
  box-sizing: border-box;
}

.text-uppercase {
  text-transform: uppercase;
}

.container-fluid {
  width: 100%;
  padding-right: 0.75rem;
  padding-left: 0.75rem;
  margin-right: auto;
  margin-left: auto;
  max-width: 1320px;
}

.grip {
  display: grid;
  gap: 32px;
  grid-template-columns: repeat(3, 1fr);

  @media (max-width: 780px) {
    grid-template-columns: repeat(1, 1fr);
  }
}
</style>
