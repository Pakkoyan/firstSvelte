<script lang="ts">
    import { Router, Route, Link } from 'svelte-routing';
    import Register from './Register.svelte';
    import Login from './Login.svelte';
    import Menu from './Menu.svelte';
</script>

<Router>
    <nav>
        <Link to="/register">Зарегаться</Link>
        <Link to="/login">Войти</Link>
        <Link to="/menu">Менюшка</Link>
    </nav>
    <Route path="/register" component={Register} />
    <Route path="/login" component={Login} />
    <Route path="/menu" component={Menu} />
</Router>
