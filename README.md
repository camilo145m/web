#<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Salome - Tienda</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-image: radial-gradient(circle, #000080, #00001a);
            color: white;
        }

        .sidebar {
            height: 100%;
            width: 250px;
            position: fixed;
            top: 0;
            left: -250px;
            background-color: rgba(0, 0, 0, 0.8);
            transition: 0.3s;
            padding-top: 60px;
            z-index: 1;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
        }

        .sidebar.show {
            left: 0;
        }

        .sidebar ul {
            list-style-type: none;
            padding: 0;
        }

        .sidebar ul li {
            padding: 10px;
            color: #fff;
            cursor: pointer;
        }

        .sidebar ul li:hover {
            background-color: #555;
        }

        .sidebar .footer {
            text-align: center;
            padding: 10px;
            color: #fff;
            border-top: 1px solid #555;
        }

        .sidebar .user-info {
            text-align: center;
            margin-top: 20px;
        }

        .sidebar .user-info img {
            width: 50px;
            border-radius: 50%;
        }

        .content {
            margin-left: 250px;
            padding: 20px;
            transition: margin-left 0.3s;
            z-index: 0;
        }

        .menu-toggle {
            position: fixed;
            left: 20px;
            top: 20px;
            color: #fff;
            cursor: pointer;
            z-index: 2;
        }

        h1, h2 {
            color: white;
        }

        a {
            color: #1e90ff;
        }

        .registro-section {
            display: none;
        }

        .registro-section.show {
            display: block;
        }

        #user-profile {
            text-align: center;
            margin-top: 20px;
        }

        #user-profile img {
            width: 100px;
            border-radius: 50%;
            margin-bottom: 10px;
        }

        #user-profile p {
            margin: 0;
            font-size: 18px;
        }
    </style>
</head>
<body>
    <div class="sidebar" id="sidebar">
        <div class="user-info" id="user-info" style="display: none;">
            <img src="https://static.vecteezy.com/system/resources/previews/019/879/186/non_2x/user-icon-on-transparent-background-free-png.png" alt="User Icon">
            <p id="user-name"></p>
        </div>
        <ul>
            <li onclick="showSection('inicio')">Inicio</li>
            <li onclick="showSection('contacto')">Contacto</li>
            <li onclick="showSection('acerca')">Acerca de</li>
            <li onclick="showSection('registro')">Registro</li>
        </ul>
        <div id="user-profile" style="display: none;">
            <img src="https://cdn-icons-png.freepik.com/256/12808/12808894.png?semt=ais_hybrid" alt="User Profile">
            <p id="user-profile-name"></p>
        </div>
        <div class="footer">
            &copy; 2024 Salome
        </div>
    </div>

    <div class="content" id="content">
        <h1>Salome - Tienda</h1>
        <div id="inicio" style="display: none;">
            <h2>Inicio</h2>
            <p>Bienvenido a Salome - Tienda. Aquí puedes escribir tus notas.</p>
        </div>
        <div id="contacto" style="display: none;">
            <h2>Contacto</h2>
            <p>Correo: <a href="mailto:camilo80m9nsalvo@gmail.com">camilo80m9nsalvo@gmail.com</a></p>
            <p>Teléfono: <a href="tel:+573135150856">313 5150856</a></p>
            <p>WhatsApp: <a href="https://wa.me/573135150856">313 5150856</a></p>
        </div>
        <div id="acerca" style="display: none;">
            <h2>Acerca de</h2>
            <p>Somos una tienda ubicada en M14 C11. Te ofrecemos un medio digitalizado de ver nuestros contactos y hacer pedidos mediante WhatsApp y más.</p>
        </div>
        <div id="registro" class="registro-section">
            <h2>Registro</h2>
            <input type="text" id="input-name" placeholder="Nombre">
            <button onclick="register()">Aceptar</button>
        </div>
    </div>

    <div class="menu-toggle" onclick="showSidebar()">☰</div>

    <script>
        function showSidebar() {
            var sidebar = document.getElementById('sidebar');
            sidebar.classList.toggle('show');
        }

        function showSection(sectionId) {
            // Oculta todas las secciones
            var sections = document.querySelectorAll('.content > div');
            sections.forEach(function(section) {
                section.style.display = 'none';
            });

            // Muestra la sección seleccionada
            var selectedSection = document.getElementById(sectionId);
            if (selectedSection) {
                selectedSection.style.display = 'block';
            }

            // Si la sección es de registro, muestra el formulario de registro
            if (sectionId === 'registro') {
                var registroSection = document.querySelector('.registro-section');
                registroSection.classList.add('show');
            } else {
                var registroSection = document.querySelector('.registro-section');
                registroSection.classList.remove('show');
            }
        }

        function register() {
            var nameInput = document.getElementById('input-name').value;
            var userProfile = document.getElementById('user-profile');
            var userName = document.getElementById('user-name');
            var userProfileName = document.getElementById('user-profile-name');
            
            userName.textContent = nameInput;
            userProfileName.textContent = nameInput;
            userProfile.style.display = 'block';
        }
    </script>
</body>
</html>
