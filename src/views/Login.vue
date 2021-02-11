<template>
    <div>
    <input v-model="login" type="text" placeholder="Логин" >
    <input v-model="password" type="password" placeholder="Пароль"> 
    <input type="submit" value="Войти" @click="auth"> 
    </div>
</template>
<script>
import axios from 'axios'
export default {
    data(){
        return{
            login: '',
            password: '',
        }
    },
    methods: {
        auth(){
            axios.get('http://37.77.104.246/api/jsonstorage/?id=d4adf8f323462ca5d4dd92d052114ff2')
                .then(res=>{
                    for(let i = 0; i<res.data.length; i++){
                        if (res.data[i].password == this.password && res.data[i].login== this.login){
                            this.$router.push('/user/' + res.data[i].login )
                            this.$emit('auth', res.data[i])
                        }
                    }
                })
        }
    }
}
</script>