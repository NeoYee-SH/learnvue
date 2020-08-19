<template>
  <div class="app-container">
    <el-form ref="form" :model="form" :rules="formRules" label-width="120px">
      <el-form-item label="Integer:" prop="integer">
        <el-input v-model="form.integer" placeholder="支持整数" class="form-width" @input="form.integer = form.integer.match(pattern.integer)[0]" />
      </el-form-item>
      <el-form-item label="Decimal:" prop="decimal">
        <el-input v-model="form.decimal" placeholder="支持两位小数" class="form-width" @input="form.decimal = form.decimal.match(pattern.decimal)[0]" />
      </el-form-item>
      <el-form-item label="English:" prop="english">
        <el-input v-model="form.english" placeholder="支持英文字母+数字+半角的逗号和句号" class="form-width" @input="form.english = form.english.match(pattern.english)[0]"/>
      </el-form-item>
      <el-form-item label="Chinese:" prop="chinese">
        <el-input v-model="form.chinese" class="form-width" placeholder="支持中文" @input="form.chinese = form.chinese.match(pattern.chinese)[0]"/>
      </el-form-item>
      <el-form-item label="Mobile:" prop="mobile">
        <el-input v-model="form.mobile" class="form-width" placeholder="支持11位手机号" @input="form.mobile = form.mobile.match(pattern.integer)[0]"/>
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="onSubmit">Create</el-button>
        <el-button @click="onCancel">Cancel</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
export default {
  name: 'Input',
  data() {
    const validateMobile = (rule, value, callback) => {
      if (value.match(this.pattern.mobile) === null) {
        callback(new Error('Wrong cell phone number'))
      } else {
        callback()
      }
    }
    return {
      form: {
        integer: '',
        decimal: '',
        english: '',
        chinese: '',
        mobile: ''
      },
      formRules: {
        integer: [{ required: true, trigger: 'blur' }],
        decimal: [{ required: true, trigger: 'blur' }],
        english: [{ required: true, trigger: 'blur' }],
        chinese: [{ required: true, trigger: 'blur' }],
        mobile: [{ required: true, trigger: 'blur', validator: validateMobile }]

      },
      pattern: {
        integer: /(^\d*)/g,
        decimal: /(^\d*)(\.?\d{0,2})/g,
        english: /(^[\w\s.,]*)/g,
        chinese: /(^[\u4e00-\u9fa5]*)/g,
        mobile: /(^1[3-9]\d{9}$)/g
      }
    }
  },
  methods: {
    onSubmit() {
      this.$refs.form.validate(valid => {
        if (valid) {
          console.log(this.form)
        } else {
          console.log('error submit!!')
          return false
        }
      })
    },
    onCancel() {
      this.$message({
        message: 'cancel!',
        type: 'warning'
      })
    },
    checkChinese(chinese) {
      return chinese === '中'
    }
  }
}
</script>

<style scoped>
    .form-width {
        width: 500px;
    }
</style>
