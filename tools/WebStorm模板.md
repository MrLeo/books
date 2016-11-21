
# 文件模版变量
- `${PACKAGE_NAME}` name of the package in which the new file is created
- `${USER}` current user system login name
- `${DATE}` current system date
- `${TIME}` current system time
- `${YEAR}` current year
- `${MONTH}` current month
- `${MONTH_NAME_SHORT}` first 3 letters of the current month name. Example: Jan, Feb, etc.
- `${MONTH_NAME_FULL}` full name of the current month. Example: January, February, etc.
- `${DAY}` current day of the month
- `${HOUR}` current hour
- `${MINUTE}`	current minute
- `${PROJECT_NAME}` the name of the current project

# 文件模版
```html
/**
 * @Date: ${DATE}  ${TIME}
 * @Author: ${USER}
 * Created with JetBrains WebStorm.
 */
<template>
    <div>
        <!--<component :is="currentView"></component>-->
    </div>
</template>
<script>
    import {mapState, mapGetters, mapMutations, mapActions} from 'vuex'
    import * as types from '../store/mutation-types'
    export default{
        name:'',
        components:{},
        props:[],
        data(){
            return{
                //currentView:''
            }
        },
        watch:{},
        computed: {
            ...mapState({}),
            ...mapGetters({
                //baseInfo: 'baseInfo'
            })
        },
        methods: mapActions([
            //'addToBaseInfo'
        ]),
        created(){},
        mounted(){}
    }
</script>
<style scoped lang="scss" rel="stylesheet/scss">
</style>
```

