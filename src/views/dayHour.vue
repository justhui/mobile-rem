<template>
    <Form
      ref="formValidate"
      :model="formValidate"
      :rules="ruleValidate"
      :label-width="80"
    >
      <FormItem label="day" prop="day">
        <InputNumber :max="365" :min="0" v-model="formValidate.day"></InputNumber>
      </FormItem>
      <FormItem label="hour" prop="hour">
        <InputNumber :max="24" :min="0" v-model="formValidate.hour"></InputNumber>
      </FormItem>
      <FormItem label="minute" prop="minute">
        <InputNumber :max="60" :min="0" v-model="formValidate.minute"></InputNumber>

      </FormItem>
      <FormItem label="second" prop="second">
        <InputNumber :max="60" :min="0" v-model="formValidate.second"></InputNumber>
      </FormItem>
    </Form>
</template>
<script>
export default {
  props: {
    dataForm: {
      type: Number,
      default:0
    }
  },
  data() {
    return {
      formValidate: {
        day:0,
        hour:0,
        minute:0,
        second:0
      },
      ruleValidate: {
        day: [
          {
            required: true,
            type:'number',
            message: "The name cannot be empty",
            trigger: "blur",
          },
        ],
        hour: [
          {
            type:'number',
            required: true,
            message: "Mailbox cannot be empty",
            trigger: "blur",
          },
        ],
        minute: [
          {
            type:'number',
            required: true,
            message: "Please select the date",
            trigger: "blur",
          },
        ],
        second: [
          {
            type:'number',
            required: true,
            message: "Please select the date",
            trigger: "blur",
          },
        ],
      },
    };
  },
  mounted(){
    const day = parseInt(this.dataForm /(24*60*60))
    const hour = parseInt((this.dataForm - day*24*60*60) / 3600)
    const minute = parseInt((this.dataForm - day*24*60*60 - hour*3600) / 60)
    const second = parseInt(this.dataForm - day*24*60*60 - hour*3600 - minute*60)
    this.formValidate = {
      day,
      hour,
      minute,
      second
    }
  },
  watch: {
    formValidate:{
      handler(){
        console.log('1111',this.formValidate)
        const day = parseInt(this.formValidate.day) *24*60*60
        const hour = parseInt(this.formValidate.hour)*3600
        const minute =parseInt(this.formValidate.minute) *  60
        const second =parseInt(this.formValidate.second )
        const data = day + hour + minute + second
        this.$emit('update:data-form',data)
      },
      deep:true,
      immediate:true
    }
  },
  methods: {
    add_0 (val){
      return String(val).length < 2 ? ('0'+val) : String(val)
    }
  }
};
</script>
<style lang="scss" scoped>

</style>