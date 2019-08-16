<template>
  <div>
    <div class="crumbs">
      <el-row>
        <el-col :span="22">
          <el-breadcrumb separator="/">
            <el-breadcrumb-item>
              <i class="el-icon-lx-calendar"></i> lottery
            </el-breadcrumb-item>
            <el-breadcrumb-item>奖品管理</el-breadcrumb-item>
          </el-breadcrumb>
        </el-col>
        <el-col :span="2">
          <router-link :to="{path:'/addPrize',query: {name: '新增奖品'}}">
            <el-button type="primary" icon="el-icon-plus">新增奖品</el-button>
          </router-link>
        </el-col>
      </el-row>
    </div>
    <div class="container ">
     <div class="sm-layout-left-center-wrap ">
        <el-card  v-for="item in prizeList" shadow="hover" style="width:200px;" class="sm-margin-left-1rem sm-margin-top-1rem">
          <img :src ="item.imgUrl" class="image" />
          <div style="padding: 14px;">
            <span>{{item.name}}</span>
            <div class="bottom clearfix">
              <div class="price">{{item.price}}</div>
              <el-button type="text" class="button"  @click="edit(item)" >修改</el-button>
              <el-button type="text" class="button">删除</el-button>
            </div>
          </div>
        </el-card>
     </div>
      <div class="pagination sm-margin-top-1rem">
        <el-pagination
          background
          @current-change="handleCurrentChange"
          layout="prev, pager, next"
          :total="1000"
        ></el-pagination>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
          prizeList: [{
            price: '21$',
            name: '好吃的汉堡',
            imgUrl: 'http://47.108.76.124/upload/20190802/170e354cd0ed4982ab2950a2da44fd8b.jpg'
          }, {
            price: '21$',
            name: '好吃的汉堡',
            imgUrl: 'http://47.108.76.124/upload/20190802/170e354cd0ed4982ab2950a2da44fd8b.jpg'
          }, {
            price: '21$',
            name: '好吃的汉堡',
            imgUrl: 'http://47.108.76.124/upload/20190802/170e354cd0ed4982ab2950a2da44fd8b.jpg'
          }, {
            price: '21$',
            name: '好吃的汉堡',
            imgUrl: 'http://47.108.76.124/upload/20190802/170e354cd0ed4982ab2950a2da44fd8b.jpg'
          },
          {
            price: '21$',
            name: '好吃的汉堡',
            imgUrl: 'http://47.108.76.124/upload/20190802/170e354cd0ed4982ab2950a2da44fd8b.jpg'
          },
          {
            price: '21$',
            name: '好吃的汉堡',
            imgUrl: 'http://47.108.76.124/upload/20190802/170e354cd0ed4982ab2950a2da44fd8b.jpg'
          },
          {
            price: '21$',
            name: '好吃的汉堡',
            imgUrl: 'http://47.108.76.124/upload/20190802/170e354cd0ed4982ab2950a2da44fd8b.jpg'
          },
          {
            price: '21$',
            name: '好吃的汉堡',
            imgUrl: 'http://47.108.76.124/upload/20190802/170e354cd0ed4982ab2950a2da44fd8b.jpg'
          },
            {
            price: '21$',
            name: '好吃的汉堡',
            imgUrl: 'http://47.108.76.124/upload/20190802/170e354cd0ed4982ab2950a2da44fd8b.jpg'
          }]
    };
  },

  edit(i){
   console.log(i.name);
  }
}
</script>

<style scoped>
.price {
    font-size: 13px;
    color: #999;
  }
  
  .bottom {
    margin-top: 13px;
    line-height: 12px;
  }

  .button {
    padding: 0;
    float: right;
  }

  .image {
    width: 100%;
    display: block;
  }

  .clearfix:before,
  .clearfix:after {
      display: table;
      content: "";
  }
  
  .clearfix:after {
      clear: both
  }
</style>
