<template>
    <div>
        <iframe id="iframeID" style="width:100%;" frameborder="no" border="0" marginwidth="0" marginheight="0" scrolling="yes" src="http://www.hao123.com"></iframe>
    </div>
</template>
<script>
export default {
    mounted() {
       let iframeID = document.getElementById('iframeID') 
       let device = document.documentElement.clientHeight
       iframeID.style.height = device - 73 + 'px'  
    }
    
}
</script>
</<style>

</style>
