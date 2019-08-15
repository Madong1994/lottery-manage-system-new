<template>
  <div>
    <div class="crumbs">
      <el-breadcrumb separator="/">
        <el-breadcrumb-item>
          <i class="el-icon-lx-calendar"></i> lottery
        </el-breadcrumb-item>
        <el-breadcrumb-item>赞助商类型</el-breadcrumb-item>
      </el-breadcrumb>
    </div>
    <div class="container">
      <el-row>
        <div>
          <el-button type="primary" @click="open" round>
            <i class="el-icon-lx-add"></i> 新增
          </el-button>
        </div>
      </el-row>

      <el-divider content-position="left">赞助商类型</el-divider>

      <el-row class="ms-layout-start-horizontal">
        <el-card v-for="item in sponsorList" :key="item" class="margin-left-20" shadow="hover">
          <div class="width-130-height-156 ms-layout-wrap-vertical">
            <div class="ms-layout-center-wrap-horizontal" style="width:100%;height:25%;">
              <el-avatar :size="60" style="font-size:36px;background:#409EFF;">
                <i class="el-icon-lx-emojifill"></i>
              </el-avatar>
            </div>
            <div class="ms-layout-center-wrap-horizontal" style="width:100%;height:25%;">
              <el-tag
                @click="drawer = true"
                type="warning"
                class="ms-layout-center-wrap-horizontal"
                style="width: 60%"
              >商户</el-tag>
            </div>
          </div>
        </el-card>
      </el-row>
      <!-- 分页组件 -->
      <el-row class="ms-layout-start-horizontal">
        <el-pagination background layout="prev, pager, next" :total="1000"></el-pagination>
      </el-row>
    </div>

    
    <!-- 新增赞助商 -->
    <el-drawer title="新增赞助商类型" :visible.sync="addDrawer" :direction="direction">
      <div class="debug ms-layout-wrap-vertical" style="width:100%;height:100%">
        <el-form :label-position="labelPosition" label-width="80px" :model="formLabelAlign">
          <el-form-item label="名称">
            <el-input v-model="formLabelAlign.name"></el-input>
          </el-form-item>
          <el-form-item label="活动区域">
            <el-input v-model="formLabelAlign.region"></el-input>
          </el-form-item>
          <el-form-item label="活动形式">
            <el-input v-model="formLabelAlign.type"></el-input>
          </el-form-item>
        </el-form>
      </div>
    </el-drawer>
  </div>
</template>
<style>
</style>

<script>
export default {
  name: "sponsortype",
  data() {
    return {
      sponsorList: [1, 2, 3, 4, 5, 6, 7, 8],
      value: "已开启",
      drawer: false,
      addDrawer: false,
      direction: "rtl",
      formLabelAlign: {
          name: '',
          region: '',
          type: ''
        }
    };
  },
  methods: {
    addSponsor: function() {
      this.$data.addDrawer = true;
      console.log(this.addDrawer);
    },
    open() {
        this.$prompt('请输入类型名称', '提示', {
          confirmButtonText: '确定',
          cancelButtonText: '取消',
          // inputPattern: /[\w!#$%&'*+/=?^_`{|}~-]+(?:\.[\w!#$%&'*+/=?^_`{|}~-]+)*@(?:[\w](?:[\w-]*[\w])?\.)+[\w](?:[\w-]*[\w])?/,
          // inputErrorMessage: '邮箱格式不正确'
        }).then(({ value }) => {
          this.$message({
            type: 'success',
            message: '你的邮箱是: ' + value
          });
        }).catch(() => {
          this.$message({
            type: 'info',
            message: '取消输入'
          });       
        });
      }
  }
};
</script>