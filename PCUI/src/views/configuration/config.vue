<template>
  <div class="app-container calendar-list-container">
  <!--<el-row>-->
    <!--<el-button type="primary">新增</el-button>-->
    <!--<el-button type="success">刪除</el-button>-->
  <!--</el-row>-->
  <div class="filter-container">
    <el-button class="filter-item" type="primary" v-waves @click="dialogFormVisible = true">新增</el-button>
  </div>
  <el-table
          :data="tableData"
          border
          style="width: 100%">
    <el-table-column
            prop="prot"
            label="端口"
            width="120">
    </el-table-column>
    <el-table-column
            prop="name"
            label="用户名"
            width="120">
    </el-table-column>
    <el-table-column
            prop="password"
            label="密码"
            width="120">
    </el-table-column>
    <el-table-column
            prop="address"
            label="地址"
            width="600">
    </el-table-column>
    <el-table-column
            fixed="right"
            label="操作"
            width="160">
      <template slot-scope="scope">
        <el-button @click="handleClick1(scope.row)" type="text" size="small">编辑</el-button>
        <el-button @click="handleClick(scope.row)" type="text" size="small">查看</el-button>
        <el-button @click="handleDelete(scope.row)" type="text" size="small">删除</el-button>
      </template>
    </el-table-column>
  </el-table>

    <el-dialog title="新增" :visible.sync="dialogFormVisible">
      <el-form :model="form" status-icon  ref="form" label-width="100px" class="demo-ruleForm">
        <el-form-item label="地址" :label-width="formLabelWidth">
          <el-input v-model="form.address" auto-complete="off"></el-input>
        </el-form-item>
        <el-form-item label="端口" :label-width="formLabelWidth">
          <el-input v-model="form.prot" auto-complete="off"></el-input>
        </el-form-item>
        <el-form-item label="用户名" :label-width="formLabelWidth">
          <el-input v-model="form.name" auto-complete="off"></el-input>
        </el-form-item>
        <el-form-item label="密码" :label-width="formLabelWidth">
          <el-input v-model="form.password" auto-complete="off"></el-input>
        </el-form-item>
      </el-form>
      <div slot="footer" class="dialog-footer">
        <el-button type="primary" @click="submitForm('form')">确 定</el-button>
        <el-button @click="resetForm('ruleForm2')">取 消</el-button>
      </div>
    </el-dialog>
  </div>
</template>


<script>


  export default {
  name: 'config',
    methods: {
      handleClick(row) {
        this.dialogFormVisible=true;
        this.form = Object.assign({}, row)
        console.log(row);
        console.log(this.form);

      },
      handleClick1(row) {
        this.dialogFormVisible=true;
      },
      handleDelete(row){
        this.tableData.pop(row);
      },
      submitForm(form) {
        this.$refs[form].validate((valid) => {
          if (valid) {
            alert('submit!');
            this.dialogFormVisible=false;
          } else {
            console.log('error submit!!');
            return false;
          }
        });
      },
    },

    data() {
      return {
        tableData: [{
          name: '王小虎',
          password: "123456",
          address: '上海市普陀区金沙江路 1518 弄',
          prot: 200333
        }, {
          name: '王小虎',
          password: "123456",
          address: '上海市普陀区金沙江路 1518 弄',
          prot: 200333
        }, {
          name: '王小虎',
          password: "123456",
          address: '上海市普陀区金沙江路 1518 弄',
          prot: 200333
        }, {
          name: '王小虎',
          password: "123456",
          address: '上海市普陀区金沙江路 1518 弄',
          prot: 200333
        }],
        dialogFormVisible: false,
        form: {
          name: '',
          prot: '',
          adree: '',
          password: '',
          region: '',
          date1: '',
          date2: '',
          delivery: false,
          type: [],
          resource: '',
          desc: ''
        },
        formLabelWidth: '120px'
      };
    }
}
</script>

<style >

</style>

