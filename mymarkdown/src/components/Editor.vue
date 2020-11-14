<template>
    <div class="editor">
        <h1>エディター画面</h1>
        <span>{{user.displayName}}</span>
        <button @click="logout">ログアウト</button>
        <div class="editorWrapper">
            <div class="memoList" v-for"(memo, index) in memos" :key=index"@click=selectMemo(index)" :data-selected="index == selectedIndex">
                <p class="memoTitle">{{ displayTitle(memo.markdown) }}</p>
            </div>
            <button class="addMemoBtn" @click="addMemo">メモの追加</button>
            <textarea class="markdown" v-model="markdown"></textarea>
            <div class="preview" v-html="preview()"></div>
        </div>
    </div>
</template>
<script>
import marked from "marked";
export default {
    name: "editor",
    props:["user"],
    data() {
        return {
            memos: [
                {
                    markdown: ""
                }
            ],
            selectedIndex: 0
        };
    },
    methods: {
        logout: function() {
            firebase.auth().signOut();
        },
        preview: function() {
            return marked(this.markdown);
        }
    }
};
</script>
<style lang="scss" scoped>
.editorWrapper { 
    display: flex;
}
.markdown {
    width: 50%;
    height: 500px;
}
.preview { 
    width: 50%;
    text-align: left;
}
</style>