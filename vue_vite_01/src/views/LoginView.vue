<template>
    <el-form
      ref="ruleFormRef"
      :model="ruleForm"
      status-icon
      :rules="rules"
      label-width="120px"
      class="demo-ruleForm"
    >
      <el-form-item label="账号" prop="username">
        <el-input v-model="ruleForm.username" autocomplete="off" />
      </el-form-item>
      <el-form-item label="密码" prop="password">
        <el-input
          v-model="ruleForm.password"
          type="password"
          autocomplete="off"
        />
      </el-form-item>
     
      <!-- <el-form-item>
        <el-button type="primary" @click="submitForm(ruleFormRef)"
          >Login</el-button
        >
        <el-button @click="resetForm(ruleFormRef)">Reset</el-button>
      </el-form-item> -->
    </el-form>
</template>
  

<script lang="ts">
import { defineComponent, reactive, toRefs } from 'vue'

export default defineComponent({
    setup () {
            const data = reactive({
                ruleForm: {
                    username: '',
                    password: ''
                },
                rules: {
                    username: [
                        { required: true, message: 'Please input Activity name', trigger: 'blur' },
                        { min: 3, max: 5, message: 'Length should be 3 to 5', trigger: 'blur' },
                    ],
                    password: [
                        { required: true, message: 'Please input Activity password', trigger: 'blur' },
                        { min: 8, max: 10, message: 'Length should be 8 to 10', trigger: 'blur' },
                    ]
                }

            })
        return {...toRefs(data)}
    }
})
</script>

<!-- @import "@/style/globalMixin.scss";
 -->
<style lang='scss' scoped>

    .login-box{
        width: 10%;
        height: 10%;
        background: url('@/assets/1.heic');
        padding: 1px;
        .demo-ruleForm {
            width: 500px;
            margin: 200px auto;
            background-color: aquamarine;
        }
    }
</style>
