<template>
  <li>
    <h2>{{ name }} {{ isFavourite ? "(Favourite)" : " " }}</h2>
    <button @click="toggleFavourite">
      Toggle Favourite
    </button>
    <button @click="toggleDetails">
      {{ !detailsAreVisible ? "Show Details" : "Hide Details" }}
    </button>
    <ul v-if="detailsAreVisible">
      <li><strong>Phone:</strong>{{ phoneNumber }}</li>
      <li><strong>Email:</strong>{{ emailAddress }}</li>
    </ul>
    <button @click="$emit('delete', id)">Delete</button>
  </li>
</template>

<script>
export default {
  props: {
    id: {
      type: String,
      required: true,
    },
    name: {
      type: String,
      required: true,
    },
    phoneNumber: {
      type: String,
      required: true,
    },
    emailAddress: {
      type: String,
      required: true,
    },
    isFavourite: {
      type: Boolean,
      required: false,
      default: false,
    },
  },
  emits: ["toggle-favourite", "delete"],
  data() {
    return {
      detailsAreVisible: false,
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    toggleFavourite() {
      // this.friendIsFavourite = !this.friendIsFavourite;
      this.$emit("toggle-favourite", this.id);
    },
  },
};
</script>

<style></style>
