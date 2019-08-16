<template>
  <div>
    <div class="crumbs">
     <el-row>
         <el-col :span="22">     
      <el-breadcrumb separator="/">
        <el-breadcrumb-item>
          <i class="el-icon-lx-calendar">奖品管理</i>
        </el-breadcrumb-item>
        <el-breadcrumb-item>{{this.$route.query.name}}</el-breadcrumb-item>
      </el-breadcrumb>
       </el-col>
     <el-col :span="2">
          <el-button type="primary">保存</el-button>
        </el-col>
     </el-row>       
    </div>

     <div class="container">
          <el-divider content-position="left">奖品信息</el-divider>
          <el-form :model="ruleForm" :rules="rules" ref="ruleForm" label-width="100px">
            <el-form-item label="奖品名称" prop="name" placeholder="请输入奖品名称">
              <el-input v-model="ruleForm.name"></el-input>
            </el-form-item>
            <el-form-item label="奖品金额" prop="price" placeholder="请输入奖品金额">
              <el-input v-model="ruleForm.price"></el-input>
            </el-form-item>
            <el-form-item label="奖品图片">
              <el-upload
            class="avatar-uploader"
            action="http://127.0.0.1:8082/upload/file"
            :show-file-list="false"
            :on-success="handleAvatarSuccess"
            :before-upload="beforeAvatarUpload">
            <img v-if="imgUrl" :src="imgUrl" class="avatar" />
            <i v-else class="el-icon-plus avatar-uploader-icon"></i>
          </el-upload>
        </el-form-item>  
          </el-form>
        </div>
    </el-row>
  </div>
</template>

<script>
export default {
  name: "editor",
  data() {
    return {
      imgUrl: '',
      ruleForm: {
        name: '',
        price: '',
      },
      rules: {
        name: [{ required: true, message: "请输入活动名称", trigger: "blur" }],
        price: [{ required: true, message: "请输入奖品金额", trigger: "blur" }]
      }
    };
  },
  methods: {
    submitForm(formName) {
      this.$refs[formName].validate(valid => {
        if (valid) {
          alert("submit!");
        } else {
          console.log("error submit!!");
          return false;
        }
      });
    },
    resetForm(formName) {
      this.$refs[formName].resetFields();
    }
  },

   /**图片 */
    handleAvatarSuccess(res, file) {
      this.imgUrl = URL.createObjectURL(file.raw);
    },
    beforeAvatarUpload(file) {
      const isJPG = file.type === "image/jpeg";
      const isLt2M = file.size / 1024 / 1024 < 2;

      if (!isJPG) {
        this.$message.error("上传头像图片只能是 JPG 格式!");
      }
      if (!isLt2M) {
        this.$message.error("上传头像图片大小不能超过 2MB!");
      }
      return isJPG && isLt2M;
    }
};
</script>

<style scoped>
  .avatar-uploader .el-upload {
    border: 1px dashed #d9d9d9;
    border-radius: 6px;
    cursor: pointer;
    position: relative;
    overflow: hidden;
  }
  .avatar-uploader .el-upload:hover {
    border-color: #409EFF;
  }
  .avatar-uploader-icon {
    font-size: 28px;
    color: #8c939d;
    width: 178px;
    height: 178px;
    line-height: 178px;
    text-align: center;
  }
  .avatar {
    width: 360px;
    height: 180px;
    display: block;
  }
</style>