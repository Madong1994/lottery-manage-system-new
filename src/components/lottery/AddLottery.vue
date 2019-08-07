<template>
  <div>
    <div class="crumbs">
      <el-breadcrumb separator="/">
        <el-breadcrumb-item>
          <i class="el-icon-lx-calendar"></i> lottery
        </el-breadcrumb-item>
        <el-breadcrumb-item>新增</el-breadcrumb-item>
      </el-breadcrumb>
    </div>
    <div class="container">
      <div class="form-box">
        <el-form ref="form" :model="form" label-width="80px">
          <el-divider content-position="left">赞助商</el-divider>
          <div class="width-250-height-156-px sm-layout-left-center">
            <div class="sm-layout-side-vertical" style="height:60%;width:40%">
              <div class="sm-layout-center-horizontal-with-wrap" style="width: 100%;height:50%">
                <el-button @click="addSponsor" type="success" round>
                  <i class="el-icon-lx-searchlist"></i> 个人
                </el-button>
              </div>
              <div class="sm-layout-center-horizontal-with-wrap" style="width: 100%;height:50%">
                <el-button @click="addSponsor" type="info" round>
                  <i class="el-icon-lx-searchlist"></i> 商户
                </el-button>
              </div>
            </div>
            <div class="ms-layout-wrap-vertical" style="height:100%;width:40%">
              <el-card class="margin-left-20" shadow="hover">
                <div class="width-80-height-100-px ms-layout-wrap-vertical"></div>
              </el-card>
            </div>
          </div>

          <el-divider content-position="left">奖品设置</el-divider>
          <el-form-item label="日期时间">
            <el-col :span="11">
              <el-date-picker
                type="date"
                placeholder="选择日期"
                v-model="form.date1"
                style="width: 100%;"
              ></el-date-picker>
            </el-col>
            <el-col class="line" :span="2">-</el-col>
            <el-col :span="11">
              <el-time-picker placeholder="选择时间" v-model="form.date2" style="width: 100%;"></el-time-picker>
            </el-col>
          </el-form-item>
          <el-form-item label="城市级联">
            <el-cascader :options="options" v-model="form.options"></el-cascader>
          </el-form-item>
          <el-form-item label="选择开关">
            <el-switch v-model="form.delivery"></el-switch>
          </el-form-item>
          <el-form-item label="多选框">
            <el-checkbox-group v-model="form.type">
              <el-checkbox label="步步高" name="type"></el-checkbox>
              <el-checkbox label="小天才" name="type"></el-checkbox>
              <el-checkbox label="imoo" name="type"></el-checkbox>
            </el-checkbox-group>
          </el-form-item>
          <el-form-item label="单选框">
            <el-radio-group v-model="form.resource">
              <el-radio label="步步高"></el-radio>
              <el-radio label="小天才"></el-radio>
              <el-radio label="imoo"></el-radio>
            </el-radio-group>
          </el-form-item>
          <el-divider content-position="left">广告设置</el-divider>
          <el-form-item label="文本框">
            <el-input type="textarea" rows="5" v-model="form.desc"></el-input>
          </el-form-item>
          <el-form-item>
            <el-button type="primary" @click="onSubmit">表单提交</el-button>
            <el-button>取消</el-button>
          </el-form-item>
        </el-form>
      </div>
    </div>
  </div>
</template>
<style>
.width-80-height-100-px {
  width: 80px;
  height: 100px;
}
</style>

<script>
export default {
  name: "baseform",
  data: function() {
    return {
      options: [
        {
          value: "guangdong",
          label: "广东省",
          children: [
            {
              value: "guangzhou",
              label: "广州市",
              children: [
                {
                  value: "tianhe",
                  label: "天河区"
                },
                {
                  value: "haizhu",
                  label: "海珠区"
                }
              ]
            },
            {
              value: "dongguan",
              label: "东莞市",
              children: [
                {
                  value: "changan",
                  label: "长安镇"
                },
                {
                  value: "humen",
                  label: "虎门镇"
                }
              ]
            }
          ]
        },
        {
          value: "hunan",
          label: "湖南省",
          children: [
            {
              value: "changsha",
              label: "长沙市",
              children: [
                {
                  value: "yuelu",
                  label: "岳麓区"
                }
              ]
            }
          ]
        }
      ],
      form: {
        name: "",
        region: "",
        date1: "",
        date2: "",
        delivery: true,
        type: ["步步高"],
        resource: "小天才",
        desc: "",
        options: []
      }
    };
  },
  methods: {
    onSubmit() {
      this.$message.success("提交成功！");
    }
  }
};
</script>