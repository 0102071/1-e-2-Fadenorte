<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Plataforma Avançada de Estudos Jurídicos</title>
    <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
    <script src="https://cdn.jsdelivr.net/npm/dayjs@1/dayjs.min.js"></script>
</head>
<body class="bg-gray-100 font-sans">
    <!-- Header -->
    <header class="bg-blue-800 p-4 text-white flex justify-between items-center shadow-lg">
        <h1 class="text-2xl font-bold">Plataforma Jurídica de Estudos</h1>
        <div>
            <span id="clock" class="font-mono text-lg"></span>
        </div>
    </header>

    <!-- Main Navigation -->
    <nav class="grid grid-cols-2 md:grid-cols-4 gap-4 p-4">
        <a href="#provas" class="bg-white rounded-2xl shadow p-4 text-center hover:bg-blue-200 transition">
            <img src="https://via.placeholder.com/150?text=Provas" class="mx-auto mb-2" alt="Provas">
            PDFs de Provas
        </a>
        <a href="#questoes" class="bg-white rounded-2xl shadow p-4 text-center hover:bg-blue-200 transition">
            <img src="https://via.placeholder.com/150?text=Quest%C3%B5es" class="mx-auto mb-2" alt="Questões">
            Cadernos de Questões
        </a>
        <a href="#materias" class="bg-white rounded-2xl shadow p-4 text-center hover:bg-blue-200 transition">
            <img src="https://via.placeholder.com/150?text=Mat%C3%A9rias" class="mx-auto mb-2" alt="Matérias">
            Conteúdos Acadêmicos
        </a>
        <a href="#oab" class="bg-white rounded-2xl shadow p-4 text-center hover:bg-blue-200 transition">
            <img src="https://via.placeholder.com/150?text=OAB" class="mx-auto mb-2" alt="OAB">
            Preparação OAB
        </a>
    </nav>

    <!-- Sections -->
    <section id="materias" class="p-4">
        <h2 class="text-xl font-semibold mb-2">Matérias por Tópico</h2>
        <ul class="grid md:grid-cols-3 gap-2">
            <li class="bg-white p-2 rounded shadow">Direito Constitucional</li>
            <li class="bg-white p-2 rounded shadow">Teoria do Direito</li>
            <li class="bg-white p-2 rounded shadow">História do Direito</li>
            <li class="bg-white p-2 rounded shadow">Teoria Geral do Estado</li>
            <li class="bg-white p-2 rounded shadow">Metodologia Científica</li>
            <li class="bg-white p-2 rounded shadow">Filosofia Jurídica</li>
            <li class="bg-white p-2 rounded shadow">Português</li>
        </ul>
    </section>

    <!-- Calendar -->
    <section id="calendario" class="p-4">
        <h2 class="text-xl font-semibold mb-2">Calendário 2025 - Anotações</h2>
        <iframe src="https://calendar.google.com/calendar/embed?src=pt.brazilian%23holiday%40group.v.calendar.google.com" class="w-full h-96 border rounded"></iframe>
    </section>

    <!-- Chat Simulador WhatsApp -->
    <section id="chat" class="p-4">
        <h2 class="text-xl font-semibold mb-2">Chat de Estudantes (Anônimo)</h2>
        <div class="bg-white rounded p-2 shadow h-64 overflow-y-scroll" id="chatBox">
            <p><strong>Anônimo 1:</strong> Alguém tem questões de Direito Constitucional?</p>
        </div>
        <input id="chatInput" class="border p-2 w-full mt-2 rounded" type="text" placeholder="Digite uma mensagem...">
    </section>

    <!-- Post-its e Mensagens Diárias -->
    <section id="postits" class="p-4">
        <h2 class="text-xl font-semibold mb-2">Mensagens e Dicas do Dia</h2>
        <div class="grid md:grid-cols-3 gap-4">
            <div class="bg-yellow-200 p-4 rounded-xl shadow">"Estudar todos os dias em pequenos blocos é mais eficaz do que maratonar."</div>
            <div class="bg-green-200 p-4 rounded-xl shadow">"Reescreva conceitos com suas próprias palavras para fixação!"</div>
            <div class="bg-pink-200 p-4 rounded-xl shadow">"Organize revisões semanais, mesmo que curtas."</div>
        </div>
    </section>

    <!-- IA de Apoio -->
    <section id="ia" class="p-4">
        <h2 class="text-xl font-semibold mb-2">Assistente Jurídico - IA</h2>
        <div class="bg-white rounded p-4 shadow">
            <p class="mb-2">Digite sua dúvida jurídica abaixo:</p>
            <input type="text" id="iaInput" class="border p-2 rounded w-full mb-2">
            <button onclick="iaResponder()" class="bg-blue-800 text-white p-2 rounded">Perguntar</button>
            <div id="iaResposta" class="mt-2 p-2 bg-gray-100 rounded"></div>
        </div>
    </section>

    <script>
        function atualizarRelogio() {
            const agora = dayjs().format('HH:mm:ss');
            document.getElementById('clock').innerText = agora;
        }
        setInterval(atualizarRelogio, 1000);
        atualizarRelogio();

        function iaResponder() {
            const pergunta = document.getElementById('iaInput').value;
            const resposta = `Estou analisando sua dúvida: "${pergunta}". Resposta em breve!`;
            document.getElementById('iaResposta').innerText = resposta;
        }

        const chatInput = document.getElementById('chatInput');
        const chatBox = document.getElementById('chatBox');
        chatInput.addEventListener('keypress', function(e) {
            if (e.key === 'Enter') {
                const msg = chatInput.value.trim();
                if (msg) {
                    const p = document.createElement('p');
                    p.innerHTML = `<strong>Anônimo:</strong> ${msg}`;
                    chatBox.appendChild(p);
                    chatInput.value = '';
                    chatBox.scrollTop = chatBox.scrollHeight;
                }
            }
        });
    </script>
</body>
</html>
