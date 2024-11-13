<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mon Portfolio</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Arial', sans-serif;
        }

        body {
            background-color: #f5f5f5;
            color: #333;
            line-height: 1.6;
        }

        header {
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            padding: 2rem;
            background-color: #fff;
        }

        .name {
            font-size: 3rem;
            margin-bottom: 1rem;
            opacity: 0;
            transform: translateY(20px);
            animation: fadeInUp 1s forwards;
        }

        .title {
            font-size: 1.5rem;
            color: #666;
            margin-bottom: 2rem;
            opacity: 0;
            transform: translateY(20px);
            animation: fadeInUp 1s 0.5s forwards;
        }

        nav {
            position: fixed;
            top: 0;
            width: 100%;
            padding: 1rem;
            background-color: rgba(255, 255, 255, 0.95);
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
            z-index: 1000;
            transform: translateY(-100%);
            transition: transform 0.3s ease;
        }

        nav.visible {
            transform: translateY(0);
        }

        nav ul {
            display: flex;
            justify-content: center;
            list-style: none;
            gap: 2rem;
        }

        nav a {
            text-decoration: none;
            color: #333;
            transition: color 0.3s ease;
        }

        nav a:hover {
            color: #007bff;
        }

        section {
            padding: 5rem 2rem;
            max-width: 1200px;
            margin: 0 auto;
        }

        .projects {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin-top: 2rem;
        }

        .project-card {
            background-color: #fff;
            padding: 1.5rem;
            border-radius: 8px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
            transition: transform 0.3s ease;
        }

        .project-card:hover {
            transform: translateY(-5px);
        }

        .project-image {
            width: 100%;
            height: 200px;
            background-color: #ddd;
            margin-bottom: 1rem;
            border-radius: 4px;
        }

        h2 {
            text-align: center;
            margin-bottom: 3rem;
        }

        @keyframes fadeInUp {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .contact-form {
            max-width: 600px;
            margin: 0 auto;
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        input, textarea {
            width: 100%;
            padding: 0.8rem;
            border: 1px solid #ddd;
            border-radius: 4px;
            margin-top: 0.5rem;
        }

        button {
            background-color: #007bff;
            color: #fff;
            padding: 0.8rem 2rem;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }

        button:hover {
            background-color: #0056b3;
        }

        footer {
            text-align: center;
            padding: 2rem;
            background-color: #333;
            color: #fff;
        }

        @media (max-width: 768px) {
            .name {
                font-size: 2.5rem;
            }
            
            .title {
                font-size: 1.2rem;
            }

            nav ul {
                gap: 1rem;
            }
        }
    </style>
</head>
<body>
    <nav id="navbar">
        <ul>
            <li><a href="#accueil">Accueil</a></li>
            <li><a href="#projets">Projets</a></li>
            <li><a href="#contact">Contact</a></li>
        </ul>
    </nav>

    <header id="accueil">
        <h1 class="name">BIL David</h1>
        <p class="title">Développeur Web Créatif</p>
    </header>

    <section id="projets">
        <h2>Mes Projets</h2>
        <div class="projects">
            <div class="project-card">
                <div class="project-image"></div>
                <h3>Projet 1</h3>
                <p>Description du projet 1. Une brève explication des technologies utilisées et du résultat obtenu.</p>
            </div>
            <div class="project-card">
                <div class="project-image"></div>
                <h3>Projet 2</h3>
                <p>Description du projet 2. Une brève explication des technologies utilisées et du résultat obtenu.</p>
            </div>
            <div class="project-card">
                <div class="project-image"></div>
                <h3>Projet 3</h3>
                <p>Description du projet 3. Une brève explication des technologies utilisées et du résultat obtenu.</p>
            </div>
        </div>
    </section>

    <section id="contact">
        <h2>Contact</h2>
        <form class="contact-form">
            <div class="form-group">
                <label for="name">Nom</label>
                <input type="text" id="name" required>
            </div>
            <div class="form-group">
                <label for="email">Email</label>
                <input type="email" id="email" required>
            </div>
            <div class="form-group">
                <label for="message">Message</label>
                <textarea id="message" rows="5" required></textarea>
            </div>
            <button type="submit">Envoyer</button>
        </form>
    </section>

    <footer>
        <p>&copy; 2024 John Doe. Tous droits réservés.</p>
    </footer>

    <script>
        // Navigation sticky
        let prevScrollpos = window.pageYOffset;
        window.onscroll = function() {
            let currentScrollPos = window.pageYOffset;
            if (prevScrollpos > currentScrollPos) {
                document.getElementById("navbar").classList.add("visible");
            } else {
                document.getElementById("navbar").classList.remove("visible");
            }
            prevScrollpos = currentScrollPos;
        }

        // Smooth scroll pour la navigation
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                document.querySelector(this.getAttribute('href')).scrollIntoView({
                    behavior: 'smooth'
                });
            });
        });

        // Gestion du formulaire
        document.querySelector('.contact-form').addEventListener('submit', function(e) {
            e.preventDefault();
            const name = document.getElementById('name').value;
            const email = document.getElementById('email').value;
            const message = document.getElementById('message').value;
            
            console.log('Formulaire soumis:', { name, email, message });
            // Ici, vous pouvez ajouter votre logique d'envoi de formulaire
            alert('Message envoyé !');
            this.reset();
        });
    </script>
</body>
</html>
