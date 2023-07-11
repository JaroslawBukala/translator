<template>
  <div id="translateform">
    <div class="col-md-6 col-md-offset-3">
    <form class="form-inline well" id="transForm" v-on:submit="formSubmit">
      <input class="form-control" type="text" v-model="textToTranslate" placeholder="Enter a Word..">
      <select class="form-control text-center" v-model='language'>
          <option value='ru'>Russian</option>
          <option value='es'>Spanish</option>
          <option value='fr'>French</option>
          <option value='zh'>Chinese</option>
      </select>

      <button class="btn btn-primary">Translate</button>
    </form>
  </div>
  </div>
</template>

<script>

export default {
  name: 'translateForm',
  data(){
    return{
      textToTranslate:'',
      language:''
    }
  },
  created(){
    this.language='ru'
  },
  methods:{
    formSubmit(e){
      this.$emit('formSubmit', this.textToTranslate, this.language)
      e.preventDefault();

    }
  }

}
</script>

<style>
    #transForm{
      border-radius:10px;
      border:1px #ccc solid
    }
</style>
