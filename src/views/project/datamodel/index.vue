<template>
  <div class="app-container">
    <div class="filter-container">
      <el-form :inline="true" :model="formObj" class="demo-form-inline">
        <el-form-item label="工程名称">
          <el-input v-model="formObj.projectName" placeholder=""/>
        </el-form-item>
        <el-form-item label="设备类别">
          <el-select v-model="formObj.deviceType" placeholder="">
            <el-option label="工程机械" value="project"/>
            <el-option label="矿山机械" value="mining"/>
            <el-option label="冶金机械" value="metallurgy"/>
          </el-select>
        </el-form-item>
        <el-form-item label="特殊资源" prop="resource">
          <el-radio-group v-model="formObj.isRunning">
            <el-radio label="启用"/>
            <el-radio label="停用"/>
          </el-radio-group>
        </el-form-item>
        <el-form-item>
          <el-button type="primary" @click="onSubmit">查询</el-button>
        </el-form-item>
      </el-form>
    </div>

    <el-table :data="tableData" border>
      <el-table-column prop="modelId" label="模板id"/>
      <el-table-column prop="modelName" label="模板名称"/>
      <el-table-column prop="projectName" label="所属工程"/>
      <el-table-column prop="deviceType" label="设备类别"/>
      <el-table-column prop="status" label="状态"/>
      <el-table-column prop="createTime" label="创建时间"/>
      <el-table-column label="操作">
        <template slot-scope="scope">
          <el-button type="text" size="small" @click="handleClick(scope.row)">查看</el-button>
          <el-button type="text" size="small">编辑</el-button>
        </template>
      </el-table-column>
    </el-table>

    <div class="filter-container">
      <el-pagination
        :current-page="currentPage"
        :page-sizes="[10, 20, 30, 40]"
        :page-size="10"
        :total="400"
        layout="total, sizes, prev, pager, next, jumper"
        @size-change="handleSizeChange"
        @current-change="handleCurrentChange"/>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ComplexTable',
  data() {
    return {
      currentPage: 1,
      formObj: {
        projectName: '',
        deviceType: '',
        isRunning: '启用'
      },
      tableData: [{
        modelId: 8823467231,
        modelName: '球磨机模板',
        projectName: '通用模板',
        deviceType: '矿山机械',
        status: '启用',
        createTime: '2018-03-22 09:33:05'
      },
      {
        modelId: 8823467231,
        modelName: '球磨机模板',
        projectName: '通用模板',
        deviceType: '矿山机械',
        status: '启用',
        createTime: '2018-03-22 09:33:05'
      },
      {
        modelId: 8823467231,
        modelName: '球磨机模板',
        projectName: '通用模板',
        deviceType: '矿山机械',
        status: '启用',
        createTime: '2018-03-22 09:33:05'
      }]
    }
  },
  methods: {
    onSubmit() {
      console.log('submit!')
    },
    handleClick(row) {
      console.log(row)
    },
    handleSizeChange(val) {
      console.log(`每页 ${val} 条`)
    },
    handleCurrentChange(val) {
      console.log(`当前页: ${val}`)
    }
  }
}
</script>
