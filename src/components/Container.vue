<template>
  <div>
    <div class='c-search'>
      <b-form v-on:submit.prevent='search' inline>
        <b-input-group class='mb-2 mr-sm-2 mb-sm-0'>
          <b-input placeholder='Search' v-model='valueSearch'></b-input>
        </b-input-group>
        <b-button variant='primary' v-on:click.prevent='search'>Search</b-button>
      </b-form>
    </div>
    <div class='container-wrap'>
      <div class='content'>
      <b-card-group deck class='col-12'>
        <Card v-for='name in paginador(breeds)' v-bind:key='name' :name='name'
          :nameBreed='nameBreed' :onSearch=okSearch>
        </Card>
      </b-card-group>
    </div>
    </div>
    <b-pagination class='c-pagination' align='center' :total-rows='this.breeds.length'
      v-model='currentPage' :per-page='itemsMaxPage'>
    </b-pagination>
  </div>
</template>

<script>
import axios from 'axios';
import Card from './Card.vue';

export default {
  name: 'Container',
  components: {
    Card,
  },
  data() {
    return {
      breeds: [],
      currentPage: 1,
      itemsMaxPage: 9,
      valueSearch: '',
      okSearch: false,
      nameBreed: '',
    };
  },
  created() {
    axios.get('https://dog.ceo/api/breeds/list/all').then((result) => {
      this.breeds = Object.keys(result.data.message);
    });
  },
  methods: {
    paginador(items) {
      const indexInit = (this.currentPage - 1) * this.itemsMaxPage;
      const indexFinal = indexInit + this.itemsMaxPage > items.length ? items.length
        : indexInit + this.itemsMaxPage;
      return items.slice(indexInit, indexFinal);
    },
    search() {
      const clearValue = this.valueSearch.toLowerCase().replace(' ', '');
      axios.get(`https://dog.ceo/api/breed/${clearValue}/images`).then((result) => {
        this.nameBreed = clearValue;
        this.breeds = result.data.message;
        this.okSearch = true;
      }).catch(() => {
        this.okSearch = false;
        axios.get('https://dog.ceo/api/breeds/list/all').then((result) => {
          this.breeds = Object.keys(result.data.message);
        });
      });
    },
    random() {
      axios.get('https://dog.ceo/api/breeds/list/all').then((result) => {
        this.breeds = Object.keys(result.data.message);
      });
    },
  },
};
</script>

<style scoped>
  aside {
    width: 283px;
    height: 498px;
    background: red;
  }
  .container-wrap {
    display: flex;
    justify-content: center;
  }
  .content {
    display: flex;
  }
  .c-search {
    background: white;
  }
  .c-pagination {
    margin-top: 24px;
  }
</style>
