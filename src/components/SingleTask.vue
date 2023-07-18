<template>
    <div class="task">
        <h4>{{ task.text }} <span>X</span>  </h4>
        <p>{{ task.date }}</p>
    </div>
</template>

<script>
    export default{
        props:{
            task:Object
        }
        
    }
</script>

<style>
.task{
    font-size: small;
    padding: 5px 20px;
    background-color: rgba(128, 128, 128, 0.288);
    margin-top: 2px;
    border-radius: 3px;
}
.task span{
    float: right;
    cursor: pointer;
    color: red;
}
</style>