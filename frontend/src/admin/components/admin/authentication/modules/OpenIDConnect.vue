
<template>

<div>

  <b-form-group horizontal :label-cols="3" description="The client_id." label="Client ID" label-for="module.config.client_id">
    <b-form-input type="text" id="module.config.client_id" v-model="module.config.client_id" />
  </b-form-group>

  <b-form-group horizontal :label-cols="3" description="The client_secret." label="Client secret" label-for="module.config.client_secret">
    <b-form-input type="text" id="module.config.client_secret" v-model="module.config.client_secret" />
  </b-form-group>

  <b-form-group horizontal :label-cols="3" description="list of the OAuth 2.0 &quot;scope&quot; values that this authorization server supports" label="scopes" label-for="module.config.scopes">
    <b-form-input type="text" id="module.config.scopes" v-model="module.config.scopes" />
  </b-form-group>

  <b-form-group horizontal :label-cols="3" description="Userinfo endpoint." label="Userinfo endpoint" label-for="module.config.userinfo_endpoint">
    <b-form-input type="text" id="module.config.userinfo_endpoint" v-model="module.config.userinfo_endpoint" />
  </b-form-group>

  <b-form-group horizontal :label-cols="3" description="URL of the authorization server's authorization endpoint." label="Authorization Endpoint"
    label-for="module.config.authorization_endpoint">
    <b-form-input type="text" id="module.config.authorization_endpoint" v-model="module.config.authorization_endpoint" />
  </b-form-group>

  <b-form-group horizontal :label-cols="3" description="URL of the authorization server's token endpoint." label="Token Endpoint" label-for="module.config.token_endpoint">
    <b-form-input type="text" id="module.config.token_endpoint" v-model="module.config.token_endpoint" />
  </b-form-group>

  <b-form-group horizontal :label-cols="3" description="Color of the login button." label="Color" label-for="module.config.button_color">
    <b-form-input type="text" id="module.config.button_color" v-model="module.config.button_color" />
  </b-form-group>

  <b-form-group horizontal :label-cols="3" description="Label for the login button" label="Label" label-for="module.config.button_text">
    <b-form-input type="text" id="module.config.button_text" v-model="module.config.button_text" />
  </b-form-group>

  <p v-if="info">
    Use the following redirect_uri: {{ info.callback }}
  </p>

</div>

</template>

<script>
export default {

  props: {
    module: null,
    info: null
  },

  data(){
    return {
      
      errors: {},
      
      wasValidated: false,
      loading: false,

      type: null,
      types: [],

      templates: {},

    }
  },

  mounted(){


    this.$http.get(this.$murl('api/mail_template')).then(response => {

      this.templates = response.data;

    }, response => {
      // error callback
    });
    
    

  },

  methods: {
    onSubmit(event){

      event.preventDefault();

    }
  }


  
}
</script>
