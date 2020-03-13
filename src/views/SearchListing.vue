<template>
  <div>
    <div class="row">
      <div class="col text-center">
        <div>
          <!-- Using components -->
          <b-input-group prepend="Listing" class="mt-3">
            <b-form-input v-model="keyword"></b-form-input>
            <b-input-group-append>
              <b-button @click="search" variant="outline-success">Search</b-button>
            </b-input-group-append>
          </b-input-group>
        </div>
      </div>
    </div>
    <div class="text-center mt-5" v-show="loading">
        <b-spinner variant="success" label="Spinning"></b-spinner>
    </div>
    <div class="row mt-5">
      <div class="col-lg-4 col-sm-12 text-center" v-for="list in listing" :key="list._id">
        <b-card
          :title="list.name"
          :img-src="list.images.picture_url"
          :img-alt="list.name"
          img-top
          tag="article"
          style="max-width: 20rem;"
          class="mb-2"
        >
          <b-card-text>{{list.summary.substring(0,50)+"..."}}</b-card-text>

          <b-button href="#" variant="primary">View</b-button>
        </b-card>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      keyword: "",
      listing: [],
      loading: false
    };
  },
  methods: {
    search() {
      this.loading = true;
      console.log(this.keyword);
      let url =
        "http://palmairbnbapi.azurewebsites.net/api/airbnb/listings/city/";
      url = url + this.keyword;
      axios.get(url).then(response => {
        console.log(response.data);
        this.listing = response.data;
        this.loading = false;
      });
    }
  }
};
</script>

<style>
</style>