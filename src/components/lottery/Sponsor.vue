<template>
  <div>
    <div class="crumbs">
      <el-breadcrumb separator="/">
        <el-breadcrumb-item>
          <i class="el-icon-lx-calendar"></i> lottery
        </el-breadcrumb-item>
        <el-breadcrumb-item>赞助商</el-breadcrumb-item>
      </el-breadcrumb>
    </div>
    <div class="container">
      <el-row>
        <div>
          <el-button @click="addSponsor" type="primary" round>
            <i class="el-icon-lx-add"></i> 新增
          </el-button>
          <el-divider direction="vertical"></el-divider>
          <el-button type="success" round>
            <i class="el-icon-lx-search"></i> 个人
          </el-button>
          <el-divider direction="vertical"></el-divider>
          <el-button type="info" round>
            <i class="el-icon-lx-search"></i> 商户
          </el-button>
        </div>
      </el-row>

      <el-divider content-position="left">赞助商</el-divider>

      <el-row class="ms-layout-start-horizontal">
        <el-card v-for="item in sponsorList" :key="item" class="margin-left-20" shadow="hover">
          <div class="width-130-height-156 ms-layout-wrap-vertical">
            <div
              class="ms-layout-center-wrap-horizontal"
              style="width:100%;height:50%"
            >大苏打撒旦{{item}}</div>
            <div class="ms-layout-center-wrap-horizontal" style="width:100%;height:25%;">
              <el-tooltip :content="value" placement="top">
                <el-switch
                  v-model="value"
                  inactive-color="#C0CCDA"
                  active-color="#409EFF"
                  active-value="已开启"
                  inactive-value="已关闭"
                ></el-switch>
              </el-tooltip>
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

    <!-- 赞助商详情 -->
    <el-drawer title="商户详情" :visible.sync="drawer" :direction="direction">
      <div class="debug ms-layout-wrap-vertical" style="width:100%;height:100%"></div>
    </el-drawer>
    <!-- 新增赞助商 -->
    <el-drawer title="新增赞助商" :visible.sync="addDrawer" :direction="direction">
      <div class="debug ms-layout-wrap-vertical" style="width:100%;height:100%"></div>
    </el-drawer>
  </div>
</template>
<style>
.debug {
  border: 1px solid red;
}

.ms-layout-center-wrap-horizontal {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;

  justify-content: center;
  align-items: center;
}
.width-130-height-156 {
  width: 130px;
  height: 156px;
}
.ms-layout-start-horizontal {
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;

  justify-content: start;
  align-items: center;
}
.ms-layout-wrap-vertical {
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;

  justify-content: space-around;
  align-items: center;
}
.margin-bottom-20 {
  margin-bottom: 20px;
}
.margin-left-20 {
  margin-left: 20px;
}
.el-row {
  margin-bottom: 20px;
  &:last-child {
    margin-bottom: 0;
  }
}
.el-col {
  border-radius: 4px;
}
.bg-purple-dark {
  background: #99a9bf;
}
.bg-purple {
  background: #d3dce6;
}
.bg-purple-light {
  background: #e5e9f2;
}
.grid-content {
  border-radius: 4px;
  min-height: 36px;
}
.row-bg {
  padding: 10px 0;
  background-color: #f9fafc;
}
</style>

<script>
export default {
  name: "sponsor",
  data() {
    return {
      sponsorList: [1, 2, 3, 4, 5, 6, 7, 8],
      value: "已开启",
      drawer: false,
      addDrawer: false,
      direction: "rtl"
    };
  },
  methods: {
    addSponsor: function() {
        this.$data.addDrawer = true;
        console.log(this.addDrawer)
    }
  }
};
</script>