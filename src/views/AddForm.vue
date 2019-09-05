
<template>
  <a-form :form="form" @submit="handleSubmit">
    <a-form-item label="运单号" :label-col="{ span: 9 }" :wrapper-col="{ span: 10 }">
      <a-input v-decorator="[
'运单号',
{rules: [{ required: true, message: '请输入运单号!' }]}
]" />
    </a-form-item>

    <a-form-item label="收件人" :label-col="{ span: 9 }" :wrapper-col="{ span: 10 }">
      <a-input v-decorator="[
'收件人',
{rules: [{ required: true, message: '收件人都能忘？' }]}
]" />
    </a-form-item>

    <a-form-item label="电话" :label-col="{ span: 9 }" :wrapper-col="{ span: 10 }">
      <a-input v-decorator="[
'电话',
{rules: [{ required: true, message: '电话给我写进去!' }]}
]" />
    </a-form-item>
    <a-form-item label="重量" :label-col="{ span: 9 }" :wrapper-col="{ span: 10 }">
      <a-input v-decorator="[
'重量',
{rules: [{ required: true, message: '自己秤秤重!' }]}
]" />
    </a-form-item>
    <a-form-item :wrapper-col="{ span: 18, offset: 5 }">
      <a-button type="primary" html-type="submit">提交</a-button>
    </a-form-item>
  </a-form>
</template>

<script>
export default {
  data() {
    return {
      formLayout: "horizontal",
      form: this.$form.createForm(this)
    };
  },
  methods: {
    handleSubmit(e) {
      e.preventDefault();
      this.form.validateFields((err, values) => {
        if (!err) {
          this.$store.dispatch("createTodos", values);
        }
      });
    }
  }
};
</script>