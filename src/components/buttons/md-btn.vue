<template>
    <a :class="[btnType,disabled?'disabled':'',large?'btn-large':'']">
       <slot name="icon">
            <md-icon   v-if="showIcon"  :text="iconText" :pos="iconPos"></md-icon>
       </slot> 
        <slot>
        </slot>
    </a>
</template>

<script>
import {hasIcon} from '../mixins/common-mixin.js';
export default {
    mixins:[hasIcon],
    props:{
            large:Boolean,
            disabled:Boolean,
            type:String
        },
    computed:{
        btnType(){
           switch(this.type){
                case 'floating' :
                    return 'btn-floating';
                case 'flat' :
                    return 'btn-flat';
                default :
                    return 'btn'
           }
        },
        showIcon(){
            return (this.type !== 'flat' && this.iconText);
        }
    }
}
</script>