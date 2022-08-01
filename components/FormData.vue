<template>
<div v-if="show">
    <div class="overlay" @click="closeModal"></div>
    <div class="FormData">
        <div class="wraper-form">
            <div class="container">
                <h3 class="font-weight-bold" v-if="type === 'edit'">
                    Edit 
                    <span>#</span>{{editData.id}}
                </h3>
                <h3 class="font-weight-bold" v-else>
                    Add New Invoice
                </h3>
                <div class="row">
                    <h5 class="label-tada">Bill From</h5>
                    <div class="col-md-12">
                        <b-form-group
                            label="Street address"
                        >
                            <b-form-input
                                id="input-1"
                                type="text"
                                v-model="payloadData.bill.from"
                                placeholder="Street address"
                                required
                                class="frm-tada"
                            ></b-form-input>
                        </b-form-group>
                    </div>
                </div>
                <div class="row">
                    <div class="col-md-4">
                        <b-form-group
                            label="City"
                        >
                            <b-form-input
                                id="input-1"
                                type="text"
                                v-model="payloadData.bill.city"
                                placeholder="City"
                                required
                                class="frm-tada"
                            ></b-form-input>
                        </b-form-group>
                    </div>
                    <div class="col-md-4">
                        <b-form-group
                            label="Post Code"
                        >
                            <b-form-input
                                id="input-1"
                                type="text"
                                v-model="payloadData.bill.postcode"
                                placeholder="Post Code"
                                required
                                class="frm-tada"
                            ></b-form-input>
                        </b-form-group>
                    </div>
                    <div class="col-md-4">
                        <b-form-group
                            label="Country"
                        >
                            <b-form-input
                                id="input-1"
                                type="text"
                                v-model="payloadData.bill.country"
                                placeholder="Country"
                                required
                                class="frm-tada"
                            ></b-form-input>
                        </b-form-group>
                    </div>
                </div>
                <div class="row">
                    <h5 class="label-tada">Bill To</h5>
                    <div class="col-md-12">
                        <b-form-group
                            label="Client Name"
                        >
                            <b-form-input
                                id="input-1"
                                type="text"
                                v-model="payloadData.client.name"
                                placeholder="Client Name"
                                required
                                class="frm-tada"
                            ></b-form-input>
                        </b-form-group>
                    </div>
                    <div class="col-md-12">
                        <b-form-group
                            label="Client's Email"
                        >
                            <b-form-input
                                id="input-1"
                                type="email"
                                v-model="payloadData.client.email"
                                placeholder="Client's Email"
                                required
                                class="frm-tada"
                            ></b-form-input>
                        </b-form-group>
                    </div>
                    <div class="col-md-12">
                        <b-form-group
                            label="Street Address"
                        >
                            <b-form-input
                                id="input-1"
                                type="text"
                                v-model="payloadData.client.address"
                                placeholder="Street Addres"
                                required
                                class="frm-tada"
                            ></b-form-input>
                        </b-form-group>
                    </div>
                </div>
                <div class="row">
                    <div class="col-md-4">
                        <b-form-group
                            label="City"
                        >
                            <b-form-input
                                id="input-1"
                                type="text"
                                v-model="payloadData.client.city"
                                placeholder="City"
                                required
                                class="frm-tada"
                            ></b-form-input>
                        </b-form-group>
                    </div>
                    <div class="col-md-4">
                        <b-form-group
                            label="Post Code"
                        >
                            <b-form-input
                                id="input-1"
                                type="text"
                                v-model="payloadData.client.postcode"
                                placeholder="Post Code"
                                required
                                class="frm-tada"
                            ></b-form-input>
                        </b-form-group>
                    </div>
                    <div class="col-md-4">
                        <b-form-group
                            label="Country"
                        >
                            <b-form-input
                                id="input-1"
                                type="text"
                                v-model="payloadData.client.country"
                                placeholder="Country"
                                required
                                class="frm-tada"
                            ></b-form-input>
                        </b-form-group>
                    </div>
                </div>
                <div class="row">
                    <div class="col-md-6">
                        <b-form-group
                            label="Invoice Date"
                        >
                            <b-form-input
                                id="input-1"
                                type="text"
                                v-model="payloadData.client.invoice_date"
                                placeholder="Invoice Date"
                                required
                                class="frm-tada"
                            ></b-form-input>
                        </b-form-group>
                    </div>
                    <div class="col-md-6">
                        <b-form-group
                            label="Payment Terms"
                        >
                            <b-form-input
                                id="input-1"
                                type="text"
                                v-model="payloadData.client.payment_terms"
                                placeholder="Street Addres"
                                required
                                class="frm-tada"
                            ></b-form-input>
                        </b-form-group>
                    </div>
                </div>
                <div class="row">
                    <div class="col-md-12">
                        <b-form-group
                            label="Project Descriptions"
                        >
                            <b-form-input
                                id="input-1"
                                type="text"
                                v-model="payloadData.client.description"
                                placeholder="Project Descriptions"
                                required
                                class="frm-tada"
                            ></b-form-input>
                        </b-form-group>
                    </div>
                </div>

                <h5 class="label-tada">Item List</h5>
                <div class="row" v-for="index in addItemElement" :key="index">
                   <div class="col-md-4">
                        <b-form-group
                            label="Item Name"
                        >
                            <b-form-input
                                id="input-1"
                                type="text"
                                v-model="objItem.name"
                                placeholder="Item Name"
                                required
                                class="frm-tada"
                            ></b-form-input>
                        </b-form-group>
                    </div>
                    <div class="col-md-2">
                        <b-form-group
                            label="Qty"
                        >
                            <b-form-input
                                id="input-1"
                                type="text"
                                v-model="objItem.qty"
                                placeholder="Qty"
                                required
                                class="frm-tada"
                            ></b-form-input>
                        </b-form-group>
                    </div>
                    <div class="col-md-3">
                        <b-form-group
                            label="Price"
                        >
                            <b-form-input
                                id="input-1"
                                type="text"
                                placeholder="Price"
                                v-model="objItem.price"
                                required
                                class="frm-tada"
                            ></b-form-input>
                        </b-form-group>
                    </div>
                    <div class="col-md-2">
                        <b-form-group
                            label="Total"
                        >
                            {{objItem.price * objItem.qty}}
                        </b-form-group>
                    </div>
                    <div class="col-md-1">
                        <div class="action-delete">
                            <label></label>
                            <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-trash3-fill" viewBox="0 0 16 16">
                                <path d="M11 1.5v1h3.5a.5.5 0 0 1 0 1h-.538l-.853 10.66A2 2 0 0 1 11.115 16h-6.23a2 2 0 0 1-1.994-1.84L2.038 3.5H1.5a.5.5 0 0 1 0-1H5v-1A1.5 1.5 0 0 1 6.5 0h3A1.5 1.5 0 0 1 11 1.5Zm-5 0v1h4v-1a.5.5 0 0 0-.5-.5h-3a.5.5 0 0 0-.5.5ZM4.5 5.029l.5 8.5a.5.5 0 1 0 .998-.06l-.5-8.5a.5.5 0 1 0-.998.06Zm6.53-.528a.5.5 0 0 0-.528.47l-.5 8.5a.5.5 0 0 0 .998.058l.5-8.5a.5.5 0 0 0-.47-.528ZM8 4.5a.5.5 0 0 0-.5.5v8.5a.5.5 0 0 0 1 0V5a.5.5 0 0 0-.5-.5Z"/>
                            </svg>
                        </div>
                    </div>
                </div>

                <div class="row">
                    <div class="col-md-12">
                        <b-button pill block variant="primary" class="cancel" @click="addItem">+ Add New Item</b-button>
                    </div>
                </div>
                <div class="row">
                    <div class="col-md-12">
                        <div class="final-action">
                            <b-button pill variant="primary" class="cancel" @click="closeModal">Cancel</b-button>
                            <b-button pill variant="danger" @click="deleteData(payloadData.id)" v-if="type === 'edit'">Delete Data</b-button>
                            <b-button pill variant="primary" class="tada-submit" @click="saveData">Save Changes</b-button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</div>
