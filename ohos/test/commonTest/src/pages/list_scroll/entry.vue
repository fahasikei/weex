<template>
    <div>
        <list class="list-wrap" v-grouping-child-elements="50" offset-accuracy="20" loadmoreoffset="800" @scroll="onScroll">
            <div>
                <cell class="list-cell" v-for="(item, index) in 10000" :key="item">
                    <text class="item">{{ lists[index % lists.length] }}</text>
                </cell>
            </div>
        </list>
        <div v-if="showButtom" class="buttomTab"></div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            lists: [
                "pretty",
                "large",
                "big",
                "small",
                "tall",
                "short",
                "long",
                "handsome",
                "plain",
                "quaint",
                "clean",
                "elegant",
                "easy",
                "angry",
                "crazy",
                "helpful",
                "mushy",
                "odd",
                "unsightly",
                "adorable",
                "important",
                "inexpensive",
                "cheap",
                "expensive",
                "fancy",
            ],
            showButtom: '',
            content: 0
        };
    },
    method: {
        onstart(item, index) {
            console.log(`${item}---${index}`);
        },
        onScroll(event) {
            if ((event.contentOffset.y - this.content) > 0) {
                this.showButtom = true
            } else {
                this.showButtom = false
            }
            console.log("===========", event.contentOffset.y - this.content)
            this.content = event.contentOffset.y
        }
    }
}
</script>

<style scoped>
.btn {
    width: 500px;
    padding: 20px;
    margin: 20px auto 0;
    border-radius: 10px;
    color: #6d7dff;
    text-align: center;
    font-size: 32px;
    border-style: solid;
    border-color: #6d7dff;
    border-width: 1px;
    opacity: 1;
}

.list-wrap {
    width: 750px;
    flex: 1;
    background-color: aliceblue;
}

.list-cell {
    width: 100%;
    margin-bottom: 20px;
}

.item {
    width: 750px;
    height: 50px;
    background-color: red;
}

.buttomTab {
    width: 100%;
    height: 100px;
    background-color: #6d7dff;
    position: absolute;
    bottom: 0;
}
</style>