<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Acessibilidade Digital para Todos</title>
    <meta name="description" content="Projeto de inclusão digital que ensina iniciantes a usar a internet e promove a acessibilidade para todos">
    <meta name="theme-color" content="#4CAF50">
    <link rel="canonical" href="https://seusite.com/acessibilidade-digital" />
    
    <!-- Open Graph / Social Media -->
    <meta property="og:title" content="Acessibilidade Digital para Todos" />
    <meta property="og:description" content="Projeto de inclusão digital que ensina iniciantes a usar a internet e promove a acessibilidade para todos" />
    <meta property="og:image" content="https://seusite.com/images/logo-social.png" />
    <meta property="og:url" content="https://seusite.com/acessibilidade-digital" />
    <meta property="og:type" content="website" />
    <meta name="twitter:card" content="summary_large_image" />
    
    <!-- Favicons -->
    <link rel="icon" href="/favicon.ico" sizes="any">
    <link rel="icon" href="/icon.svg" type="image/svg+xml">
    <link rel="apple-touch-icon" href="/apple-touch-icon.png">
    <link rel="manifest" href="/site.webmanifest">
    
    <!-- Preload de recursos importantes -->
    <link rel="preload" href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap" as="style">
    <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap">
    
    <!-- CSS dividido em seções lógicas -->
    <style>
        /* ===== RESET E VARIÁVEIS ===== */
        :root {
            --primary-color: #4CAF50;
            --primary-dark: #45a049;
            --background-dark: #000;
            --background-light: #111;
            --background-lighter: #222;
            --text-color: #f0f0f0;
            --text-contrast: #fff;
            --border-color: #444;
            --shadow-color: rgba(255, 255, 255, 0.1);
            --transition-fast: 0.2s;
            --transition-medium: 0.3s;
            --border-radius-sm: 4px;
            --border-radius-md: 8px;
            --border-radius-lg: 10px;
            --focus-outline: 3px solid var(--primary-color);
            --focus-offset: 2px;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        /* ===== BASE E TIPOGRAFIA ===== */
        html {
            font-size: 16px;
            scroll-behavior: smooth;
        }

        @media (min-width: 768px) {
            html {
                font-size: 18px;
            }
        }

        body {
            font-family: 'Poppins', sans-serif;
            background-color: var(--background-dark);
            color: var(--text-color);
            line-height: 1.6;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
        }

        h1, h2, h3 {
            line-height: 1.2;
            font-weight: 600;
        }

        h1 {
            font-size: 2.5rem;
        }

        h2 {
            font-size: 1.8rem;
        }

        h3 {
            font-size: 1.4rem;
        }

        p, li {
            margin-bottom: 1em;
        }

        a {
            color: var(--primary-color);
            text-decoration: underline;
            text-underline-offset: var(--focus-offset);
            transition: color var(--transition-fast);
        }

        a:hover, a:focus {
            color: var(--primary-dark);
            text-decoration: none;
        }

        :focus {
            outline: var(--focus-outline);
            outline-offset: var(--focus-offset);
        }

        /* ===== ACESSIBILIDADE ===== */
        .skip-link {
            position: absolute;
            top: -40px;
            left: 0;
            background: var(--primary-color);
            color: var(--text-contrast);
            padding: 8px;
            z-index: 100;
            transition: top var(--transition-medium);
        }

        .skip-link:focus {
            top: 0;
        }

        .sr-only {
            position: absolute;
            width: 1px;
            height: 1px;
            padding: 0;
            margin: -1px;
            overflow: hidden;
            clip: rect(0, 0, 0, 0);
            white-space: nowrap;
            border-width: 0;
        }

        @media (prefers-contrast: more) {
            body {
                background-color: var(--background-dark);
                color: var(--text-contrast);
            }
            
            a, button {
                border: 2px solid currentColor;
            }
        }

        @media (prefers-reduced-motion: reduce) {
            * {
                animation-duration: 0.01ms !important;
                animation-iteration-count: 1 !important;
                transition-duration: 0.01ms !important;
                scroll-behavior: auto !important;
            }
        }

        /* ===== LAYOUT ===== */
        .container {
            width: 100%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        header {
            background-color: var(--background-lighter);
            padding: 20px 0;
            text-align: center;
        }

        header h1 {
            color: var(--primary-color);
            margin-bottom: 10px;
            letter-spacing: 1px;
        }

        main {
            flex: 1;
            padding: 20px;
            max-width: 800px;
            margin: 0 auto;
        }

        footer {
            background-color: var(--background-lighter);
            padding: 20px;
            text-align: center;
            margin-top: 30px;
        }

        /* ===== COMPONENTES ===== */
        /* Botões */
        .button {
            display: inline-block;
            background-color: var(--primary-color);
            color: var(--text-contrast);
            border: none;
            padding: 10px 20px;
            border-radius: var(--border-radius-sm);
            cursor: pointer;
            font-size: 1rem;
            margin: 5px;
            transition: background-color var(--transition-medium);
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        .button:hover {
            background-color: var(--primary-dark);
        }

        .button:focus:not(:active)::after {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            width: 5px;
            height: 5px;
            background: rgba(255, 255, 255, 0.5);
            opacity: 0;
            border-radius: 100%;
            transform: scale(1, 1) translate(-50%);
            transform-origin: 50% 50%;
            animation: ripple 0.6s ease-out;
        }

        .button[aria-expanded="true"] {
            background-color: var(--primary-dark);
            font-weight: bold;
        }

        .button:disabled {
            opacity: 0.6;
            cursor: not-allowed;
        }

        .button-large {
            padding: 15px 30px;
            font-size: 1.1rem;
            border-radius: var(--border-radius-md);
            transition: transform var(--transition-fast);
        }

        .button-large:hover {
            transform: scale(1.05);
        }

        .button-large:active {
            transform: scale(0.95);
        }

        @keyframes ripple {
            0% {
                transform: scale(0, 0);
                opacity: 0.5;
            }
            100% {
                transform: scale(20, 20);
                opacity: 0;
            }
        }

        /* Abas */
        .tab {
            display: none;
        }

        .tab.active {
            display: block;
        }

        /* Seções de conteúdo */
        section {
            margin-bottom: 30px;
            background-color: var(--background-light);
            padding: 20px;
            border-radius: var(--border-radius-md);
            box-shadow: 0 2px 4px var(--shadow-color);
        }

        section h2 {
            color: var(--primary-color);
            margin-bottom: 15px;
        }

        section ul, section ol {
            margin-left: 20px;
            margin-bottom: 1em;
        }

        section li {
            margin-bottom: 10px;
        }

        /* Imagens */
        .section-image {
            width: 100%;
            max-width: 400px;
            height: auto;
            margin: 20px auto;
            display: block;
            border-radius: var(--border-radius-md);
        }

        /* Chatbot */
        .chatbot {
            position: fixed;
            bottom: 20px;
            right: 20px;
            width: 350px;
            max-height: 80vh;
            background-color: var(--background-light);
            border-radius: var(--border-radius-lg);
            box-shadow: 0 2px 10px var(--shadow-color);
            display: none;
            flex-direction: column;
            overflow: hidden;
            z-index: 1000;
        }

        @media (max-width: 600px) {
            .chatbot {
                width: calc(100% - 40px);
                max-width: 100%;
                bottom: 10px;
                right: 10px;
            }
        }

        .chatbot.open {
            display: flex;
        }

        .chatbot header {
            background-color: var(--background-lighter);
            color: var(--text-contrast);
            padding: 10px;
            text-align: center;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .chatbot .messages {
            flex: 1;
            padding: 10px;
            overflow-y: auto;
            background-color: var(--background-light);
            border-bottom: 1px solid var(--border-color);
            max-height: 300px;
        }

        .chatbot .message {
            margin-bottom: 10px;
            padding: 8px 12px;
            border-radius: var(--border-radius-md);
            max-width: 80%;
            word-wrap: break-word;
        }

        .chatbot .message.user {
            background-color: var(--primary-color);
            color: var(--text-contrast);
            margin-left: auto;
        }

        .chatbot .message.bot {
            background-color: var(--background-lighter);
            color: var(--text-contrast);
            margin-right: auto;
        }

        .chatbot input {
            width: 100%;
            padding: 10px;
            border: none;
            border-top: 1px solid var(--border-color);
            outline: none;
            font-size: 1rem;
            background-color: var(--background-lighter);
            color: var(--text-contrast);
        }

        .chatbot-toggle {
            position: fixed;
            bottom: 20px;
            right: 20px;
            z-index: 999;
        }

        @media (max-width: 600px) {
            .chatbot-toggle {
                bottom: 10px;
                right: 10px;
            }
        }

        /* Modal */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.7);
            justify-content: center;
            align-items: center;
            z-index: 2000;
        }

        .modal.open {
            display: flex;
        }

        .modal-content {
            background-color: var(--background-light);
            padding: 20px;
            border-radius: var(--border-radius-md);
            width: 90%;
            max-width: 400px;
            box-shadow: 0 2px 10px var(--shadow-color);
        }

        @media (prefers-reduced-motion: no-preference) {
            .modal-content {
                animation: fadeIn 0.3s ease-out;
            }
            
            @keyframes fadeIn {
                from { opacity: 0; transform: translateY(20px); }
                to { opacity: 1; transform: translateY(0); }
            }
        }

        .modal-content h2 {
            color: var(--primary-color);
            margin-bottom: 15px;
        }

        .modal-content label {
            display: block;
            margin-bottom: 5px;
            font-size: 0.9rem;
        }

        .modal-content input {
            width: 100%;
            padding: 10px;
            margin-bottom: 15px;
            border: 1px solid var(--border-color);
            border-radius: var(--border-radius-sm);
            background-color: var(--background-lighter);
            color: var(--text-contrast);
        }

        .modal-content button {
            width: 100%;
        }

        /* Loading */
        .loading {
            padding: 10px;
            text-align: center;
            color: var(--primary-color);
            font-weight: bold;
        }
    </style>
</head>
<body>
    <a href="#main-content" class="skip-link">Pular para conteúdo principal</a>

    <header role="banner">
        <div class="container">
            <h1 id="site-title">Acessibilidade Digital para Todos</h1>
            <nav aria-label="Navegação principal">
                <div class="header-buttons">
                    <button class="button" onclick="showTab('learn')" aria-controls="learn" aria-expanded="true">Quero Aprender</button>
                    <button class="button" onclick="showTab('help')" aria-controls="help" aria-expanded="false">Quero Ajudar</button>
                    <button class="button" onclick="showAccountModal()" aria-haspopup="dialog">Criar Conta</button>
                </div>
            </nav>
        </div>
    </header>

    <main id="main-content" role="main">
        <!-- Aba: Quero Aprender -->
        <div id="learn" class="tab active" role="tabpanel" aria-labelledby="learn-tab">
            <section>
                <h2>Como Usar a Internet?</h2>
                <p>A internet é uma ferramenta poderosa que pode transformar vidas, oferecendo acesso a conhecimento, comunicação e oportunidades. Se você está começando, não se preocupe! Vamos te guiar de forma simples e prática.</p>
                
                <img src="https://img.freepik.com/fotos-gratis/local-de-trabalho-com-dinheiro-e-notas-de-dolar-dos-eua-perto-do-laptop_158538-26284.jpg" 
                     alt="Pessoa usando um laptop com símbolos de internet e dinheiro ao redor" 
                     class="section-image" 
                     loading="lazy">
                
                <ol>
                    <li>
                        <strong>Conecte-se à internet:</strong>
                        <p>Para acessar a internet, você precisa de uma conexão. Aqui estão as principais formas de se conectar:</p>
                        <ul>
                            <li><strong>Wi-Fi:</strong> Em casa, cafés, bibliotecas ou outros locais públicos. Basta selecionar a rede Wi-Fi disponível e inserir a senha, se necessário.</li>
                            <li><strong>Dados móveis:</strong> No celular, você pode usar o plano de dados da sua operadora. Verifique se o pacote de dados está ativo e habilitado nas configurações do seu aparelho.</li>
                        </ul>
                    </li>
                    <li>
                        <strong>Abra um navegador:</strong>
                        <p>Um navegador é um programa que permite acessar sites. Aqui estão alguns navegadores populares:</p>
                        <ul>
                            <li><strong>Google Chrome:</strong> Disponível para computadores e celulares.</li>
                            <li><strong>Mozilla Firefox:</strong> Conhecido por sua segurança e privacidade.</li>
                            <li><strong>Microsoft Edge:</strong> Integrado ao Windows e com boa performance.</li>
                            <li><strong>Safari:</strong> Usado em dispositivos da Apple, como iPhones e Macs.</li>
                        </ul>
                        <img src="https://s32907.pcdn.co/wp-content/uploads/2019/08/escritorio-do-google-frente.jpg" 
                             alt="Logotipos dos principais navegadores web" 
                             class="section-image" 
                             loading="lazy">
                    </li>
                    <li>
                        <strong>Digite um endereço:</strong>
                        <p>Na barra maior do navegador, digite o site que você quer visitar. Por exemplo:</p>
                        <ul>
                            <li><strong>www.google.com</strong> para pesquisar informações.</li>
                            <li><strong>www.youtube.com</strong> para assistir a vídeos.</li>
                            <li><strong>www.facebook.com</strong> para acessar redes sociais.</li>
                        </ul>
                        <p>Se você não sabe o endereço exato, pode usar um site de busca, como o Google, para encontrar o que precisa.</p>
                    </li>
                    <li>
                        <strong>Pesquise informações:</strong>
                        <p>Use a barra de pesquisa do Google ou de outros sites para encontrar o que você precisa. Aqui estão algumas dicas:</p>
                        <ul>
                            <li>Digite palavras-chave relacionadas ao que você procura. Por exemplo: "receita de bolo de chocolate", "notícias sobre tecnologia", "como cuidar de plantas".</li>
                            <li>Use aspas para pesquisar frases exatas. Exemplo: "como fazer um currículo".</li>
                            <li>Adicione palavras como "tutorial" ou "passo a passo" para encontrar guias detalhados.</li>
                        </ul>
                    </li>
                    <li>
                        <strong>Navegue com segurança:</strong>
                        <p>A internet é um lugar incrível, mas é importante tomar alguns cuidados para proteger sua privacidade e segurança:</p>
                        <ul>
                            <li><strong>Evite clicar em links suspeitos:</strong> Eles podem levar a sites maliciosos ou tentar roubar suas informações.</li>
                            <li><strong>Use senhas fortes:</strong> Combine letras, números e símbolos para criar senhas seguras. Evite usar a mesma senha em vários sites.</li>
                            <li><strong>Mantenha seus dispositivos atualizados:</strong> Atualizações de software corrigem falhas de segurança e melhoram a performance.</li>
                            <li><strong>Cuidado com informações pessoais:</strong> Não compartilhe dados como CPF, endereço ou senhas em sites desconhecidos.</li>
                        </ul>
                        <img src="https://t2.tudocdn.net/363127?w=719&h=431" 
                             alt="Ilustração mostrando um cadeado representando segurança digital" 
                             class="section-image" 
                             loading="lazy">
                    </li>
                </ol>
                <p>Com esses passos, você já pode começar a explorar a internet com mais confiança! Se tiver dúvidas, clique no botão do chatbot no canto inferior direito.</p>
            </section>
        </div>

        <!-- Aba: Quero Ajudar -->
        <div id="help" class="tab" role="tabpanel" aria-labelledby="help-tab">
            <section>
                <h2>Nosso Projeto de Acessibilidade Digital</h2>
                <p>Acreditamos que a internet deve ser acessível para todos, independentemente de suas habilidades ou limitações. Nosso projeto visa:</p>
                <ul>
                    <li>Facilitar o acesso à internet para iniciantes.</li>
                    <li>Promover a inclusão digital.</li>
                    <li>Oferecer tutoriais e suporte.</li>
                </ul>
                <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRB--sjbOFzscMguCHe6YdI85XYdlMTK4xyTw&s" 
                     alt="Grupo diversificado de pessoas usando dispositivos digitais" 
                     class="section-image" 
                     loading="lazy">
                <p>Você pode contribuir de várias maneiras:</p>
                <ul>
                    <li><strong>Doações:</strong> Sua doação ajuda a manter nossos projetos e expandir nosso alcance.</li>
                    <li><strong>Voluntariado:</strong> Participe de iniciativas para ensinar pessoas a usar a internet.</li>
                    <li><strong>Divulgação:</strong> Compartilhe nosso projeto com amigos e familiares.</li>
                </ul>
                <button class="button button-large" onclick="openDonationModal()">Doar Agora</button>
            </section>
        </div>
    </main>

    <footer role="contentinfo">
        <div class="container">
            <h3>Acessibilidade Digital para Todos</h3>
            <p>&copy; <span id="current-year"></span> Todos os direitos reservados.</p>
        </div>
    </footer>

    <!-- Chatbot -->
    <div id="chatbot-learn" class="chatbot" role="dialog" aria-labelledby="chatbot-title-learn" aria-modal="true">
        <header>
            <h3 id="chatbot-title-learn">Chatbot de Ajuda</h3>
            <button class="button close-btn" onclick="toggleChatbot('learn')" aria-label="Fechar chatbot">×</button>
        </header>
        <div class="messages" id="chatbotMessagesLearn" role="log" aria-live="polite">
            <div class="message bot">Olá! Eu sou um chatbot para ajudar iniciantes na internet. Você pode me perguntar coisas como:<br>
                - Como usar o Google?<br>
                - Como pesquisar na internet?<br>
                - O que é um navegador?<br>
                Digite sua pergunta abaixo!
            </div>
        </div>
        <label for="chatbotInputLearn" class="sr-only">Digite sua mensagem</label>
        <input type="text" id="chatbotInputLearn" placeholder="Digite sua mensagem..." onkeypress="handleChatbotInput(event, 'learn')">
    </div>

    <div id="chatbot-help" class="chatbot" role="dialog" aria-labelledby="chatbot-title-help" aria-modal="true">
        <header>
            <h3 id="chatbot-title-help">Chatbot de Ajuda</h3>
            <button class="button close-btn" onclick="toggleChatbot('help')" aria-label="Fechar chatbot">×</button>
        </header>
        <div class="messages" id="chatbotMessagesHelp" role="log" aria-live="polite">
            <div class="message bot">Olá! Eu sou um chatbot para ajudar você a contribuir com nosso projeto. Você pode me perguntar coisas como:<br>
                - Como posso doar?<br>
                - Como ser voluntário?<br>
                - Como divulgar o projeto?<br>
                Digite sua pergunta abaixo!
            </div>
        </div>
        <label for="chatbotInputHelp" class="sr-only">Digite sua mensagem</label>
        <input type="text" id="chatbotInputHelp" placeholder="Digite sua mensagem..." onkeypress="handleChatbotInput(event, 'help')">
    </div>

    <!-- Botões para abrir o chatbot -->
    <button id="chatbot-toggle-learn" class="button chatbot-toggle" onclick="toggleChatbot('learn')">Falar com o Chatbot</button>
    <button id="chatbot-toggle-help" class="button chatbot-toggle" onclick="toggleChatbot('help')">Falar com o Chatbot</button>

    <!-- Modal de Doação -->
    <div id="donationModal" class="modal" role="dialog" aria-labelledby="donation-modal-title" aria-modal="true">
        <div class="modal-content">
            <h2 id="donation-modal-title">Faça uma Doação</h2>
            <form id="donationForm">
                <label for="donationAmount">Valor da Doação:</label>
                <input type="number" id="donationAmount" placeholder="R$ 0,00" required>
                
                <label for="donationName">Seu Nome:</label>
                <input type="text" id="donationName" placeholder="Nome" required>
                
                <label for="donationEmail">Seu Email:</label>
                <input type="email" id="donationEmail" placeholder="Email" required>
                
                <button type="submit" class="button">Doar</button>
            </form>
        </div>
    </div>

    <!-- Modal de Criação de Conta -->
    <div id="accountModal" class="modal" role="dialog" aria-labelledby="account-modal-title" aria-modal="true">
        <div class="modal-content">
            <h2 id="account-modal-title">Criar Conta</h2>
            <form id="accountForm">
                <label for="accountName">Seu Nome:</label>
                <input type="text" id="accountName" placeholder="Nome" required>
                
                <label for="accountEmail">Seu Email:</label>
                <input type="email" id="accountEmail" placeholder="Email" required>
                
                <label for="accountPassword">Senha:</label>
                <input type="password" id="accountPassword" placeholder="Senha" required minlength="6">
                
                <button type="submit" class="button">Criar Conta</button>
            </form>
        </div>
    </div>

    <script>
        // ===== VARIÁVEIS GLOBAIS =====
        const qaPairsLearn = [
            {
                question: "o que é internet",
                answer: "A internet é como uma grande rede que conecta computadores no mundo todo. É como uma biblioteca gigante onde você pode encontrar informações, falar com outras pessoas, assistir vídeos e muito mais."
            },
            {
                question: "como entrar na internet",
                answer: "Para entrar na internet você precisa:<br>1) Ter um celular, tablet ou computador<br>2) Conectar no Wi-Fi (rede sem fio) ou usar dados móveis (do seu plano de celular)<br>3) Abrir um programa chamado 'navegador' (como Chrome, Firefox ou Safari)"
            },
            {
                question: "o que é um navegador",
                answer: "Um navegador é um programa que abre sites na internet. É como uma porta para a web. Exemplos:<br>- Google Chrome<br>- Mozilla Firefox<br>- Microsoft Edge<br>- Safari (no iPhone e Mac)"
            },
            {
                question: "como pesquisar algo na internet",
                answer: "Passo a passo simples:<br>1) Abra o Google (digite www.google.com)<br>2) Na caixa branca, escreva o que quer saber<br>3) Aperte Enter ou clique no botão de lupa<br>4) Escolha um dos resultados que aparecerem"
            },
            {
                question: "como criar um email",
                answer: "Para criar um email gratuito:<br>1) Vá no site do Gmail (www.gmail.com)<br>2) Clique em 'Criar conta'<br>3) Preencha seu nome, data de nascimento<br>4) Escolha um nome de email e senha<br>5) Anote sua senha em lugar seguro!"
            },
            {
                question: "o que é wi-fi",
                answer: "Wi-Fi é uma forma de conectar à internet sem usar fios. É como um rádio invisível que leva internet para seu celular ou computador. Você precisa saber o nome da rede (ex: 'MinhaCasaWiFi') e a senha."
            },
            {
                question: "como conectar no wi-fi",
                answer: "No celular:<br>1) Vá em Configurações > Wi-Fi<br>2) Escolha o nome da rede<br>3) Digite a senha (peça para quem sabe)<br>4) Pronto! Quando vir o símbolo de Wi-Fi no topo, está conectado."
            },
            {
                question: "o que é um site",
                answer: "Um site é como uma página de revista na internet. Cada site tem um endereço que começa com www. Exemplos:<br>- www.google.com (para pesquisar)<br>- www.youtube.com (para vídeos)<br>- www.facebook.com (para redes sociais)"
            },
            {
                question: "como abrir um site",
                answer: "1) Abra o navegador (Chrome, Firefox, etc)<br>2) No topo tem uma barra branca longa<br>3) Digite o endereço do site (como www.receitas.com.br)<br>4) Aperte Enter no teclado"
            },
            {
                question: "o que é senha forte",
                answer: "Uma senha forte é difícil de adivinhar. Deve ter:<br>- Letras maiúsculas e minúsculas<br>- Números (ex: 123)<br>- Símbolos (ex: @#!)<br>Exemplo: <strong>Senha@2023</strong> é melhor que <strong>senha123</strong>"
            },
            {
                question: "como saber se um site é seguro",
                answer: "Dicas de segurança:<br>1) Veja se o endereço começa com <strong>https://</strong> (o 's' é importante)<br>2) Procure um cadeado perto do endereço<br>3) Desconfie de sites com muitos anúncios ou que pedem muitos dados pessoais"
            },
            {
                question: "o que não fazer na internet",
                answer: "Cuidados importantes:<br>- Não clique em links de emails desconhecidos<br>- Não digite senhas em sites que você não conhece<br>- Não acredite em tudo que lê (tem muita mentira na internet)<br>- Nunca marque encontro com estranhos"
            },
            {
                question: "como fazer compras online",
                answer: "Passo a passo seguro:<br>1) Escolha sites conhecidos (como Mercado Livre, Amazon)<br>2) Veja avaliações do vendedor<br>3) Prefira pagar quando o produto chegar ou use PayPal<br>4) Nunca envie dinheiro diretamente para pessoas"
            },
            {
                question: "o que é rede social",
                answer: "Rede social é um site ou app onde você conversa e compartilha coisas com outras pessoas. Exemplos:<br>- Facebook: para amigos e família<br>- WhatsApp: para mensagens<br>- Instagram: para fotos<br>- YouTube: para vídeos"
            },
            {
                question: "como baixar aplicativos",
                answer: "No celular:<br>1) Abra a Loja de Apps (Play Store no Android ou App Store no iPhone)<br>2) Pesquise o nome do app (ex: 'WhatsApp')<br>3) Clique em 'Instalar'<br>4) Espere baixar e depois abra o app"
            },
            {
                question: "esqueci minha senha",
                answer: "Não se preocupe! Na página de login, clique em 'Esqueci a senha'. Você vai precisar do seu email ou telefone cadastrado para receber um link e criar uma senha nova."
            },
            {
                question: "o que é vírus no computador",
                answer: "Vírus é um programa malicioso que pode danificar seu dispositivo ou roubar informações. Para se proteger:<br>- Não clique em links estranhos<br>- Tenha um antivírus instalado<br>- Mantenha seu sistema atualizado"
            },
            {
                question: "como assistir vídeos na internet",
                answer: "Você pode usar:<br>- YouTube (www.youtube.com) para vídeos em geral<br>- Netflix, Globoplay ou Amazon Prime para filmes e séries<br>Só digite o nome do site no navegador ou abra o aplicativo no celular."
            },
            {
                question: "o que é download",
                answer: "Download é quando você baixa um arquivo da internet para seu dispositivo. Por exemplo:<br>- Baixar uma foto para seu celular<br>- Baixar uma música para ouvir offline<br>Cuidado: só baixe arquivos de sites confiáveis!"
            },
            {
                question: "como enviar fotos pelo celular",
                answer: "Pelo WhatsApp:<br>1) Abra uma conversa<br>2) Clique no clipe 📎<br>3) Escolha 'Galeria' ou 'Câmera'<br>4) Selecione a foto e envie<br>Por email:<br>1) Escreva o email<br>2) Procure o botão 'Anexar'<br>3) Escolha a foto"
            }
        ];

        const qaPairsHelp = [
            {
                question: "o que é esse projeto",
                answer: "Nosso projeto ajuda pessoas que estão começando a usar a internet ou têm dificuldades com tecnologia. Ensinamos desde coisas básicas (como criar um email) até dicas de segurança online."
            },
            {
                question: "como posso doar",
                answer: "Você pode doar de várias formas:<br>- Pelo botão 'Doar Agora' (cartão ou PIX)<br>- Depósito bancário (nosso CNPJ: XX.XXX.XXX/XXXX-XX)<br>- Doação de equipamentos (celulares ou tablets usados em bom estado)"
            },
            {
                question: "para que serve o dinheiro doado",
                answer: "O dinheiro é usado para:<br>- Manter nosso site e materiais gratuitos<br>- Oferecer cursos presenciais em comunidades carentes<br>- Comprar equipamentos para quem não tem<br>- Pagar professores voluntários"
            },
            {
                question: "posso doar qualquer valor",
                answer: "Sim! Qualquer valor ajuda. Com R$ 20 compramos um caderno para aulas. Com R$ 100 pagamos internet para uma aula comunitária. Com R$ 500 compramos um tablet para doação."
            },
            {
                question: "como ser voluntário",
                answer: "Passos para voluntariado:<br>1) Preencha o formulário no site<br>2) Participe de uma entrevista online<br>3) Faça o treinamento (8 horas)<br>4) Escolha como ajudar: dar aulas, traduzir materiais ou ajudar online"
            },
            {
                question: "preciso saber muito de tecnologia",
                answer: "Não precisa ser expert! Valorizamos:<br>- Paciência para ensinar<br>- Vontade de ajudar<br>- Conhecimentos básicos de internet<br>Temos materiais de apoio para todos os voluntários."
            },
            {
                question: "quanto tempo preciso dedicar",
                answer: "Você escolhe:<br>- Aulas presenciais (4h por semana)<br>- Ajuda online (1h por dia)<br>- Tradução de materiais (quando puder)<br>Temos opções para todos os horários."
            },
            {
                question: "como divulgar o projeto",
                answer: "Você pode ajudar compartilhando:<br>- Nosso site nas redes sociais<br>- Vídeos explicativos no WhatsApp<br>- Cartazes em locais públicos (pegue em nosso site)<br>- Falando para amigos que podem se interessar"
            },
            {
                question: "onde vocês atuam",
                answer: "Atualmente estamos em:<br>- Capitais: São Paulo, Rio, BH<br>- Interior: cidades com mais de 50 mil habitantes<br>- Online: atendemos todo Brasil por videochamada<br>Queremos expandir para mais lugares!"
            },
            {
                question: "vocês dão certificado",
                answer: "Sim! Voluntários recebem certificado após 3 meses de trabalho. Alunos recebem certificado ao completar cursos. Os certificados podem ser usados para horas complementares em faculdades."
            },
            {
                question: "como surgiu o projeto",
                answer: "Começou em 2018 quando nossa fundadora viu sua avó com dificuldades para usar o celular. Hoje já ajudamos mais de 5.000 pessoas em todo o país! Queremos chegar a 10.000 até o próximo ano."
            },
            {
                question: "preciso de ajuda agora",
                answer: "Se for urgente:<br>- Ligue para nosso suporte: (11) 4002-8922<br>- Use o chatbot para perguntas simples<br>- Visite nossa página de ajuda rápida (link no rodapé)<br>Respondemos em até 24h."
            },
            {
                question: "vocês têm cursos",
                answer: "Sim! Oferecemos:<br>- Curso básico de internet (8 aulas)<br>- Segurança online (4 aulas)<br>- Redes sociais para negócios (6 aulas)<br>Todos gratuitos e com material de apoio."
            },
            {
                question: "como saber se doação chegou",
                answer: "Temos total transparência:<br>- Enviamos email com comprovante<br>- Publicamos relatórios mensais no site<br>- Você pode ligar para confirmar (11) 4002-8922<br>Todos os doadores recebem nossas newsletters."
            },
            {
                question: "posso doar equipamentos",
                answer: "Aceitamos:<br>- Celulares e tablets (mesmo antigos)<br>- Notebooks em bom estado<br>- Roteadores Wi-Fi<br>Os equipamentos são reformados e doados ou usados em aulas. Entre em contato para combinar a entrega."
            },
            {
                question: "como acompanhar o trabalho",
                answer: "Você pode:<br>- Assinar nossa newsletter (no rodapé do site)<br>- Seguir nas redes sociais @AcessibilidadeDigital<br>- Participar de nossos eventos online mensais<br>- Ler nossos relatórios anuais"
            },
            {
                question: "vocês são uma ong",
                answer: "Sim! Somos uma ONG registrada (CNPJ XX.XXX.XXX/XXXX-XX). Todos os recursos são usados para o projeto. Temos certificado de entidade beneficente e prestamos contas regularmente."
            },
            {
                question: "como entrar em contato",
                answer: "Por:<br>- Email: contato@acessibilidadedigital.org.br<br>- Telefone: (11) 4002-8922 (horário comercial)<br>- Redes sociais: @AcessibilidadeDigital<br>- Pessoalmente em nossos polos (veja endereços no site)"
            },
            {
                question: "preciso de ajuda especial",
                answer: "Temos programas para:<br>- Pessoas com deficiência visual<br>- Idosos<br>- Pessoas com baixa escolaridade<br>Conte-nos suas necessidades específicas no formulário de contato."
            },
            {
                question: "vocês dão suporte continuo",
                answer: "Sim! Depois das aulas básicas, oferecemos:<br>- Grupo de WhatsApp para tirar dúvidas<br>- Aulas de aprofundamento mensais<br>- Plantão de dúvidas por telefone<br>Ninguém fica sem apoio depois de começar conosco."
            }
        ];

        const translations = {
            'pt-BR': {
                'siteTitle': 'Acessibilidade Digital para Todos',
                'learnTab': 'Quero Aprender',
                'helpTab': 'Quero Ajudar',
                'accountButton': 'Criar Conta',
                'chatbotTitle': 'Chatbot de Ajuda',
                'donateButton': 'Doar Agora',
                'chatbotPrompt': 'Falar com o Chatbot'
            },
            'en': {
                'siteTitle': 'Digital Accessibility for All',
                'learnTab': 'I Want to Learn',
                'helpTab': 'I Want to Help',
                'accountButton': 'Create Account',
                'chatbotTitle': 'Help Chatbot',
                'donateButton': 'Donate Now',
                'chatbotPrompt': 'Talk to Chatbot'
            }
        };

        // ===== FUNÇÕES DE INTERAÇÃO =====
        function showTab(tabId) {
            // Esconder todas as abas
            document.querySelectorAll('.tab').forEach(tab => {
                tab.classList.remove('active');
                tab.setAttribute('aria-hidden', 'true');
            });
            
            // Mostrar a aba selecionada
            const activeTab = document.getElementById(tabId);
            activeTab.classList.add('active');
            activeTab.setAttribute('aria-hidden', 'false');
            
            // Atualizar atributos ARIA dos botões
            document.querySelector('[aria-controls="learn"]').setAttribute('aria-expanded', tabId === 'learn');
            document.querySelector('[aria-controls="help"]').setAttribute('aria-expanded', tabId === 'help');
            
            // Mostrar o botão do chatbot correspondente
            document.getElementById('chatbot-toggle-learn').style.display = tabId === 'learn' ? 'block' : 'none';
            document.getElementById('chatbot-toggle-help').style.display = tabId === 'help' ? 'block' : 'none';
        }

        function toggleChatbot(type) {
            const chatbot = document.getElementById(`chatbot-${type}`);
            const toggleButton = document.getElementById(`chatbot-toggle-${type}`);
            const isOpen = chatbot.classList.toggle('open');
            
            // Atualizar atributos ARIA
            chatbot.setAttribute('aria-hidden', !isOpen);
            toggleButton.setAttribute('aria-expanded', isOpen);
            
            // Esconder o botão de toggle quando o chatbot está aberto
            toggleButton.style.display = isOpen ? 'none' : 'block';
            
            // Focar no input quando o chatbot abrir
            if (isOpen) {
                setTimeout(() => {
                    document.getElementById(`chatbotInput${type.charAt(0).toUpperCase() + type.slice(1)}`).focus();
                }, 100);
            }
        }

        function openDonationModal() {
            const modal = document.getElementById('donationModal');
            modal.classList.add('open');
            modal.setAttribute('aria-hidden', 'false');
            document.getElementById('donationAmount').focus();
        }

        function closeDonationModal() {
            const modal = document.getElementById('donationModal');
            modal.classList.remove('open');
            modal.setAttribute('aria-hidden', 'true');
        }

        function showAccountModal() {
            const modal = document.getElementById('accountModal');
            modal.classList.add('open');
            modal.setAttribute('aria-hidden', 'false');
            document.getElementById('accountName').focus();
        }

        function closeAccountModal() {
            const modal = document.getElementById('accountModal');
            modal.classList.remove('open');
            modal.setAttribute('aria-hidden', 'true');
        }

        // ===== FUNÇÕES DO CHATBOT =====
        function respondToMessage(message, type) {
            const lowerMessage = message.toLowerCase().trim();
            let response = "Desculpe, não entendi. Aqui estão algumas perguntas que posso responder:<br>";
            
            const commonQuestions = type === 'learn' 
                ? ["Como usar o Google?", "Como pesquisar na internet?", "O que é um navegador?"]
                : ["Como posso doar?", "Como ser voluntário?", "Como divulgar o projeto?"];
            
            response += commonQuestions.map((q, i) => `${i+1}) ${q}`).join("<br>");
            
            const qaPairs = type === 'learn' ? qaPairsLearn : qaPairsHelp;
            
            // Busca mais inteligente
            for (const pair of qaPairs) {
                const keywords = pair.question.toLowerCase().split(' ');
                const matches = keywords.filter(keyword => lowerMessage.includes(keyword));
                
                // Se pelo menos 60% das palavras-chave corresponderem
                if (matches.length / keywords.length >= 0.6) {
                    response = pair.answer;
                    break;
                }
            }
            
            // Adicionar sugestões de acompanhamento
            if (!response.startsWith("Desculpe")) {
                response += "<br><br>Posso te ajudar com algo mais?";
            }
            
            return response;
        }

        function addMessage(text, sender, type) {
            const messages = document.getElementById(`chatbotMessages${type.charAt(0).toUpperCase() + type.slice(1)}`);
            const messageElement = document.createElement('div');
            messageElement.classList.add('message', sender);
            messageElement.innerHTML = text;
            messages.appendChild(messageElement);
            messages.scrollTop = messages.scrollHeight;
        }

        function handleChatbotInput(event, type) {
            const inputId = `chatbotInput${type.charAt(0).toUpperCase() + type.slice(1)}`;
            const input = document.getElementById(inputId);
            
            if (event.key === 'Enter') {
                const message = input.value.trim();
                if (message) {
                    addMessage(message, 'user', type);
                    input.value = '';
                    
                    // Mostrar que o bot está digitando
                    const typingIndicator = document.createElement('div');
                    typingIndicator.id = 'typing-indicator';
                    typingIndicator.className = 'message bot';
                    typingIndicator.textContent = 'Digitando...';
                    document.getElementById(`chatbotMessages${type.charAt(0).toUpperCase() + type.slice(1)}`)
                        .appendChild(typingIndicator);
                    
                    // Simular tempo de resposta
                    setTimeout(() => {
                        document.getElementById('typing-indicator')?.remove();
                        const botResponse = respondToMessage(message, type);
                        addMessage(botResponse, 'bot', type);
                    }, 1000 + Math.random() * 2000);
                }
            }
        }

        // ===== MANIPULAÇÃO DE FORMULÁRIOS =====
        function handleDonationForm(event) {
            event.preventDefault();
            
            const amount = parseFloat(document.getElementById('donationAmount').value);
            const name = document.getElementById('donationName').value.trim();
            const email = document.getElementById('donationEmail').value.trim();
            
            // Validação
            if (!amount || amount <= 0) {
                alert('Por favor, insira um valor válido para doação.');
                return;
            }
            
            if (!name) {
                alert('Por favor, insira seu nome.');
                return;
            }
            
            if (!email.includes('@') || !email.includes('.')) {
                alert('Por favor, insira um email válido.');
                return;
            }
            
            // Simular envio
            const form = event.target;
            const loading = document.createElement('div');
            loading.className = 'loading';
            loading.textContent = 'Processando doação...';
            form.appendChild(loading);
            
            setTimeout(() => {
                loading.remove();
                alert(`Obrigado, ${name}, por sua doação de R$ ${amount.toFixed(2)}! Um email de confirmação foi enviado para ${email}.`);
                closeDonationModal();
                form.reset();
            }, 1500);
        }

        function handleAccountForm(event) {
            event.preventDefault();
            
            const name = document.getElementById('accountName').value.trim();
            const email = document.getElementById('accountEmail').value.trim();
            const password = document.getElementById('accountPassword').value;
            
            // Validação
            if (!name) {
                alert('Por favor, insira seu nome.');
                return;
            }
            
            if (!email.includes('@') || !email.includes('.')) {
                alert('Por favor, insira um email válido.');
                return;
            }
            
            if (password.length < 6) {
                alert('A senha deve ter pelo menos 6 caracteres.');
                return;
            }
            
            // Simular criação de conta
            const form = event.target;
            const loading = document.createElement('div');
            loading.className = 'loading';
            loading.textContent = 'Criando sua conta...';
            form.appendChild(loading);
            
            setTimeout(() => {
                loading.remove();
                alert(`Conta criada com sucesso para ${name}! Um email de confirmação foi enviado para ${email}.`);
                closeAccountModal();
                form.reset();
            }, 2000);
        }

        // ===== INTERNACIONALIZAÇÃO =====
        function setLanguage(lang) {
            if (translations[lang]) {
                document.getElementById('site-title').textContent = translations[lang].siteTitle;
                document.querySelector('[onclick="showTab(\'learn\')"]').textContent = translations[lang].learnTab;
                document.querySelector('[onclick="showTab(\'help\')"]').textContent = translations[lang].helpTab;
                document.querySelector('[onclick="showAccountModal()"]').textContent = translations[lang].accountButton;
                document.querySelectorAll('.chatbot h3').forEach(header => {
                    header.textContent = translations[lang].chatbotTitle;
                });
                document.querySelector('.button-large').textContent = translations[lang].donateButton;
                document.querySelectorAll('.chatbot-toggle').forEach(btn => {
                    btn.textContent = translations[lang].chatbotPrompt;
                });
            }
        }

        // ===== INICIALIZAÇÃO =====
        document.addEventListener('DOMContentLoaded', function() {
            // Configurar eventos
            document.getElementById('donationForm').addEventListener('submit', handleDonationForm);
            document.getElementById('accountForm').addEventListener('submit', handleAccountForm);
            
            // Fechar modais ao clicar fora
            window.addEventListener('click', (event) => {
                if (event.target === document.getElementById('donationModal')) {
                    closeDonationModal();
                }
                if (event.target === document.getElementById('accountModal')) {
                    closeAccountModal();
                }
            });
            
            // Navegação por teclado nos modais
            const modals = document.querySelectorAll('.modal');
            modals.forEach(modal => {
                modal.addEventListener('keydown', function(e) {
                    if (e.key === 'Escape') {
                        if (modal.id === 'donationModal') closeDonationModal();
                        if (modal.id === 'accountModal') closeAccountModal();
                    }
                    
                    if (e.key === 'Tab') {
                        const focusableElements = 'button, [href], input, select, textarea, [tabindex]:not([tabindex="-1"])';
                        const focusableModalElements = modal.querySelectorAll(focusableElements);
                        const firstElement = focusableModalElements[0];
                        const lastElement = focusableModalElements[focusableModalElements.length - 1];
                        
                        if (e.shiftKey && document.activeElement === firstElement) {
                            lastElement.focus();
                            e.preventDefault();
                        } else if (!e.shiftKey && document.activeElement === lastElement) {
                            firstElement.focus();
                            e.preventDefault();
                        }
                    }
                });
            });
            
            // Detectar idioma do navegador
            const userLang = navigator.language || navigator.userLanguage;
            if (userLang.startsWith('en')) {
                setLanguage('en');
            }
            
            // Atualizar ano no rodapé
            document.getElementById('current-year').textContent = new Date().getFullYear();
            
            // Inicializar mostrando apenas o botão do chatbot da aba ativa
            document.getElementById('chatbot-toggle-help').style.display = 'none';
            
            // Configurar atributos ARIA iniciais
            document.getElementById('learn').setAttribute('aria-hidden', 'false');
            document.getElementById('help').setAttribute('aria-hidden', 'true');
            document.getElementById('chatbot-learn').setAttribute('aria-hidden', 'true');
            document.getElementById('chatbot-help').setAttribute('aria-hidden', 'true');
        });
    </script>
</body>
</html>
