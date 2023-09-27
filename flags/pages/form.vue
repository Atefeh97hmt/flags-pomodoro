<template>


<div class="container">
<form class="flex flex-col items-center"> 

    <div class="column is-12">
            <label class="label">Email</label>
            <p class="control has-icon has-icon-right">
                <input v-bind="email" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" name="email"  type="email" placeholder="Email">

                <div class="text-red-500">{{ errors.email }}</div>

            </p>
        </div>

        <div class="column is-12">
            <label class="label">Name</label>
            <p class="control has-icon has-icon-right">
                <input  v-bind="name" class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" name="name"  type="text" placeholder="text">
             
                <div class="text-red-500">{{ errors.name }}</div>

            </p>
        </div>

        <div class="column is-12">
            <label class="label">Phone number</label>
            <p class="control has-icon has-icon-right">
                <input v-bind="phone"  class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500" name="phone"  placeholder="phone">
                <div class="text-red-500">{{ errors.phone }}</div>

            </p>
        </div>
       
</form>
</div>
</template>

<script setup>
import { useForm } from 'vee-validate';
import * as yup from 'yup';

const { errors, defineInputBinds } = useForm({
  validationSchema: yup.object({
    email: yup.string().email().required(),
    name: yup.string().required().min(2).max(256),
    phone: yup.number().required().test((value, context) => {
        const customPhoneCondition = valid(value)
        return customPhoneCondition || context.createError({ message: "Please Enter a Correct Phone Number" })
    }),
  }),
});

const email = defineInputBinds('email');
const name = defineInputBinds('name');
const phone = defineInputBinds('phoneNumber')


const phoneNumberValidation = /^((+98|0)?9\d{9})$/;
const valid = (phone) => {
    console.log("phoneNumber ==>", phone)
    return phone.length && phone.test(phoneNumberValidation)
}

</script>


