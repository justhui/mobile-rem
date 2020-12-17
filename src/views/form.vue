<template>
  <div class="home">
    <Form
      ref="formValidate"
      :model="formValidate"
      :rules="ruleValidate"
      :label-width="80"
    >
      <FormItem label="name" prop="name">
        <Input
          v-model="formValidate.name"
          placeholder="Enter your name"
        />
      </FormItem>
      <FormItem label="phone" prop="phone">
        <Input
          v-model="formValidate.phone"
          placeholder="Enter your name"
       />
      </FormItem>
      <FormItem label="date" prop="date">
        --{{formValidate.date}}**
        <day-hour :data-form.sync="formValidate.date"></day-hour>
      </FormItem>
    </Form>
  </div>
</template>
<script>
import dayHour from './dayHour'
export default {
  components: {
    dayHour
  },
  data() {
    return {
      formValidate: {
        name: "",
        phone: '',
        date: 9999999,
      },
      ruleValidate: {
        name: [
          {
            required: true,
            message: "The name cannot be empty",
            trigger: "blur",
          },
        ],
        phone: [
          {
            required: true,
            message: "Mailbox cannot be empty",
            trigger: "blur",
          },
          { type: "email", message: "Incorrect email format", trigger: "blur" },
        ],
        date: [
          {
            required: true,
            message: "Please select the date",
            trigger: "blur",
          }
        ]
      },
    };
  }
};
</script>
<style lang="scss" scoped>
  .home {
    width: 50%;
    margin: 20vh 10vh;
    display: flex;
    justify-content: center;
  }
  
</style>