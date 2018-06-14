<template>
    <div>
        <!-- home 页面 -->
        <header class="top-week">
            <span class="txt" v-if="fatherComponent=='home'">{{level}}</span>
            <span class="txt" v-if="fatherComponent=='item'">第一题</span>
        </header>
        <section v-if="fatherComponent=='home'">
            <div class="txt-img"></div>
            <a href="javaScript:void(0);" class="start-btn"></a>
        </section>
        <section v-if="fatherComponent=='item'">
            <div class="txt-img item">
                <div class="t-item" v-if="itemDetail.length > 0">
                    <header class="w-txt">{{itemDetail[itemNum-1].topic_name}}</header>
                    <ul>
                        <li v-for="(item, index) in itemDetail[itemNum-1].topic_answer">
                            <span class="w-txt c-txt">{{index+1}}</span>
                            <span class="w-txt">{{item['answer_name']}}</span>
                        </li>
                    </ul>
                </div>
            </div>
            <a href="javascript:void(0);" class="start-btn next" @click="next" v-if="itemNum < itemDetail.length"></a>
            <a href="javascript:void(0);" class="start-btn submit" @click="submitAnswer" v-else></a>
      </section>
    </div>
</template>
<script>
import {mapState, mapMutations,mapActions} from 'vuex';

export default {
    name:'itemContainer',
    props:['fatherComponent'],
    data(){
        return {
            answer:[]
        }
    },
    computed:{
        ...mapState(['level','itemNum','allTime','timer','itemDetail'])
    },
    methods:{
        ...mapMutations(['next','submit']),
        submitAnswer(){
            if(this.answer.length > 0){
                this.$router.push('score');
            }else{
                alert('请选择答案')
            }
        }
    }
}
</script>



<style lang="scss" scoped>
    .c-txt{
        &.w-txt{
            font-size: 10px;
        }
        &:before{
            content:'';
            width: 15px;
            height: 15px;
            border-radius: 50%;
            border:1px solid #ccc;
            display: inline-block;
            margin-right: -12px;
            vertical-align: middle;
        }
    }
    .top-week{
        background: url('../assets/images/1-3.png') no-repeat;
        position: absolute;
        right: 2.6rem;
        top: 0;
        height: 7.35rem;
        width: 5.25rem;
        background-size: 100% 100%;
        .txt{
            position: absolute;
            bottom: 12px;
            left: 22px;
            font-size: 14px;
            color: rgb(236, 28, 209)
        }
    }
    .txt-img{
        background: url('../assets/images/1-2.png') no-repeat;
        background-size: 93% 100%;
        position: absolute;
        left: 8%;
        top: 7rem;
        width: 20rem;
        height: 45%;
        &.item{
             background: url('../assets/images/2-1.png') no-repeat;
             background-size: 93% 100%;
        }
        .w-txt{
            color: #fff;
            font-size: 14px;
        }
        .t-item{
            width: 80%;
            margin: 18% 20%;
            header{
                margin-bottom: 8px;
            }
            li{
                line-height: 25px;
                letter-spacing: 1px;
            }
        }
    }

    .start-btn{
        background: url('../assets/images/1-4.png') no-repeat;
        background-size: 100% 100%;
        width: 90px;
        height: 50px;
        display: block;
        position: absolute;
        top: 58%;
        left: calc(50% - 45px);
        &.next{
            background: url('../assets/images/2-2.png') no-repeat;
            background-size: 100% 100%;
        }
        &.submit{
            background: url('../assets/images/3-1.png') no-repeat;
            background-size: 100% 100%;
        }
    }
</style>


