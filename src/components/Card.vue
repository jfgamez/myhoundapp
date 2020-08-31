<template>
<div class='c-card'>
 <b-card header-tag='header' footer-tag='footer' class='border-0'>
  <template v-slot:header>
   <h6 class='mb-0 txt-f-med'>Thursday 12 Dec 2019 - 15:10</h6>
  </template>
  <b-col class='u-p-0'>
   <b-card-img v-bind:src='pathImgCard' alt='Image' class='img-card rounded-0' v-if='pathImgCard' />
   <div class='img-card rounded-0 text-center d-flex-ai-center' v-else>
    <b-spinner type='grow' label='Loading...'></b-spinner>
   </div>
  </b-col>
  <b-container class='bv-example-row mb-3'>
   <b-row class='w-100 border-item'>
    <b-col class='name-breed txt-f-sbold text-left text-capitalize txt-l-h-50px' v-if='!onSearch'>
      {{ name }}
    </b-col>
    <b-col class='name-breed txt-f-sbold text-left text-capitalize txt-l-h-50px' v-else>
      {{ nameBreed }}</b-col>
    <b-col class='text-right txt-l-h-50px'>2019</b-col>
   </b-row>
   <b-row class='w-100 border-item border-item txt-l-h-50px'>
    <b-col class=' name-breed text-right text-capitalize'>
      <img src='../assets/common/visible.svg' class='logo' alt=''> 7,732 Views
    </b-col>
   </b-row>
  </b-container>
  <div class="row">
    <div class="col-2 d-flex-jc-center">
      <img src='../assets/common/pin.svg' class='logo' alt=''>
    </div>
    <div class="col-10">
      Location <span></span>
      <div class="row">
        <div class="col-9 txt-f-bold">Riyadh Yard, Saudi Arabia</div>
      </div>
    </div>
  </div>
  <template v-slot:footer>
    <b-dropdown text="View 3 Bids" class='w-100 custom-c-grad-sushi'>
      <b-dropdown-item>Item 1</b-dropdown-item>
      <b-dropdown-item>Item 2</b-dropdown-item>
      <b-dropdown-divider></b-dropdown-divider>
      <b-dropdown-item>Item 3</b-dropdown-item>
    </b-dropdown>
  </template>
</b-card>
</div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Card',
  props: { name: String, onSearch: Boolean, nameBreed: String },
  data() {
    return {
      pathImgCard: '',
    };
  },
  created() {
    if (!this.onSearch) {
      axios.get(`https://dog.ceo/api/breed/${this.name}/images/random`).then((result) => {
        this.pathImgCard = result.data.message;
      });
    } else {
      this.pathImgCard = this.name;
    }
  },
};
</script>

<style scoped>
 .card-header {
   background: rgb(231,48,84);
   background: linear-gradient(264deg, rgba(231,48,84,1) 0%, rgba(185,70,70,1) 35%);
   border-radius: 5px !important;
   border-color: none !important;
   color: white;
 }
 .img-card {
   width: 328px;
   height: 277px;
   -o-object-fit: cover;
   object-fit: cover;
   border-bottom-left-radius: 10px 10px !important;
   border-bottom-right-radius: 10px 10px !important;
   transition: 'all 900ms ease-out';
 }
 .name-breed {
   font-size: 17px;
 }
 .card-body {
   padding: 1.25em 0;
 }
 .c-card {
   margin-top: 12px;
 }
 .card-footer {
   background: white;
   border: none;
 }
 .border-item {
   border-bottom: 1px solid #44444414;
 }
</style>