</template>
<script>
export default {
    name: "FormData",
    props: {
        show: {
            type: Boolean,
            default: false,
        },
        type: {
            type: String,
            default: 'edit'
        },
        editData: {
            type: Object,
            default: () => {}
        }
    },
    data() {
        return {
            payloadData: {
                id: null,
                status: null,
                bill: {
                    from: null,
                    city: null,
                    country: null,
                    postcode: null
                },
                client: {
			        name: null,
			        email: null,
			        address: null,
			        city: null,
			        postcode: null,
                    country: null,
                    invoice_date: null,
                    payment_terms: null,
                    description: null
		        },
                item: [
                
                ]
            },
            objItem:{
                name: null,
				qty: null,
				price: null,
				total: null
            },
            addItemElement: 0
        }
    },
    watch: {
        editData: {
            deep: true,
            handler: function(value) {
                if(this.type === 'edit' && value.id) {
                    const mockData = JSON.parse(localStorage.getItem('dataMock')) ?? []
                    mockData.forEach((item) => {
                        if(item.id == value.id){
                            this.payloadData = item;
                        }
                    });
                }
            }
        },
        type: function(value) {
            if (value === 'add') {
                this.resetData();
            }
        }
    },
    methods: {
        closeModal() {
            this.$emit('close', false);
        },
        addItem() {
            this.addItemElement += 1;
            this.payloadData.item.push(this.objItem);
        },
        saveData() {
            const status = ['paid', 'pending', 'draft'];
            var item = status[Math.floor(Math.random()*status.length)];
            this.payloadData.status = item;
            this.payloadData.id = Math.floor(Math.random()*90000) + 10000;
            this.payloadData.item.push(this.objItem);
            const localData = JSON.parse(localStorage.getItem('dataMock')) ?? [];
            localData.push(this.payloadData);
            localStorage.setItem('dataMock', JSON.stringify(localData));
            location.reload();
            this.resetData();
            this.resetObj();
        },
        deleteData(id) {
            const mockData = JSON.parse(localStorage.getItem('dataMock')) ?? [];
            const deleteData = mockData.filter(function(value){ 
                return value.id != id; 
            });

            localStorage.setItem('dataMock', JSON.stringify(deleteData));
            location.reload();
        },
        resetData() {
            this.payloadData = {
                id: null,
                status: null,
                bill: {
                    from: null,
                    city: null,
                    country: null,
                    postcode: null
                },
                client: {
			        name: null,
			        email: null,
			        address: null,
			        city: null,
			        postcode: null,
                    country: null,
                    invoice_date: null,
                    payment_terms: null,
                    description: null
		        },
                item: []
            };
            this.objItem = {
                name: null,
				qty: null,
				price: null,
				total: null
            };
        },
        resetObj() {
            this.objItem = {
                name: null,
				qty: null,
				price: null,
				total: null
            }
        }
    }
}
</script>


