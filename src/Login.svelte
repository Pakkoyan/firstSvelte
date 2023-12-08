<script lang="ts">
    import {navigate} from "svelte-routing";

    let login: string = '';
    let password: string = '';
    let errorMessage: string = '';

    function loginHandler() {
        const storedLogin = localStorage.getItem('login');
        const storedPassword = localStorage.getItem('password');

        if (!(login || password)) {
            errorMessage = 'Заполните поля';
            return;
        }

        if (login !== storedLogin || password !== storedPassword) {
            errorMessage = 'Инвалид логин ор пароль';
            return;
        }
        navigate('/menu');
    }
</script>

<form on:submit|preventDefault={loginHandler}>
    <input type="text" bind:value={login} placeholder="Login" />
    <input type="password" bind:value={password} placeholder="Password" />
    <button type="submit">Log in</button>
    {#if errorMessage}
        <p>{errorMessage}</p>
    {/if}
</form>
