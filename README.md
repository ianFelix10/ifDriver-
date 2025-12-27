# ifDriver-
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ifDriver - Oficial</title>
    <script src="https://www.gstatic.com/firebasejs/8.10.1/firebase-app.js"></script>
    <script src="https://www.gstatic.com/firebasejs/8.10.1/firebase-auth.js"></script>
    <style>
        body { margin: 0; font-family: sans-serif; background: #f1f5f9; display: flex; flex-direction: column; height: 100vh; }
        header { background: #2563eb; color: white; padding: 20px; text-align: center; font-weight: bold; font-size: 24px; }
        .container { padding: 20px; flex: 1; display: flex; flex-direction: column; justify-content: center; }
        input { width: 100%; padding: 15px; margin: 10px 0; border: 1px solid #ccc; border-radius: 8px; font-size: 16px; }
        button { width: 100%; padding: 15px; background: #2563eb; color: white; border: none; border-radius: 8px; font-size: 18px; font-weight: bold; cursor: pointer; }
        .link { text-align: center; margin-top: 15px; color: #2563eb; text-decoration: none; display: block; }
    </style>
</head>
<body>
    <header>ifDriver</header>
    <div class="container" id="auth-area">
        <h2 id="titulo">Login</h2>
        <input type="email" id="email" placeholder="E-mail">
        <input type="password" id="senha" placeholder="Senha">
        <button onclick="executar()">Entrar</button>
        <a href="#" class="link" onclick="alternar()" id="toggle">Criar conta gratuita</a>
    </div>

    <script>
        const firebaseConfig = {
            apiKey: "AIzaSyAiOUhWfK68qzo7miPSxqxYEH5aMqhswl4",
            authDomain: "ifdriver-33cb7.firebaseapp.com",
            projectId: "ifdriver-33cb7",
            appId: "1:692150714118:web:269879ff5c526f33236887"
        };
        firebase.initializeApp(firebaseConfig);

        let modoCadastro = false;
        function alternar() {
            modoCadastro = !modoCadastro;
            document.getElementById('titulo').innerText = modoCadastro ? 'Cadastro' : 'Login';
            document.getElementById('toggle').innerText = modoCadastro ? 'Já tenho conta' : 'Criar conta gratuita';
        }

        function executar() {
            const email = document.getElementById('email').value;
            const senha = document.getElementById('senha').value;
            const auth = firebase.auth();

            if(modoCadastro) {
                auth.createUserWithEmailAndPassword(email, senha)
                    .then(() => alert("Conta criada!"))
                    .catch(e => alert(e.message));
            } else {
                auth.signInWithEmailAndPassword(email, senha)
                    .then(() => alert("Logado!"))
                    .catch(e => alert(e.message));
            }
        }
    </script>
</body>
</html>
