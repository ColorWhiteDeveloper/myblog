在element-plus中，el-upload是一个十分好用的组件，接下来就
开始放一下自己写的el-upload上传图片的功能
``` vue
<template>
  <el-upload
    v-model:file-list="fileList"
    class="upload-demo"
    action=""//文件上传保存地址
    multiple
    :show-file-list="flag"//是否显示上传成功的文件列表
    :before-upload="beforeUpload"//上传之前的钩子函数
    :limit="3"//限制选中文件个数
    :on-success="handleSuccess"//上传成功之后的回调函数
    :on-change="handleChange"
  >
  <!-- :auto-upload="flag" -->
    <el-button type="primary">Click to upload</el-button>
  </el-upload>
  <div v-html="imgShow"></div>//显示上传成功的图片
</template>
<script lang="ts" setup>
import { ref } from 'vue'
import { ElMessage, ElMessageBox } from 'element-plus'
import type { UploadProps, UploadUserFile , UploadFile, UploadFiles} from 'element-plus'
const flag =false;
const fileList = ref<UploadUserFile[]>([]);
const imgShow = ref('');
const handleSuccess = (response: any, uploadFile: UploadFile, uploadFiles: UploadFiles)=>{
  console.log('Response',response);//上传成功之后响应数据
  console.log('successFile',uploadFile);
  console.log('successFiles',uploadFiles);
  let str = response.data;//图片路径
  imgShow.value = `<img src='${str}' />`

}
const beforeUpload: UploadProps['beforeUpload'] = (rawFile) => {
  // console.log(rawFile);
  if (rawFile.type !== 'image/jpeg') {
    ElMessage.error('Avatar picture must be JPG format!')
    return false
  } else if (rawFile.size / 1024 / 1024 > 2) {
    ElMessage.error('Avatar picture size can not exceed 2MB!')
    return false
  }
  return true
}
const handleChange  = (uploadFile: UploadFile, uploadFiles: UploadFiles)=>{
  // console.log(uploadFile,uploadFiles);
}
</script>
```