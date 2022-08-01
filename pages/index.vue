<template>
<div class="container">
  <div class="row">
    <div class="col-md-12 header-content">
      <div class="row">
        <div class="col-12 col-xl-8 mb-4 mb-xl-0">
          <h3 class="font-weight-bold">Invoices</h3>
          <h6 class="font-weight-normal mb-0">{{ textTotalData }}</h6>
        </div>
        <div class="col-12 col-xl-4">
         <div class="justify-content-end d-flex">
          <div class="dropdown flex-md-grow-1 flex-xl-grow-0">
            <b-dropdown size="lg"  variant="link" toggle-class="text-decoration-none" no-caret>
              <template #button-content>
                <div class="filter-label">
                  Filter by status 
                  <span>
                    <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-chevron-down" viewBox="0 0 16 16">
                      <path fill-rule="evenodd" d="M1.646 4.646a.5.5 0 0 1 .708 0L8 10.293l5.646-5.647a.5.5 0 0 1 .708.708l-6 6a.5.5 0 0 1-.708 0l-6-6a.5.5 0 0 1 0-.708z"/>
                    </svg>
                  </span>
                </div>
              </template>
              <b-dropdown-item @click="filterData('paid')">Paid</b-dropdown-item>
              <b-dropdown-item @click="filterData('pending')">Pending</b-dropdown-item>
              <b-dropdown-item @click="filterData('draft')">Draft</b-dropdown-item>
            </b-dropdown>
          </div>
          <div class="action-button">
            <b-button pill variant="primary" @click="openAdd">
              <svg xmlns="http://www.w3.org/2000/svg" width="27" height="27" fill="currentColor" class="bi bi-plus-circle-fill" viewBox="0 0 16 16">
                <path d="M16 8A8 8 0 1 1 0 8a8 8 0 0 1 16 0zM8.5 4.5a.5.5 0 0 0-1 0v3h-3a.5.5 0 0 0 0 1h3v3a.5.5 0 0 0 1 0v-3h3a.5.5 0 0 0 0-1h-3v-3z"/>
              </svg>
              New Invoice
            </b-button>
          </div>
         </div>
        </div>
      </div>
    </div>
  </div>
  <div class="row">
    <div class="col-md-12">
      <div class="list-content">
        <CardContent 
          v-for="(item, index) in dataMock" 
          :key="index" 
          :data="item"
          @open="openData"
        />
      </div>
    </div>
  </div>
  <FormData
    :show="form"
    :type="typeForm"
    @close="closeForm"
    :editData="editData"
  />
</div>
</template>

<script>
import fakeData from '~/assets/mock/mock-data.json';
export default {
  name: 'Layouts',
  data() {
    return {
      dataMock: [],
      fake: fakeData,
      form: false,
      typeForm: '',
      editData: {}
    }
  },
  mounted() {
    // if (this.dataMock.length == 0) {
    //   localStorage.setItem('dataMock', JSON.stringify(this.fake));
    //   this.dataMock = this.fake;
    // } else {
    //   this.dataMock = JSON.parse(localStorage.getItem('dataMock')) ?? [];
    // }
    this.dataMock = JSON.parse(localStorage.getItem('dataMock')) ?? [];
  },
  methods: {
    openData(value) {
      this.form = true;
      this.typeForm = 'edit';
      this.editData = value;
    },
    closeForm(value) {
      this.form = value;
    },
    openAdd() {
      this.form = true;
      this.typeForm = 'add';
    },
    filterData(value) {
      const dataFake = JSON.parse(localStorage.getItem('dataMock')) ?? [];
      const filterResult =  dataFake.filter( status => status.status === value);
      this.dataMock = filterResult;
    }
  },
  computed: {
    textTotalData() {
      const lengthData = this.dataMock.length;
      if (lengthData == 0) return 'Invoices is not available';
      else if (lengthData == 1) return `There is ${lengthData} total invoice`;
      else return `There are ${lengthData} total invoices`;
    }
  }
}
</script>

<style lang="scss" scoped>
@import '@/assets/style/variable.scss';
.header-content {
  margin: 40px 0px;
  .filter-label {
    color: $white;
    font-size: 14px;
  }
  .action-button {
    margin-left: 15px;
    .btn-primary {
      background-color: $purple-tada!important;
      border-color: $purple-tada!important;
      font-size: 14px;
      padding: 12px 10px;
      svg {
        margin-right: 8px;
      }
    }
  }
}
</style>
