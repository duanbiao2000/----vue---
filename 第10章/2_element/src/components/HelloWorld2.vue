<template>
    <div>  
        <template v-for="(tag,index) in tags" :key="tag">
        <el-tag :closable="true" @close="closeTag(index)">{{tag}}</el-tag>
        <span style="padding:10px"></span>
        </template>
        <el-input style="width: 90px"
                v-if="show"
                v-model="inputValue"
                @keyup.enter="handleInputConfirm"
                @blur="handleInputConfirm"
                size="small">
        </el-input>
        <el-button size="small" v-else @click="showInput">新建标签 +</el-button>
    </div>
    <div>
        <el-check-tag :checked="true">足球</el-check-tag>
        <el-check-tag :checked="false">篮球</el-check-tag>
    </div>
</template>
<script>
export default {
    data() {
    return {
        tags:["男装","女装","帽子","鞋子"],
        show:false,
        inputValue:""
    }
    },
    methods:{
    closeTag(index) {
        this.tags.splice(index, 1);
    },
    showInput() {
        this.show = true
    },
    handleInputConfirm(){
        let inputValue = this.inputValue;
        if (inputValue) {
        this.tags.push(inputValue);
        }
        this.show = false;
        this.inputValue = '';
    }
    }
}
</script>