<template>
    <div>
        <div class="field">
            <label class="label">First Name</label>
            <div class="control">
                <input
                  class="input"
                  type="text"
                  placeholder="First Name"
                  v-model="fname"
                />
            </div>
        </div>

        <div class="field">
            <label class="label">Last Name</label>
            <div class="control">
                <input
                  class="input"
                  type="text"
                  placeholder="Last Name"
                  v-model="lname"
                />
            </div>
        </div>

        <div class="control">
            <button class="button is-success" @click="updateUser">UPDATE</button>
        </div>
    </div>
</template>


<script>
import axios from "axios";

export default {
    name: "EditProduct",
    data() {
        return {
            fname: "",
            lname: "",
        };
    },

    created: function () {
        this.getUserById();
    },
    methods: {
        // Get User By Id
        async getUserById() {
            try {
                const response = await axios.get(
                    `https://naughty-sandals-foal.cyclic.app/users/${this.$route.params.id}`
                );

                // this.productName = response.data.product_name;
                // this.productPrice = response.data.product_price;
                this.fname.value = response.data.fname;
                this.lname.value = response.data.lname;
            } catch (err) {
                console.log(err);
            }
            console.log("beer");
        },
        // // Update product
        // async updateProduct() {
        //     try {
        //         await axios.put(
        //             `https://naughty-sandals-foal.cyclic.app/products/${this.$route.params.id}`,
        //             {
        //                 product_name: this.productName,
        //                 product_price: this.productPrice,
        //             }
        //         );

        //         this.productName = "";
        //         this.productPrice = "";
        //         this.$router.push("/");

        //     } catch (err) {
        //         console.log(err);
        //     }
        // },
    },
};

</script>