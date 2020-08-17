<template>
  <div class="app-container">
    <el-form ref="form" label-width="100px" label-position="right">
      <el-form-item label="城市:">
        <el-cascader
          v-model="selectedOptions"
          placeholder="请选择城市"
          expand-trigger="hover"
          size="large"
          :options="options"
          filterable
          :show-all-levels="false"
          @change="onChange"
        />
      </el-form-item>
      <el-form-item>
        <el-button type="primary" @click="onSubmit">提交</el-button>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
import { provinceAndCityData } from 'element-china-area-data'
export default {
  data() {
    return {
      options: provinceAndCityData,
      selectedOptions: [],
      query: {
        city: '上海'
      }
    }
  },

  created() {
    this.initCities()
    console.log(this.selectedOptions)
  },
  methods: {
    initCities() {
      let tmpCity = ''
      for (let i = 0; i < this.options.length; i++) {
        for (let j = 0; j < this.options[i].children.length; j++) {
          if (this.options[i].children[j].label === '市辖区') {
            this.options[i].children[j].label = this.options[i].label
          }
          tmpCity = this.options[i].children[j].label
          if (tmpCity.match(/(.*[^市])市$/g) !== null) {
            this.options[i].children[j].label = tmpCity.substr(0, tmpCity.length - 1)
          }
          if (this.options[i].children[j].label === this.query.city) {
            this.selectedOptions = [
              this.options[i].value,
              this.options[i].children[j].value
            ]
          }
        }
      }
    },
    onSubmit() {
      console.log(this.query)
    },
    onChange() {
      for (let i = 0; i < this.options.length; i++) {
        if (this.options[i].value === this.selectedOptions[0]) {
          for (let j = 0; j < this.options[i].children.length; j++) {
            if (this.options[i].children[j].value === this.selectedOptions[1]) {
              this.query.city = this.options[i].children[j].label
            }
          }
        }
      }
      console.log(this.query.city)
    }
  }
}
</script>

<style scoped>
    .line{
        text-align: center;
    }
</style>
