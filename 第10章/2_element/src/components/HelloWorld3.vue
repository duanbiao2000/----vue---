<template>
    <div class="hello">
      <h1>{{ msg }}</h1>
      <el-empty description="设置空态图的描述文案" :image-size="400"></el-empty>
    </div>
    <div class="hello">
        <el-empty>
            <!-- image具名插槽用来替换默认的图片部分 -->
            <template v-slot:image>
                <div>这里是自定义图片位置</div>
            </template>
            <!-- description具名插槽用来替换默认的描述部分 -->
            <template v-slot:description>
                <h3>自定义描述内容</h3>
            </template>
            <!-- 默认的插槽用来在空态图的尾部追加内容 -->
            <el-button>看看其他内容</el-button>
        </el-empty>
    </div>
    <div class="hello">
        <el-skeleton :rows="10" :animated="true"></el-skeleton>
    </div>
    <div class="hello">
        <el-skeleton :animated="true">
        <template #template>
            <!-- 定义标题骨架 -->
            <el-skeleton-item variant="h1" style="width: 100px; height: 30px; padding:0"/>
            <!-- 定义图片骨架 -->
            <el-skeleton-item variant="image" style="width: 240px; height: 240px; padding:0" />
            <!-- 定义段落骨架 -->
            <el-skeleton-item variant="p" style="width: 30%; padding:0; margin-top:20px"/>
            <el-skeleton-item variant="p" style="width: 90%; padding:0"/>
            <el-skeleton-item variant="p" style="width: 90%; padding:0"/>
        </template>
        </el-skeleton>
    </div>
    <div class="hello">
        <el-skeleton :rows="1" :animated="true" :loading="loading">
            <h1>这里是真实的页面元素</h1>
            <p>{{msg}}</p>
        </el-skeleton>
    </div>
  </template>
  
  <script>
  export default {
    name: 'HelloWorld',
    data() {
        return {
        msg:"",
        loading:true
        }
    },
    // 模拟页面加载3秒后请求到数据
    mounted(){
        setTimeout(this.getData, 3000);
    },
    methods:{
        getData() {
            this.msg = "这里是请求到的数据"
            this.loading = false
        }
    }
  }
  </script>
  
  <style>
    .hello {
      margin-top: 40px;
      text-align: left;
    }
  </style>