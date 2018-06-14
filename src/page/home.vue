<template>
    <div>
        <item-container father-component="home"></item-container>
    </div>
</template>

<script>
import itemContainer from '@/components/itemContainer'
export default {
    name:'home',
    data (){
        return{
            
        }
    },
    components:{
        itemContainer
    }
}
</script>
