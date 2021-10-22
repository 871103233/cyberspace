<!--
页面：登录组件
路由：-
作者：阎超
时间：2021-10-13
编辑记录:
    2021-00-13 阎超 编写登录表单组件

-->
<template>
  <a-form :label-col="labelCol" :wrapper-col="wrapperCol">
    <a-form-item label="Activity name" v-bind="validateInfos.name">
      <a-input v-model:value="modelRef.name" />
    </a-form-item>
    <a-form-item label="Sub name" v-bind="validateInfos['sub.name']">
      <a-input v-model:value="modelRef.sub.name" />
    </a-form-item>
    <a-form-item :wrapper-col="{ span: 14, offset: 4 }">
      <a-button type="primary" @click.prevent="onSubmit">Create</a-button>
      <a-button style="margin-left: 10px" @click="reset">Reset</a-button>
    </a-form-item>
  </a-form>
</template>
<script>
import { defineComponent, reactive, toRaw } from "vue";
import { Form } from "ant-design-vue";
const useForm = Form.useForm;
export default defineComponent({
  setup() {
    const modelRef = reactive({
      name: "",
      sub: {
        name: "",
      },
    });
    const { resetFields, validate, validateInfos } = useForm(
      modelRef,
      reactive({
        name: [
          {
            required: true,
            message: "Please input name",
          },
        ],
        "sub.name": [
          {
            required: true,
            message: "Please input sub name",
          },
        ],
      })
    );
    const onSubmit = () => {
      validate()
        .then((res) => {
          console.log(res, toRaw(modelRef));
        })
        .catch((err) => {
          console.log("error", err);
        });
    };
    const reset = () => {
      resetFields();
    };
    return {
      labelCol: { span: 8 },
      wrapperCol: { span: 16 },
      validateInfos,
      reset,
      modelRef,
      onSubmit,
    };
  },
});
</script>
<style scoped lang="less"></style>
