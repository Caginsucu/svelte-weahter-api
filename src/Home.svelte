<script>
    import {Link} from 'svelte-navigator'
</script>




<main class="container">

    <h1 class="title">Hava Durumu Uygulamasına Hoşgeldin</h1>

    <div class="nav-links-wrapper">
        <ul class="nav-links">
            <li><Link to="/">Anasayfa</Link></li>
            <li><Link to="/weather">Hava Durumu</Link></li>

        </ul>
    </div>

    <div class="footer">
        <p class="author">&copy; Cagin Sucu Tarafından Yapılmıştır</p>
        <ul class="footer-links">
            <li><a href="https://www.github.com/caginsucu" target="_blank"><i class="fa-brands fa-github-alt"></i></a></li>
            <li><a href="https://www.linkedin.com/in/ahmet-cagin-sucu" target="_blank"><i class="fa-brands fa-linkedin-in"></i></a></li>
        </ul>
    </div>

</main>


<style>
    .container {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        gap: 2rem;

        width: 100%;
        height: 100vh;
        
        
        text-align: center;
        color: white;
    }

    .title {
        font-size: 1.6rem;
        letter-spacing: .18rem;
        text-transform: uppercase;
    }
    .footer {
        display: flex;
        flex-direction: column;
        gap: .5rem;
    }
    .footer-links,.nav-links {
        display: flex;
        justify-content: center;
        gap: .5rem;
    }

    .nav-links li {
        display: inline-block;
        color: white;
        padding: 10px 20px;
        border: 1px solid white;

        transition: .4s ease;
    }

    .nav-links li:hover {
        background-color: white;
        color: black;
    }


    .footer-links a {
        font-size: 1.4rem;
    }
    
</style>