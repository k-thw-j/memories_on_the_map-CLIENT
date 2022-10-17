<template>
    <br>
    <div class="frm">
        <div class="loginfrm">
            <input placeholder="ID" type="text" v-model="id"/><br>
            <input placeholder="Password" type="password" v-model="pw"/><br>
            <button class= "loginbtn" @click="login" type="submit">Sign In</button><br>
            <!-- <a href>GO SIGN UP</a> -->
        </div>
    </div>
</template>
<script>
import axios from 'axios'
export default {
    data() {
    return {
        id: "",
        pw: "",
    };
    },
    methods:{
        login(){
            axios.post('http://localhost:8000/api/auth/login',{id:this.id,pw:this.pw},{withCredentials:true})
            .then((res)=>{
                alert(res.data.msg)
            })
        }
    }
}
</script>
<style>
    .frm{
        position: absolute;
        top:50%;
        left:50%;
        transform: translate(-50%, -50%);
        text-align: center;
        width: 350px;
        height: 300px;
        border-radius: 10px;
        background-color: #EEEFF1;
    }
    .loginfrm{
        padding-top: 20%;
    }
    .loginbtn{
        margin-top: 20px;
        background:#1AAB8A;
        color:#fff;
        border:none;
        position:relative;
        width: 245px;
        height: 40px;
        font-size:2.0ch;
        padding:0 2em;
        cursor:pointer;
        transition:800ms ease all;
        border-radius: 4px;
        outline:none;
    }
    .loginbtn:hover{
        background:#fff;
        color:#1AAB8A;
    }
    .loginbtn:after{
        content:'';
        position:absolute;
        top:0;
        right:0;
        height:2px;
        width:0;
        background: #1AAB8A;
        transition:500ms ease all;
    }
    .loginbtn:after{
        right:inherit;
        top:inherit;
        left:0;
        bottom:0;
    }
    .loginbtn:hover:after{
        width:100%;
        transition:900ms ease all;
    }

    input{
        background-color: transparent;
        margin-top: 5px;
        width: 240px;
        height: 30px;
        border: none;
        border-bottom: 1px #cad2d1 solid;
    }

    input:focus{
        outline: none;
        border-bottom: 2px #0a6a56 solid;
    }
    body{
        background-color:#1BBC9B;
    }
</style>
