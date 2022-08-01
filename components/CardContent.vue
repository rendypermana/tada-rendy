<template>
    <div class="CardContent" @click="detailData(data)">
        <div class="contentList">
            <div class="contentList__item">
                <div class="id">
                    <span>#</span>{{ data.id }}
                </div>
                <div class="date">
                    Due {{ data.client.invoice_date }}
                </div>
                <div class="name">
                    {{ data.client.name }}
                </div>
                <div class="currency">
                    {{ totalPrice }}
                </div>
                <div class="action">
                    <button class="btn btn-success" v-if="data.status === 'paid'">
                        Paid
                    </button>
                    <button class="btn btn-warning" v-else-if="data.status === 'pending'">
                        Pending
                    </button>
                    <button class="btn btn-light" v-else-if="data.status === 'draft'">
                        Draft
                    </button>
                    <span> > </span>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default{
    name: "CardContent",
    props: {
        data: {
            type: Object,
            default: () => {},
        }
    },
    methods: {
        detailData(value) {
            this.$emit('open', value);
        },
    },
    computed: {
        totalPrice() {
            let total = 0;
            this.data.item.forEach((data) => {
                total += data.total;
            });
            const money = total;
            const format = money.toString().split('').reverse().join('');
            const convert = format.match(/\d{1,3}/g);
            const rupiah = 'IDR ' + convert.join('.').split('').reverse().join('')
            return rupiah;
        }
    }
}
</script>


<style lang="scss" scoped>
@import '@/assets/style/variable.scss';
.CardContent {
    padding: 15px 20px;
    background-color: $tada-light;
    border-radius: 8px;
    color: $white;
    margin-bottom: 15px;
    cursor: pointer;
    &:hover {
        border: 1px solid $purple-tada;
    }
    .contentList {
        &__item {
            width: 100%;
            display: flex;
            div {
                width: 25%;
            }
            .action {
                text-align: right;
                span {
                    text-align: right;
                }
            }
        }
    }
}
</style>