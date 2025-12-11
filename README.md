# overmind-treinamento
Documentação de treinamento do sistema OVERMIND"

<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>OVERMIND - Módulo Elegibilidade</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=Rajdhani:wght@300;400;600;700&display=swap');
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Rajdhani', sans-serif;
            background: linear-gradient(135deg, #0a0e27 0%, #1a1f3a 50%, #0f1729 100%);
            color: #e0e6f0;
            line-height: 1.6;
            padding: 40px;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            background: rgba(15, 23, 42, 0.95);
            border-radius: 20px;
            overflow: hidden;
            box-shadow: 0 20px 60px rgba(0, 255, 255, 0.3);
            border: 2px solid rgba(0, 255, 255, 0.3);
        }
        
        .header {
            background: linear-gradient(135deg, #00ff88 0%, #00d4ff 50%, #0099ff 100%);
            padding: 60px 40px;
            text-align: center;
            position: relative;
            overflow: hidden;
        }
        
        .header::before {
            content: '';
            position: absolute;
            top: -50%;
            left: -50%;
            width: 200%;
            height: 200%;
            background: repeating-linear-gradient(
                0deg,
                transparent,
                transparent 2px,
                rgba(255, 255, 255, 0.03) 2px,
                rgba(255, 255, 255, 0.03) 4px
            );
            animation: scan 8s linear infinite;
        }
        
        @keyframes scan {
            0% { transform: translateY(0); }
            100% { transform: translateY(50px); }
        }
        
        .header h1 {
            font-family: 'Orbitron', sans-serif;
            font-size: 4em;
            font-weight: 900;
            color: #ffffff;
            text-shadow: 0 0 20px rgba(0, 0, 0, 0.5), 0 0 40px rgba(0, 255, 136, 0.5);
            letter-spacing: 8px;
            margin-bottom: 10px;
            position: relative;
            z-index: 1;
        }
        
        .header .module-badge {
            display: inline-block;
            background: rgba(0, 0, 0, 0.3);
            padding: 10px 30px;
            border-radius: 50px;
            font-size: 1.2em;
            color: #ffffff;
            font-weight: 700;
            letter-spacing: 3px;
            margin-bottom: 15px;
            position: relative;
            z-index: 1;
            border: 2px solid rgba(255, 255, 255, 0.3);
        }
        
        .header .subtitle {
            font-size: 1.6em;
            color: rgba(255, 255, 255, 0.95);
            font-weight: 700;
            position: relative;
            z-index: 1;
            text-transform: uppercase;
            letter-spacing: 4px;
        }
        
        .content {
            padding: 50px;
        }
        
        .section {
            margin-bottom: 50px;
            background: rgba(30, 41, 59, 0.6);
            padding: 40px;
            border-radius: 15px;
            border-left: 5px solid #00ff88;
            backdrop-filter: blur(10px);
            transition: all 0.3s ease;
        }
        
        .section:hover {
            transform: translateX(5px);
            box-shadow: 0 10px 30px rgba(0, 255, 136, 0.2);
        }
        
        .section-title {
            font-family: 'Orbitron', sans-serif;
            font-size: 2em;
            color: #00ff88;
            margin-bottom: 25px;
            text-transform: uppercase;
            letter-spacing: 3px;
            display: flex;
            align-items: center;
            gap: 15px;
        }
        
        .section-title::before {
            content: '▶';
            color: #00d4ff;
            font-size: 0.8em;
        }
        
        .highlight-box {
            background: linear-gradient(135deg, rgba(0, 255, 136, 0.15) 0%, rgba(0, 212, 255, 0.15) 100%);
            border: 2px solid rgba(0, 255, 136, 0.4);
            padding: 25px;
            border-radius: 12px;
            margin: 20px 0;
        }
        
        .highlight-box h3 {
            color: #00ff88;
            font-size: 1.4em;
            margin-bottom: 15px;
            font-weight: 700;
        }
        
        .credentials {
            background: rgba(0, 0, 0, 0.4);
            padding: 25px;
            border-radius: 10px;
            border: 1px solid #00ff88;
            font-family: 'Courier New', monospace;
            margin: 20px 0;
        }
        
        .credentials p {
            color: #00ff88;
            font-size: 1.1em;
            margin: 8px 0;
        }
        
        .credentials strong {
            color: #00d4ff;
        }
        
        .step {
            background: rgba(0, 150, 100, 0.1);
            padding: 20px;
            margin: 15px 0;
            border-radius: 10px;
            border-left: 4px solid #00ff88;
            transition: all 0.3s ease;
        }
        
        .step:hover {
            background: rgba(0, 150, 100, 0.2);
            transform: translateX(3px);
        }
        
        .step-number {
            display: inline-block;
            background: linear-gradient(135deg, #00ff88, #00d4ff);
            color: #0a0e27;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            text-align: center;
            line-height: 40px;
            font-weight: 900;
            font-family: 'Orbitron', sans-serif;
            margin-right: 15px;
            font-size: 1.2em;
        }
        
        .convênios-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 15px;
            margin: 20px 0;
        }
        
        .convenio-item {
            background: rgba(0, 255, 136, 0.1);
            padding: 15px;
            border-radius: 8px;
            border: 1px solid rgba(0, 255, 136, 0.3);
            text-align: center;
            font-weight: 600;
            transition: all 0.3s ease;
        }
        
        .convenio-item:hover {
            background: rgba(0, 255, 136, 0.2);
            transform: scale(1.05);
            box-shadow: 0 5px 15px rgba(0, 255, 136, 0.3);
        }
        
        .alert {
            background: linear-gradient(135deg, rgba(255, 170, 0, 0.2), rgba(255, 200, 50, 0.2));
            border: 2px solid #ffaa00;
            padding: 20px;
            border-radius: 10px;
            margin: 20px 0;
        }
        
        .alert strong {
            color: #ffcc00;
            font-size: 1.2em;
        }
        
        .success {
            background: linear-gradient(135deg, rgba(0, 255, 136, 0.2), rgba(0, 212, 255, 0.2));
            border: 2px solid #00ff88;
            padding: 20px;
            border-radius: 10px;
            margin: 20px 0;
        }
        
        .success strong {
            color: #00ff88;
            font-size: 1.2em;
        }
        
        .image-container {
            background: rgba(0, 0, 0, 0.3);
            padding: 20px;
            border-radius: 12px;
            margin: 25px 0;
            border: 2px solid rgba(0, 255, 136, 0.2);
            text-align: center;
        }
        
        .image-container img {
            max-width: 100%;
            height: auto;
            border-radius: 8px;
            box-shadow: 0 10px 30px rgba(0, 255, 136, 0.3);
            border: 1px solid rgba(0, 255, 136, 0.3);
        }
        
        .image-caption {
            color: #00ff88;
            font-size: 0.95em;
            margin-top: 15px;
            font-style: italic;
        }
        
        ul {
            list-style: none;
            padding-left: 0;
        }
        
        li {
            padding: 10px 0;
            padding-left: 30px;
            position: relative;
        }
        
        li::before {
            content: '◆';
            position: absolute;
            left: 0;
            color: #00ff88;
            font-size: 1.2em;
        }
        
        .key-message {
            background: linear-gradient(135deg, rgba(0, 255, 136, 0.25), rgba(0, 212, 255, 0.25));
            border: 3px solid #00ff88;
            padding: 30px;
            border-radius: 15px;
            margin: 30px 0;
            text-align: center;
            box-shadow: 0 0 30px rgba(0, 255, 136, 0.3);
        }
        
        .key-message h3 {
            font-family: 'Orbitron', sans-serif;
            font-size: 1.8em;
            color: #00ff88;
            margin-bottom: 15px;
            letter-spacing: 2px;
        }
        
        .key-message p {
            font-size: 1.2em;
            line-height: 1.8;
        }
        
        .footer {
            background: linear-gradient(135deg, #1a1f3a, #0a0e27);
            padding: 30px;
            text-align: center;
            border-top: 2px solid rgba(0, 255, 136, 0.3);
        }
        
        .footer p {
            color: #00ff88;
            font-size: 1.1em;
        }
        
        @media print {
            body {
                background: white;
                padding: 0;
            }
            .container {
                box-shadow: none;
                border: none;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <div class="module-badge">MÓDULO ESPECIALIZADO</div>
            <h1>OVERMIND</h1>
            <p class="subtitle">ELEGIBILIDADE</p>
        </div>
        
        <div class="content">
            <div class="section">
                <h2 class="section-title">Funções do Sistema</h2>
                <ul>
                    <li>Autorização de exames</li>
                    <li>Emissão de elegibilidade</li>
                </ul>
            </div>
            
            <div class="section">
                <h2 class="section-title">Qual a Finalidade?</h2>
                <p>O OVERMIND é um <strong>sistema de autorização automatizado</strong> que possibilita o lançamento de pedidos de autorização e elegibilidade através do Tasy, com o intuito de:</p>
                <div class="highlight-box">
                    <h3>✓ Agilizar o processo de atendimento</h3>
                    <p>Reduzindo significativamente o tempo dedicado em solicitações</p>
                    <h3>✓ Eliminar acessos múltiplos</h3>
                    <p>Dispensando o acesso e uso dos portais de cada convênio individualmente</p>
                </div>
            </div>
            
            <div class="section">
                <h2 class="section-title">Como o OVERMIND Funciona?</h2>
                <p>O sistema integra-se ao Tasy através de um processo simplificado:</p>
                <div class="step">
                    <span class="step-number">1</span>
                    <strong>Acesse o sistema através do link oficial</strong>
                </div>
                <div class="step">
                    <span class="step-number">2</span>
                    <strong>Preencha os dados do pedido médico no Tasy</strong> (opção "AUTORIZAÇÃO CONVÊNIO")
                </div>
                <div class="step">
                    <span class="step-number">3</span>
                    <strong>Anexe o pedido e envie</strong> através do estágio "LIBERADO PARA OVERMIND"
                </div>
                <div class="step">
                    <span class="step-number">4</span>
                    <strong>Visualize e imprima a guia</strong> dentro da plataforma OVERMIND
                </div>
                
                <div class="credentials">
                    <h3 style="color: #00ff88; margin-bottom: 15px;">📡 CREDENCIAIS DE ACESSO</h3>
                    <p><strong>URL:</strong> https://www.overmind.ai/portal/home</p>
                    <p><strong>DOMÍNIO:</strong> scpoa</p>
                    <p><strong>USUÁRIO:</strong> portal</p>
                    <p><strong>SENHA:</strong> scpoa123</p>
                </div>
                
                <div class="alert">
                    <strong>⚠️ IMPORTANTE:</strong> Mantenha o site sempre aberto para acompanhar as guias lançadas e imprimir a elegibilidade quando necessário.
                </div>
            </div>
            
            <div class="section">
                <h2 class="section-title">Convênios com Elegibilidade Ativa</h2>
                <p style="margin-bottom: 20px;">Os seguintes convênios possuem elegibilidade integrada ao OVERMIND:</p>
                <div class="convênios-grid">
                    <div class="convenio-item">ASSEFAZ</div>
                    <div class="convenio-item">PROASA</div>
                    <div class="convenio-item">BRADESCO</div>
                    <div class="convenio-item">MAIS UNIMED</div>
                    <div class="convenio-item">SAÚDE CAIXA</div>
                    <div class="convenio-item">POSTAL SAÚDE</div>
                    <div class="convenio-item">AMIL</div>
                    <div class="convenio-item">GEAP</div>
                    <div class="convenio-item">SUL AMÉRICA</div>
                    <div class="convenio-item">MEDISERVICE</div>
                    <div class="convenio-item">SAÚDE PETROBRÁS</div>
                    <div class="convenio-item">GAMA SAÚDE</div>
                </div>
            </div>
            
            <div class="section">
                <h2 class="section-title">O Que é Elegibilidade?</h2>
                <div class="key-message">
                    <h3>🔍 CONCEITO FUNDAMENTAL</h3>
                    <p>A elegibilidade é a <strong>confirmação automática</strong> de que o paciente possui cobertura ativa no convênio e está apto a realizar procedimentos naquele momento.</p>
                </div>
                
                <div class="highlight-box">
                    <h3>Diferença entre Autorização e Elegibilidade</h3>
                    <p><strong style="color: #00d4ff;">AUTORIZAÇÃO:</strong> Precisa ser lançada ANTES de gerar o atendimento no Tasy</p>
                    <p style="margin-top: 10px;"><strong style="color: #00ff88;">ELEGIBILIDADE:</strong> É gerada automaticamente DURANTE a geração do atendimento</p>
                </div>
            </div>
            
            <div class="section">
                <h2 class="section-title">Passo a Passo - Elegibilidade</h2>
                
                <div class="step">
                    <span class="step-number">1</span>
                    <strong>Inicie o processo de atendimento no Tasy</strong>
                    <p style="margin-top: 10px; padding-left: 15px;">A elegibilidade será gerada automaticamente quando você inserir os dados da carteirinha do convênio na parte de "CONVÊNIOS" do Tasy</p>
                </div>
                
                <div class="step">
                    <span class="step-number">2</span>
                    <strong>Preencha os dados do solicitante e da senha</strong>
                    <p style="margin-top: 10px; padding-left: 15px;">Logo após preencher estes dados, uma tela se abrirá automaticamente para os convênios com elegibilidade ativa</p>
                </div>
                
                <div class="step">
                    <span class="step-number">3</span>
                    <strong>Preencha o número da carteirinha</strong>
                    <p style="margin-top: 10px; padding-left: 15px;">Digite o número da carteirinha no campo indicado</p>
                </div>
                
                <div class="step">
                    <span class="step-number">4</span>
                    <strong>Pressione a tecla TAB</strong>
                    <p style="margin-top: 10px; padding-left: 15px;">Continue pressionando TAB até que o sistema processe o retorno de elegibilidade</p>
                </div>
                
                <div class="image-container">
                    <img src="https://i.postimg.cc/G3DhxB4J/elegb1.png" alt="Tela de preenchimento da carteirinha">
                    <p class="image-caption">Tela de preenchimento do número da carteirinha no Tasy</p>
                </div>
                
                <div class="step">
                    <span class="step-number">5</span>
                    <strong>Aguarde a confirmação</strong>
                    <div class="success" style="margin-top: 15px;">
                        <strong>✓ RETORNO DE ELEGIBILIDADE ACEITA!</strong><br><br>
                        Quando esta mensagem aparecer, significa que os dados da carteirinha preenchidos no campo "TIPO DE IDENTIFICAÇÃO" já foram encaminhados ao convênio e o paciente está elegível para realizar os procedimentos.
                    </div>
                </div>
            </div>
            
            <div class="section">
                <h2 class="section-title">Como Imprimir a Elegibilidade</h2>
                
                <div class="step">
                    <span class="step-number">1</span>
                    <strong>Acesse o menu do OVERMIND</strong>
                    <p style="margin-top: 10px; padding-left: 15px;">Retorne ao site do OVERMIND que deve estar aberto em outra aba/janela</p>
                </div>
                
                <div class="step">
                    <span class="step-number">2</span>
                    <strong>Selecione a opção "ELEGIBILIDADE"</strong>
                    <p style="margin-top: 10px; padding-left: 15px;">No menu principal, localize e clique na opção ELEGIBILIDADE</p>
                </div>
                
                <div class="image-container">
                    <img src="https://i.postimg.cc/v8nHt147/elegb2.png" alt="Menu de elegibilidade">
                    <p class="image-caption">Menu do OVERMIND - Opção Elegibilidade</p>
                </div>
                
                <div class="step">
                    <span class="step-number">3</span>
                    <strong>Clique sobre a palavra "ELEGÍVEL"</strong>
                    <p style="margin-top: 10px; padding-left: 15px;">Na lista de elegibilidades processadas, clique sobre o status "ELEGÍVEL"</p>
                </div>
                
                <div class="image-container">
                    <img src="https://i.postimg.cc/66Z5f78f/elegb3.png" alt="Lista de elegibilidades">
                    <p class="image-caption">Lista de elegibilidades - Clique em "ELEGÍVEL"</p>
                </div>
                
                <div class="step">
                    <span class="step-number">4</span>
                    <strong>Visualize e imprima o documento</strong>
                    <p style="margin-top: 10px; padding-left: 15px;">O sistema direcionará para uma nova tela com a elegibilidade completa pronta para impressão</p>
                </div>
                
                <div class="image-container">
                    <img src="https://i.postimg.cc/RVfv5qKs/elegb4.png" alt="Documento de elegibilidade">
                    <p class="image-caption">Documento de elegibilidade pronto para impressão</p>
                </div>
                
                <div class="success" style="margin-top: 30px;">
                    <strong>🎉 Processo Concluído!</strong><br><br>
                    A elegibilidade foi validada e está disponível para impressão e anexação ao prontuário do paciente.
                </div>
            </div>
            
            <div class="section">
                <h2 class="section-title">Dicas Importantes</h2>
                <div class="highlight-box">
                    <h3>✓ Mantenha o OVERMIND aberto</h3>
                    <p>Sempre mantenha o site do OVERMIND aberto durante o atendimento para acessar rapidamente as elegibilidades geradas</p>
                </div>
                
                <div class="highlight-box">
                    <h3>✓ Verifique os dados da carteirinha</h3>
                    <p>Certifique-se de que o número da carteirinha está correto antes de pressionar TAB para evitar retrabalho</p>
                </div>
                
                <div class="highlight-box">
                    <h3>✓ Aguarde o processamento</h3>
                    <p>O retorno de elegibilidade pode levar alguns segundos. Aguarde a mensagem de confirmação antes de prosseguir</p>
                </div>
                
                <div class="highlight-box">
                    <h3>✓ Imprima e anexe ao prontuário</h3>
                    <p>Sempre imprima a elegibilidade e anexe à documentação do paciente para fins de auditoria e controle</p>
                </div>
            </div>
        </div>
        
        <div class="footer">
            <p>OVERMIND - Módulo Elegibilidade | Sistema Inteligente de Validação Automática</p>
        </div>
    </div>
</body>
</html>
