<template>
  <tf-form class="form" ref="form" :model="user" :rules="rules">
    <tf-form-item label="用户名" prop="username">
      <!-- <tf-input v-model="user.username"></tf-input> -->
      <tf-input :value="user.username" @input="user.username=$event" placeholder="请输入用户名"></tf-input>
    </tf-form-item>
    <tf-form-item label="密码" prop="password">
      <tf-input type="password" v-model="user.password"></tf-input>
    </tf-form-item>
    <tf-form-item>
      <tf-button type="primary" @click="login">登 录</tf-button>
    </tf-form-item>
  </tf-form>
</template>

<script>
import TfForm from './form/Form'
import TfFormItem from './form/FormItem'
import TfInput from './form/Input'
import TfButton from './form/Button'
export default {
  components: {
    TfForm,
    TfFormItem,
    TfInput,
    TfButton
  },
  data () {
    return {
      user: {
        username: '',
        password: ''
      },
      rules: {
        username: [
          {
            required: true,
            message: '请输入用户名'
          }
        ],
        password: [
          {
            required: true,
            message: '请输入密码'
          },
          {
            min: 6,
            max: 12,
            message: '请输入6-12位密码'
          }
        ]
      }
    }
  },
  methods: {
    login () {
      console.log('button')
      this.$refs.form.validate(valid => {
        if (valid) {
          alert('验证成功')
        } else {
          alert('验证失败')
          return false
        }
      })
    }
  }
}
</script>

<style>
  .form {
    width: 30%;
    margin: 150px auto;
  }
</style>
