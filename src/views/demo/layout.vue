<template>
  <div class="app-container">
    <el-form ref="form" :model="form" label-width="100px">
      <el-row :gutter="20">
        <el-col :span="8">
          <el-form-item label="活动名称" style="width: 420px">
            <el-input v-model="form.name" />
          </el-form-item>
        </el-col>
        <el-col :span="8">
          <el-form-item label="活动区域">
            <el-select v-model="form.region" placeholder="请选择活动区域" style="width: 320px">
              <el-option label="区域一" value="shanghai" />
              <el-option label="区域二" value="beijing" />
            </el-select>
          </el-form-item>
        </el-col>
      </el-row>
      <el-row :gutter="20">
        <el-col :span="8">
          <el-form-item label="计数">
            <el-input-number v-model="form.num" :min="1" :max="10" style="width: 320px" />
          </el-form-item>
        </el-col>
        <el-col :span="8">
          <el-form-item label="SLIDER">
            <el-slider v-model="form.slider" :step="10" style="width: 320px" />
          </el-form-item>
        </el-col>
      </el-row>
      <el-row :gutter="20">
        <el-col :span="8">
          <el-form-item label="活动图片" style="width: 420px">
            <el-upload
              class="upload-demo"
              action="https://jsonplaceholder.typicode.com/posts/"
              :on-preview="handlePreview"
              :on-remove="handleRemove"
              :file-list="fileList"
              list-type="picture"
            >
              <el-button size="small" type="primary" style="width: 320px">点击上传</el-button>
              <div slot="tip" class="el-upload__tip">只能上传jpg/png文件，且不超过500kb</div>
            </el-upload>
          </el-form-item>
        </el-col>
        <el-col :span="8">
          <el-form-item label="活动日期" style="width: 420px">
            <el-date-picker v-model="form.date1" type="date" placeholder="选择日期" />
          </el-form-item>
        </el-col>
      </el-row>
      <el-row :gutter="20">
        <el-col :span="8">
          <el-form-item label="活动性质" style="width: 420px">
            <el-checkbox-group v-model="form.type">
              <el-checkbox label="美食" name="type" />
              <el-checkbox label="地推活动" name="type" />
              <el-checkbox label="线下主题活动" name="type" />
              <el-checkbox label="单纯品牌曝光" name="type" />
            </el-checkbox-group>
          </el-form-item>
        </el-col>
        <el-col :span="8">
          <el-form-item label="特殊资源" style="width: 420px">
            <el-radio-group v-model="form.resource">
              <el-radio label="线上品牌商赞助" />
              <el-radio label="线下场地免费" />
            </el-radio-group>
          </el-form-item>
        </el-col>
      </el-row>
      <el-row :gutter="20">
        <el-col :span="8">
          <el-form-item label="活动形式" style="width: 420px">
            <el-input v-model="form.desc" type="textarea" />
          </el-form-item>
        </el-col>
        <el-col :span="8">
          <el-form-item label="即时配送">
            <el-switch v-model="form.delivery" />
          </el-form-item>
        </el-col>
      </el-row>
      <el-row :gutter="20">
        <el-col :span="8">
          <el-form-item label="" style="width: 420px">
            <el-button>取消</el-button>
            <el-button type="primary" @click="onSubmit">立即创建</el-button>
          </el-form-item>
        </el-col>
      </el-row>
    </el-form>
  </div>
</template>

<script>
export default {
  name: 'Layout',

  data() {
    return {
      form: {
        name: '',
        region: '',
        date1: '',
        date2: '',
        delivery: false,
        type: [],
        resource: '',
        desc: '',
        num: 0,
        slider: 10
      },
      fileList: [
        { name: 'food.jpeg', url: 'https://fuss10.elemecdn.com/3/63/4e7f3a15429bfda99bce42a18cdd1jpeg.jpeg?imageMogr2/thumbnail/360x360/format/webp/quality/100' }
      ]
    }
  },
  created() {
  },
  methods: {
    onSubmit() {
      console.log(this.form)
    },
    handleRemove(file, fileList) {
      console.log(file, fileList)
    },
    handlePreview(file) {
      console.log(file)
    }
  }
}
</script>

<style scoped>

</style>
