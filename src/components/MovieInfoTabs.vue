<template>
    <div>
        <ul class="movieInfoTbasHeader">
            <li v-for="(tab, index) in tabs" :key="tab.title" @click="selectTab(index)">{{ tab.title }}</li>
        </ul>
        <slot></slot>
    </div>
    
</template>

<script>
export default {
    data() {
        return {
            selectedIndex: 0,
            tabs: []
        }
    },
    created() {
        this.tabs = this.$children
    },
    mounted() {
        this.selectTab(0)
    },
    methods: {
        selectTab(i) {
            this.selectedIndex = i

            this.tabs.forEach((tab, index) => {
                tab.isActive = (index === i)
            })
        }
    }
}

</script>

<style>

.movieInfoTbasHeader {
    
}

ul.movieInfoTbasHeader {
    display: block;
    z-index: 1;
    list-style: none;
    margin: 0 0 0 20px;
    padding: 0;
  }

  ul.movieInfoTbasHeader > li {
    padding: 15px 30px;
    border-radius: 10px;
    margin: 0;
    display: inline-block;
    margin-right: 5px;
    cursor: pointer;
  }

</style>