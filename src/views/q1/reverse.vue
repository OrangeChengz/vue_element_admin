<template>
  <div class="container">
    <div class="input">
      <el-card class="box-card">
        <template #header>
          <div class="card-header">
            <span>问题输入</span>
          </div>
        </template>
        <el-form :model="form" label-width="120px">
          <el-row>
            <el-col :span="4">
              <el-form-item>
                <div class="grid-content bg-purple">区域一</div>
              </el-form-item>
            </el-col>

            <el-col :span="6">
              <el-form-item label="区域形状">
                <el-select
                  v-model="form.shape1"
                  class="el-selector"
                  placeholder="请选择"
                >
                  <el-option
                    v-for="item in area_options"
                    :key="item.value"
                    :label="item.label"
                    :value="item.value"
                  />
                </el-select>
              </el-form-item>
            </el-col>

            <el-col :span="6">
              <el-form-item label="形状参数">
                <el-input v-model="form.para1" />
              </el-form-item>
            </el-col>

            <el-col :span="6">
              <el-form-item label="投送数量">
                <el-input v-model="form.n1_1" />
              </el-form-item>
            </el-col>
          </el-row>

          <el-row>
            <el-col :span="4">
              <el-form-item>
                <div class="grid-content bg-purple">区域二</div>
              </el-form-item>
            </el-col>

            <el-col :span="6">
              <el-form-item label="区域形状">
                <el-select
                  v-model="form.shape2"
                  class="el-selector"
                  placeholder="请选择"
                >
                  <el-option
                    v-for="item in area_options"
                    :key="item.value"
                    :label="item.label"
                    :value="item.value"
                  />
                </el-select>
              </el-form-item>
            </el-col>

            <el-col :span="6">
              <el-form-item label="形状参数">
                <el-input v-model="form.para2" />
              </el-form-item>
            </el-col>

            <el-col :span="6">
              <el-form-item label="投送数量">
                <el-input v-model="form.n2_1" />
              </el-form-item>
            </el-col>
          </el-row>

          <el-row>
            <el-col :span="4">
              <el-form-item>
                <div class="grid-content bg-purple">区域三</div>
              </el-form-item>
            </el-col>

            <el-col :span="6">
              <el-form-item label="区域形状">
                <el-select
                  v-model="form.shape3"
                  class="el-selector"
                  placeholder="请选择"
                >
                  <el-option
                    v-for="item in area_options"
                    :key="item.value"
                    :label="item.label"
                    :value="item.value"
                  />
                </el-select>
              </el-form-item>
            </el-col>

            <el-col :span="6">
              <el-form-item label="形状参数">
                <el-input v-model="form.para3" />
              </el-form-item>
            </el-col>

            <el-col :span="6">
              <el-form-item label="投送数量">
                <el-input v-model="form.n3_1" />
              </el-form-item>
            </el-col>
          </el-row>

          <el-row>
            <el-col :span="4">
              <el-form-item>
                <div class="grid-content bg-purple">物资包参数</div>
              </el-form-item>
            </el-col>

            <el-col :span="6">
              <el-form-item label="误差">
                <el-input v-model="form.p1_err" />
              </el-form-item>
            </el-col>

            <el-col :span="6">
              <el-form-item label="最小置信度">
                <el-input v-model="form.minC" />
              </el-form-item>
            </el-col>
          </el-row>

          <el-row>
            <el-col :span="4">
              <el-form-item>
                <div class="grid-content bg-purple">模型优化</div>
              </el-form-item>
            </el-col>

            <el-col :span="6">
              <el-form-item label="优化等级">
                <el-select
                  v-model="form.level"
                  class="el-selector"
                  placeholder="请选择"
                >
                  <el-option
                    v-for="item in options"
                    :key="item.value"
                    :label="item.label"
                    :value="item.value"
                  />
                </el-select>
              </el-form-item>
            </el-col>
          </el-row>

          <el-form-item>
            <el-button type="primary" plain @click="onSubmit">提交</el-button>
          </el-form-item>
        </el-form>
      </el-card>
    </div>
    <div class="output">
      <el-card class="box-card">
        <template #header>
          <div class="card-header">
            <span>计算结果</span>
          </div>
        </template>
        <el-form :model="form_output" label-width="120px">
          <el-row>
            <el-col :span="4">
              <el-form-item>
                <div class="grid-content bg-purple">区域一</div>
              </el-form-item>
            </el-col>

            <el-col :span="6">
              <el-form-item label="投掷点坐标">
                <el-input v-model="form_output.loc1" />
              </el-form-item>
            </el-col>
          </el-row>
          <el-row>
            <el-col :span="4">
              <el-form-item>
                <div class="grid-content bg-purple">区域二</div>
              </el-form-item>
            </el-col>

            <el-col :span="6">
              <el-form-item label="投掷点坐标">
                <el-input v-model="form_output.loc2" />
              </el-form-item>
            </el-col>
          </el-row>

          <el-row>
            <el-col :span="4">
              <el-form-item>
                <div class="grid-content bg-purple">区域三</div>
              </el-form-item>
            </el-col>

            <el-col :span="6">
              <el-form-item label="投掷点坐标">
                <el-input v-model="form_output.loc3" />
              </el-form-item>
            </el-col>
          </el-row>
        </el-form>
      </el-card>
    </div>
    <div class="picture">
      <el-card class="box-card">
        <template #header>
          <div class="card-header">
            <span>图片</span>
          </div>
        </template>
        <div id="mychart" class="chart" />
      </el-card>
    </div>
  </div>
