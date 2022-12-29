<template>
  <div class="app-container">
    <!-- 输入表单 -->
    <el-form label-width="120px">
      <el-form-item label="借款额度">
        <el-input-number v-model="integralGrade.borrowAmount" :min="0" />
      </el-form-item>
      <el-form-item label="积分区间开始">
        <el-input-number v-model="integralGrade.integralStart" :min="0" />
      </el-form-item>
      <el-form-item label="积分区间结束">
        <el-input-number v-model="integralGrade.integralEnd" :min="0" />
      </el-form-item>
      <el-form-item>
        <el-button
          :disabled="saveBtnDisabled"
          type="primary"
          @click="saveOrUpdate()"
        >
          保存
        </el-button>
      </el-form-item>
    </el-form>
  </div>
</template>

<script>
import integralGradeApi from '@/api/core/intergral-grade'
export default {
  data() {
    return {
      saveBtnDisabled: false, //防止表单重复提交
      integralGrade: {}, //积分等级对象
    }
  },
  methods: {
    saveOrUpdate() {
      //调用新增
      this.saveBtnDisabled = true
      this.saveData()
      //调用更新
    },
    saveData() {
      integralGradeApi.save(this.integralGrade).then((response) => {
        this.$message({
          type: 'success',
          message: response.message,
        })
        this.$router.push('/core/integral-grade/list')
      })
    },
    updateData() {},
  },
}
</script>

<style scoped></style>
