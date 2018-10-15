<template>
  <div class="app-container">
    <el-form ref="form" :model="form" label-width="120px">
      <el-form-item label="请假人">
        <el-input v-model="form.name" />
      </el-form-item>
      <el-form-item label="部门">
        <el-input v-model="form.name" />
      </el-form-item>
      <el-form-item label="请假类型">
        <el-select v-model="form.region" placeholder="请选择请假类型">
          <el-option label="Zone one" value="shanghai" />
          <el-option label="Zone two" value="beijing" />
        </el-select>
      </el-form-item>
      <div>
        <span>
          <el-form-item label="开始时间">
            <el-col :span="6">
              <el-date-picker v-model="form.date1" type="date" placeholder="选择时间" style="width: 100%;" />
            </el-col>
            <el-col :span="2" class="line">-</el-col>
            <el-col :span="6">
              <el-time-picker v-model="form.date2" type="fixed-time" placeholder="选择日期" style="width: 100%;" />
            </el-col>
          </el-form-item>
        </span>
        <!-- <div>至</div> -->
        <span>
          <el-form-item label = "结束时间">
            <el-col :span="6">
              <el-date-picker v-model="form.date1" type="date" placeholder="选择时间" style="width: 100%;" />
            </el-col>
            <el-col :span="2" class="line">-</el-col>
            <el-col :span="6">
              <el-time-picker v-model="form.date2" type="fixed-time" placeholder="选择日期" style="width: 100%;" />
            </el-col>
          </el-form-item>
        </span>
      </div>
      <el-form-item label="请假事由">
        <el-input v-model="form.desc" type="textarea" />
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
  data() {
    return {
      form: {
        name: "",
        region: "",
        date1: "",
        date2: "",
        delivery: false,
        type: [],
        resource: "",
        desc: ""
      }
    };
  },
  methods: {
    onSubmit() {
      this.$message("submit!");
    },
    onCancel() {
      this.$message({
        message: "cancel!",
        type: "warning"
      });
    }
  }
};
</script>

<style scoped>
.line {
  text-align: center;
}
</style>

