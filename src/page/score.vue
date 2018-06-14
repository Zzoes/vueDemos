<template>
    <div>
        <item-container father-component="score"></item-container>
    </div>
</template>

<script>
import itemContainer from '@/components/itemContainer'
export default {
    name:'score',
    data (){
        return{
            
        }
    },
    components:{
        itemContainer
    }
}
</script>