<style lang="scss" scoped>
@import '@/assets/style/variable.scss';
.overlay {
    position: fixed;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: rgba(0,0,0,0.5);
    z-index: 99;
    }
.FormData {
    position: absolute;
    left: 100px;
    height: 100vh;
    width: 500px;
    background: $tada-dark;
    top: 0;
    z-index: 999;
    padding: 20px 0px;
    overflow-y: scroll;
    -webkit-animation: slide-in-left 1s ease-in both;
	animation: slide-in-left 1s ease-in both;
    @include breakpoint(mobileonly) {
        width: 100%!important;
        left: 0px;
    }
    &::-webkit-scrollbar {
        width: 7px;
    }
    &::-webkit-scrollbar-thumb {
        background-color: $tada-dark;
        border-radius: 6px;
        border: 0px solid $tada-dark;
    }
    ::-webkit-scrollbar-track {
        background: #fff;
    }
    .wraper-form {
        padding: 20px;
        h3{
            margin-bottom: 20px;
        }
        .label-tada {
            color: $purple-tada;
            font-size: 16px;
            padding-left: 15px;
            padding-bottom: 15px;
        }
    }
    .frm-tada {
        background-color: $tada-light;
        color: $white;
        border-color: $tada-light;
    }
    .action-delete {
        cursor: pointer;
    }
    .cancel{
        background-color: $cancel;
        color: $white;
        border-color: $cancel;
    }
    .tada-submit{
        background-color: $purple-tada;
        color: $white;
        border-color: $purple-tada;
    }
    .final-action {
        text-align: right;
        margin-top: 20px;
    }
}
    
</style>