<template>
  <div class="login_div">
    <el-card class="box-card">
      <el-form status-icon ref="loginform" :model="loginform" :rules="loginRules">
        <img src="../assets/images/logo_index.png" alt />
        <el-form-item prop="mobile">
          <el-input v-model="loginform.mobile" placeholder="手机号"></el-input>
        </el-form-item>
        <el-form-item class="abc" prop="code">
          <el-input v-model="loginform.code" id="yzm" placeholder="验证码"></el-input>
          <el-button id="aa">发送验证码</el-button>
        </el-form-item>
        <el-form-item>
          <el-checkbox v-model="checked"></el-checkbox>
          <span>
            我已阅读并同意
            <a href>用户协议</a>与
            <a href>隐私条款</a>
          </span>
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="logindl">登录</el-button>
        </el-form-item>
      </el-form>
    </el-card>
  </div>
</template>

<script>
export default {
  data () {
    const checkmobile1 = (rule, value, callback) => {
      if (/^1[3-9]\d{9}$/.test(value)) {
        callback()
      } else {
        callback(new Error('填入11位手机号'))
      }
    }
    const checkmobile2 = (rele, value, callback) => {
      if (/^\d{6}$/.test(value)) {
        callback()
      } else {
        callback(new Error('填入5位验证码'))
      }
    }
    return {
      checked: true,
      loginform: {
        mobile: '18612310417',
        code: '246810'
      },
      loginRules: {
        mobile: [
          { required: true, message: '手机号必填', trigger: 'blur' },
          { validator: checkmobile1, trigger: 'blur' }
        ],
        code: [
          { required: true, message: '验证码必填', trigger: 'blur' },
          { validator: checkmobile2, trigger: 'blur' }
        ]
      }
    }
  },
  methods: {
    logindl () {
      this.$refs.loginform.validate(valid => {
        if (valid) {
          this.axios.post(
            'http://ttapi.research.itcast.cn/mp/v1_0/authorizations',
            this.loginform
          )
            .then(res => {
              const data = res.data
              console.log(data)
              this.$router.push('/home')
            })
        }
      })
    }
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
}
.login_div {
  position: absolute;
  width: 100%;
  height: 100%;
  background-image: url("../assets/images/login_bg.jpg");
  background: no-repeat cover;
}
.text {
  font-size: 14px;
}

.item {
  padding: 18px 0;
}

.box-card {
  width: 480px;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
}
.box-card img {
  display: block;
  margin: 0 auto;
}
#yzm {
  float: left;
  margin-top: 5px;
  display: inline-block;
  width: 100%;
}
#aa {
  float: right;
  display: inline-block;
  width: 30%;
  margin-top: 5px;
}
.el-checkbox {
  margin-right: 2px;
}
.el-button--primary {
  width: 100%;
}

.el-form-item.abc .el-form-item__content .el-input {
  width: 70%;
}
</style>