</template>

<script>
import * as echarts from 'echarts'

export default {
  name: 'Q1',
  data() {
    // 用到的数据在data里声明
    return {
      form: {
        shape1: '1',
        para1: '[[6, 347], 50]',
        n1_1: '2',
        shape2: '',
        para2: '',
        n2_1: '',
        shape3: '',
        para3: '',
        n3_1: '',
        p1_err: '',
        minC: '',
        level: '3'
      },
      form_output: {
        c1: '',
        c2: '',
        c3: ''
      },
      area_options: [
        {
          value: '0',
          label: '无'
        },
        {
          value: '1',
          label: '圆形'
        },
        {
          value: '2',
          label: '矩形'
        },
        {
          value: '3',
          label: '多边形'
        }
      ],
      options: [
        {
          value: '1',
          label: '1级'
        },
        {
          value: '2',
          label: '2级'
        },
        {
          value: '3',
          label: '3级'
        },
        {
          value: '4',
          label: '4级'
        },
        {
          value: '5',
          label: '5级'
        }
      ],
      formLabelAlign: {
        name: '',
        region: '',
        type: ''
      }
    }
  },
  mounted() {
    this.chartInit()
  },

  methods: {
    chartInit() {
      // 基于刚刚准备好的 DOM 容器，初始化 EChart 实例
      var myChart = echarts.init(document.getElementById('mychart'))
      // 绘制图表
      myChart.setOption({
        title: { text: '示意图' },
        tooltip: {},
        xAxis: {
          min: -10,
          max: 500
        },
        yAxis: {},
        dataZoom: [
          {
            // 这个dataZoom组件，默认控制x轴。
            type: 'slider', // 这个 dataZoom 组件是 slider 型 dataZoom 组件
            start: 10, // 左边在 10% 的位置。
            end: 60 // 右边在 60% 的位置。
          },
          {
            // 这个dataZoom组件，也控制x轴。
            type: 'inside', // 这个 dataZoom 组件是 inside 型 dataZoom 组件
            start: 10, // 左边在 10% 的位置。
            end: 60 // 右边在 60% 的位置。
          }
        ],
        series: [
          {
            type: 'line',
            name: '1',
            data: [
              [1, 100],
              [5, 110],
              [10, 150]
            ]
          },
          {
            type: 'line',
            name: '2',
            data: [
              [20, 100],
              [30, 110],
              [40, 150]
            ]
          }
        ]
      })
    },
    onSubmit() {
      console.log('onsubmit')
      this.refreshData('test')
    },

    refreshData(data) {
      console.log(data)
      var myChart = echarts.getInstanceByDom(
        document.getElementById('mychart')
      )
      var option = myChart.getOption()
      // option.series[0].data=data
      option.series[0].data = [
        [50, 100],
        [60, 110],
        [70, 150]
      ]
      myChart.setOption(option)
    }
  }
}
</script>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  flex-direction: column;
  padding: 2%;
}

.input,
.output,
.picture {
  margin: 1%;
}
.el-selector {
  width: 100%;
}
.card-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.grid-content {
  font-size: 16px;
}

.chart {
  height: 600px;
  width: 100%;
}
</style>
