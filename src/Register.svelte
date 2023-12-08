<script lang="ts">
    import { navigate } from 'svelte-routing';

    let login: string = '';
    let password: string = '';
    let errorMessage: string = '';

    function register() {
        if (login.length < 6 || password.length < 6) {
            errorMessage = 'Логин и пароль должен быть больше 6 символов ващето';
            return;
        }
        if (!(password.match(/.*[0-9].*/) || password.match(/.*[!@#$%^&*].*/))) {
            errorMessage = 'Пасворд должен держать в себе символ букву и тд и тп';
            return;
        }

        localStorage.setItem('login', login);
        localStorage.setItem('password', password);
        errorMessage = '';
        navigate('/menu');

    }
</script>

<form on:submit|preventDefault={register}>
    <input type="text" bind:value={login} placeholder="Login" />
    <input type="password" bind:value={password} placeholder="Password" />
    <button type="submit">Register</button>
    {#if errorMessage}
        <p>{errorMessage}</p>
    {/if}
</form>
