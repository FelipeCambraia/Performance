<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dashboard BDR - Especialista em Soluções SAP</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            color: #333;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        .header {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            padding: 20px;
            border-radius: 20px;
            box-shadow: 0 15px 35px rgba(0,0,0,0.1);
            margin-bottom: 20px;
            text-align: center;
            border: 1px solid rgba(255, 255, 255, 0.2);
        }

        .header h1 {
            color: #2c3e50;
            font-size: 2.5em;
            margin-bottom: 10px;
            background: linear-gradient(45deg, #667eea, #764ba2);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            text-shadow: 0 2px 4px rgba(0,0,0,0.1);
        }

        .header p {
            font-size: 1.1em;
            color: #666;
            margin-bottom: 15px;
        }

        .quick-stats {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-top: 15px;
        }

        .quick-stat {
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
            padding: 10px 20px;
            border-radius: 25px;
            font-size: 0.9em;
            font-weight: bold;
            box-shadow: 0 5px 15px rgba(102, 126, 234, 0.3);
        }

        .nav-tabs {
            display: flex;
            justify-content: center;
            margin-bottom: 20px;
            gap: 10px;
            flex-wrap: wrap;
        }

        .nav-tab {
            background: rgba(255, 255, 255, 0.9);
            backdrop-filter: blur(10px);
            border: none;
            padding: 15px 25px;
            border-radius: 15px;
            cursor: pointer;
            font-weight: bold;
            transition: all 0.3s ease;
            box-shadow: 0 5px 20px rgba(0,0,0,0.1);
            border: 1px solid rgba(255, 255, 255, 0.3);
        }

        .nav-tab.active {
            background: linear-gradient(45deg, #667eea, #764ba2);
            color: white;
            transform: translateY(-3px);
            box-shadow: 0 10px 30px rgba(102, 126, 234, 0.4);
        }

        .nav-tab:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(0,0,0,0.15);
        }

        .tab-content {
            display: none;
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            padding: 30px;
            border-radius: 20px;
            box-shadow: 0 15px 35px rgba(0,0,0,0.1);
            margin-bottom: 20px;
            border: 1px solid rgba(255, 255, 255, 0.2);
        }

        .tab-content.active {
            display: block;
            animation: fadeIn 0.5s ease-in-out;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .cards-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }

        .card {
            background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
            padding: 25px;
            border-radius: 15px;
            border-left: 5px solid #667eea;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(0,0,0,0.05);
        }

        .card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
        }

        .card h3 {
            color: #2c3e50;
            margin-bottom: 15px;
            font-size: 1.3em;
        }

        .priorities {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 15px;
            margin-bottom: 20px;
        }

        .priority-card {
            padding: 20px;
            border-radius: 15px;
            text-align: center;
            color: white;
            font-weight: bold;
            transition: transform 0.3s ease;
            box-shadow: 0 5px 20px rgba(0,0,0,0.2);
        }

        .priority-card:hover {
            transform: translateY(-3px);
        }

        .priority-max {
            background: linear-gradient(135deg, #e74c3c, #c0392b);
        }

        .priority-high {
            background: linear-gradient(135deg, #f39c12, #d68910);
        }

        .priority-medium {
            background: linear-gradient(135deg, #27ae60, #229954);
        }

        .daily-tracker {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            padding: 25px;
            border-radius: 20px;
            box-shadow: 0 15px 35px rgba(0,0,0,0.1);
            border: 1px solid rgba(255, 255, 255, 0.2);
        }

        .metric-box {
            display: inline-block;
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
            padding: 15px 25px;
            border-radius: 12px;
            margin: 5px;
            font-weight: bold;
            text-align: center;
            min-width: 150px;
            box-shadow: 0 5px 15px rgba(102, 126, 234, 0.3);
            transition: transform 0.3s ease;
        }

        .metric-box:hover {
            transform: translateY(-2px);
        }

        .metric-input {
            width: 60px;
            padding: 8px;
            border: 2px solid rgba(255, 255, 255, 0.3);
            border-radius: 8px;
            text-align: center;
            margin-left: 10px;
            background: rgba(255, 255, 255, 0.2);
            color: white;
            font-weight: bold;
        }

        .metric-input::placeholder {
            color: rgba(255, 255, 255, 0.7);
        }

        .solution-comparison {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(400px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }

        .solution-card {
            background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
            padding: 25px;
            border-radius: 15px;
            border-top: 5px solid #667eea;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(0,0,0,0.05);
        }

        .solution-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
        }

        .solution-card.invoice {
            border-top-color: #e74c3c;
        }

        .solution-card.roit {
            border-top-color: #27ae60;
        }

        .personas-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 20px;
        }

        .persona-card {
            background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
            padding: 20px;
            border-radius: 15px;
            border-left: 5px solid #667eea;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(0,0,0,0.05);
        }

        .persona-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 30px rgba(0,0,0,0.1);
        }

        .weekly-schedule {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 15px;
            margin-bottom: 30px;
        }

        .week-card {
            background: linear-gradient(135deg, #f8f9fa 0%, #e9ecef 100%);
            padding: 20px;
            border-radius: 15px;
            text-align: center;
            border-top: 5px solid #667eea;
            transition: all 0.3s ease;
            box-shadow: 0 5px 15px rgba(0,0,0,0.05);
        }

        .week-card:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 25px rgba(0,0,0,0.1);
        }

        .checklist-item {
            display: flex;
            align-items: center;
            padding: 12px;
            margin-bottom: 8px;
            border-radius: 8px;
            transition: all 0.3s ease;
            background: rgba(102, 126, 234, 0.02);
            border: 1px solid rgba(102, 126, 234, 0.1);
        }

        .checklist-item:hover {
            background: rgba(102, 126, 234, 0.05);
            transform: translateX(5px);
        }

        .checklist-item input[type="checkbox"] {
            margin-right: 12px;
            transform: scale(1.2);
            accent-color: #667eea;
        }

        .btn {
            background: linear-gradient(45deg, #667eea, #764ba2);
            color: white;
            padding: 12px 25px;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            font-weight: bold;
            transition: all 0.3s ease;
            margin: 5px;
            box-shadow: 0 5px 15px rgba(102, 126, 234, 0.3);
        }

        .btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(102, 126, 234, 0.4);
        }

        .btn:active {
            transform: translateY(0);
        }

        .progress-bar {
            background: #e9ecef;
            height: 25px;
            border-radius: 15px;
            overflow: hidden;
            margin: 20px 0;
            box-shadow: inset 0 2px 5px rgba(0,0,0,0.1);
        }

        .progress-fill {
            background: linear-gradient(45deg, #667eea, #764ba2);
            height: 100%;
            transition: width 0.5s ease;
            border-radius: 15px;
            position: relative;
        }

        .progress-fill::after {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
            animation: shine 2s infinite;
        }

        @keyframes shine {
            0% { transform: translateX(-100%); }
            100% { transform: translateX(100%); }
        }

        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 15px;
            margin-bottom: 30px;
        }

        .stat-card {
            background: linear-gradient(135deg, #667eea, #764ba2);
            color: white;
            padding: 20px;
            border-radius: 15px;
            text-align: center;
            transition: all 0.3s ease;
            box-shadow: 0 5px 20px rgba(102, 126, 234, 0.3);
        }

        .stat-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 30px rgba(102, 126, 234, 0.4);
        }

        .stat-number {
            font-size: 2.2em;
            font-weight: bold;
            margin-bottom: 5px;
        }

        .time-display {
            position: fixed;
            top: 20px;
            right: 20px;
            background: rgba(255, 255, 255, 0.9);
            backdrop-filter: blur(10px);
            padding: 10px 20px;
            border-radius: 15px;
            font-weight: bold;
            color: #2c3e50;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            border: 1px solid rgba(255, 255, 255, 0.3);
        }

        .notification {
            position: fixed;
            top: 20px;
            left: 50%;
            transform: translateX(-50%);
            background: linear-gradient(45deg, #27ae60, #229954);
            color: white;
            padding: 15px 25px;
            border-radius: 10px;
            font-weight: bold;
            box-shadow: 0 5px 20px rgba(39, 174, 96, 0.3);
            opacity: 0;
            transition: all 0.3s ease;
            z-index: 1000;
        }

        .notification.show {
            opacity: 1;
            transform: translateX(-50%) translateY(0);
        }

        @media (max-width: 768px) {
            .solution-comparison {
                grid-template-columns: 1fr;
            }
            
            .weekly-schedule {
                grid-template-columns: repeat(2, 1fr);
            }
            
            .priorities {
                grid-template-columns: 1fr;
            }

            .quick-stats {
                flex-direction: column;
                align-items: center;
            }

            .nav-tabs {
                flex-direction: column;
                align-items: center;
            }

            .nav-tab {
                width: 100%;
                max-width: 200px;
            }

            .time-display {
                position: relative;
                top: 0;
                right: 0;
                margin-bottom: 20px;
            }
        }
    </style>
</head>
<body>
    <div class="time-display" id="timeDisplay"></div>
    <div class="notification" id="notification"></div>

    <div class="container">
        <div class="header">
            <h1>Dashboard BDR - Especialista em Soluções SAP</h1>
            <p>Plano de 30 dias para InvoiceToPay e ROIT for SAP</p>
            <div class="quick-stats">
                <div class="quick-stat">🎯 Meta: 400 contatos/mês</div>
                <div class="quick-stat">📊 Pipeline: R$ 3-4M</div>
                <div class="quick-stat">🚀 SQLs: 6-8/mês</div>
            </div>
        </div>

        <div class="nav-tabs">
            <button class="nav-tab active" onclick="showTab('overview')">📊 Visão Geral</button>
            <button class="nav-tab" onclick="showTab('solutions')">💡 Soluções</button>
            <button class="nav-tab" onclick="showTab('prospects')">🎯 Prospecção</button>
            <button class="nav-tab" onclick="showTab('daily')">📅 Controle Diário</button>
            <button class="nav-tab" onclick="showTab('scripts')">💬 Scripts</button>
        </div>

        <div id="overview" class="tab-content active">
            <div class="stats-grid">
                <div class="stat-card">
                    <div class="stat-number">400</div>
                    <div>Contatos/Mês</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number">6-8</div>
                    <div>SQLs/Mês</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number">10</div>
                    <div>Reuniões/Mês</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number">R$ 3-4M</div>
                    <div>Pipeline/Mês</div>
                </div>
            </div>

            <div class="priorities">
                <div class="priority-card priority-max">
                    <h3>🔴 PRIORIDADE MÁXIMA</h3>
                    <p>Faturamento R$ 1B+ com SAP</p>
                    <p>Farmacêutica, Energia, Financeiro</p>
                </div>
                <div class="priority-card priority-high">
                    <h3>🟡 PRIORIDADE ALTA</h3>
                    <p>Faturamento R$ 500M-1B</p>
                    <p>Empresas em crescimento</p>
                </div>
                <div class="priority-card priority-medium">
                    <h3>🟢 PRIORIDADE MÉDIA</h3>
                    <p>Faturamento R$ 300-500M</p>
                    <p>ERP robusto</p>
                </div>
            </div>

            <div class="weekly-schedule">
                <div class="week-card">
                    <h3>Semana 1</h3>
                    <p><strong>90 contatos</strong></p>
                    <p>1 SQL | 2 Reuniões</p>
                    <p>Setup e início</p>
                </div>
                <div class="week-card">
                    <h3>Semana 2</h3>
                    <p><strong>90 contatos</strong></p>
                    <p>1-2 SQLs | 2 Reuniões</p>
                    <p>Otimização</p>
                </div>
                <div class="week-card">
                    <h3>Semana 3</h3>
                    <p><strong>110 contatos</strong></p>
                    <p>2 SQLs | 3 Reuniões</p>
                    <p>Aceleração</p>
                </div>
                <div class="week-card">
                    <h3>Semana 4</h3>
                    <p><strong>110 contatos</strong></p>
                    <p>2-3 SQLs | 3 Reuniões</p>
                    <p>Conversão</p>
                </div>
            </div>
        </div>

        <div id="solutions" class="tab-content">
            <div class="solution-comparison">
                <div class="solution-card invoice">
                    <h3>💰 InvoiceToPay</h3>
                    <p><strong>Foco:</strong> Automação de pagamento de notas fiscais</p>
                    <p><strong>ERPs:</strong> SAP, Oracle, Microsoft, Totvs, Outros</p>
                    <p><strong>Clientes:</strong> Empresas de médio a grande porte</p>
                    <p><strong>Personas:</strong></p>
                    <ul>
                        <li>• CFO / Diretor Financeiro</li>
                        <li>• Gerente de Contas a Pagar</li>
                        <li>• Coordenador Financeiro</li>
                    </ul>
                    <p><strong>Pain Points:</strong></p>
                    <ul>
                        <li>• Processos manuais demorados</li>
                        <li>• Falta de controle e visibilidade</li>
                        <li>• Erros em pagamentos</li>
                        <li>• Compliance e auditoria</li>
                    </ul>
                </div>

                <div class="solution-card roit">
                    <h3>⚖️ ROIT for SAP</h3>
                    <p><strong>Foco:</strong> Adequação do SAP para Reforma Tributária</p>
                    <p><strong>ERPs:</strong> Exclusivamente SAP</p>
                    <p><strong>Clientes:</strong> Grandes corporações com SAP</p>
                    <p><strong>Personas:</strong></p>
                    <ul>
                        <li>• Consultor SAP Fiscal</li>
                        <li>• CTO / Diretor de TI</li>
                        <li>• Gerente de TI Fiscal</li>
                    </ul>
                    <p><strong>Pain Points:</strong></p>
                    <ul>
                        <li>• Complexidade da Reforma Tributária</li>
                        <li>• Pressão por adequações rápidas</li>
                        <li>• Risco de multas por não conformidade</li>
                        <li>• Falta de recursos especializados</li>
                    </ul>
                </div>
            </div>

            <div class="cards-grid">
                <div class="card">
                    <h3>🎯 Critérios de Qualificação</h3>
                    <p><strong>Budget:</strong> R$ 100K+ para adequações</p>
                    <p><strong>Authority:</strong> CTO, Diretor TI, Gerente SAP</p>
                    <p><strong>Need:</strong> Adequação fiscal, automação</p>
                    <p><strong>Timeline:</strong> 3-12 meses</p>
                    <p><strong>Competition:</strong> Big 4, consultores SAP</p>
                </div>

                <div class="card">
                    <h3>📊 Benchmarks por Canal</h3>
                    <p><strong>LinkedIn:</strong> 45-60% abertura, 5-10% resposta</p>
                    <p><strong>Email:</strong> 25-35% abertura, 1-5% resposta</p>
                    <p><strong>WhatsApp:</strong> 60-80% abertura, 15-25% resposta</p>
                </div>
            </div>
        </div>

        <div id="prospects" class="tab-content">
            <div class="cards-grid">
                <div class="card">
                    <h3>🏢 Lista A - Prioridade Máxima (100 contas)</h3>
                    <p><strong>Faturamento:</strong> R$ 1B+</p>
                    <p><strong>Setores:</strong> Farmacêutico, Energia, Financeiro</p>
                    <p><strong>Exemplos:</strong> Petrobras, Vale, Itaú, Novartis</p>
                    <p><strong>Critério:</strong> SAP confirmado</p>
                </div>

                <div class="card">
                    <h3>🏭 Lista B - Prioridade Alta (150 contas)</h3>
                    <p><strong>Faturamento:</strong> R$ 500M-1B</p>
                    <p><strong>Setores:</strong> Indústria, Varejo, Tecnologia</p>
                    <p><strong>Funcionários:</strong> 1000+</p>
                    <p><strong>Critério:</strong> ERP robusto</p>
                </div>

                <div class="card">
                    <h3>🚀 Lista C - Prioridade Média (150 contas)</h3>
                    <p><strong>Faturamento:</strong> R$ 300-500M</p>
                    <p><strong>Funcionários:</strong> 500-1000</p>
                    <p><strong>Critério:</strong> Empresas em expansão</p>
                </div>

                <div class="card">
                    <h3>🔥 Sinais de Timing Ideal</h3>
                    <p><strong>Quentes:</strong></p>
                    <ul>
                        <li>• Posts sobre Reforma Tributária</li>
                        <li>• Job postings SAP Fiscal</li>
                        <li>• Mudanças na liderança</li>
                    </ul>
                    <p><strong>Mornos:</strong></p>
                    <ul>
                        <li>• Eventos fiscais/ERP</li>
                        <li>• Contratação de consultores</li>
                    </ul>
                </div>
            </div>

            <div class="personas-grid">
                <div class="persona-card">
                    <h3>👨‍💼 Decisor Técnico</h3>
                    <p><strong>Cargo:</strong> Consultor SAP Fiscal</p>
                    <p><strong>Idade:</strong> 38-52 anos</p>
                    <p><strong>Experiência:</strong> 12-25 anos</p>
                    <p><strong>Linguagem:</strong> Técnica, específica</p>
                </div>

                <div class="persona-card">
                    <h3>👨‍💻 Decisor Executivo</h3>
                    <p><strong>Cargo:</strong> CTO, Diretor TI</p>
                    <p><strong>Idade:</strong> 42-55 anos</p>
                    <p><strong>Experiência:</strong> 15+ anos</p>
                    <p><strong>Linguagem:</strong> ROI, eficiência</p>
                </div>

                <div class="persona-card">
                    <h3>👨‍🔧 Influenciador</h3>
                    <p><strong>Cargo:</strong> Analista SAP Sênior</p>
                    <p><strong>Idade:</strong> 28-38 anos</p>
                    <p><strong>Experiência:</strong> 5-12 anos</p>
                    <p><strong>Linguagem:</strong> Prática, operacional</p>
                </div>
            </div>
        </div>

        <div id="daily" class="tab-content">
            <div class="daily-tracker">
                <h2>📅 Controle Diário</h2>
                
                <div class="cards-grid">
                    <div class="card">
                        <h3>🌅 Manhã (4 horas)</h3>
                        <div class="checklist-item">
                            <input type="checkbox" id="morning1">
                            <label for="morning1">1h: Planejamento e research</label>
                        </div>
                        <div class="checklist-item">
                            <input type="checkbox" id="morning2">
                            <label for="morning2">1.5h: LinkedIn connections (8 novos)</label>
                        </div>
                        <div class="checklist-item">
                            <input type="checkbox" id="morning3">
                            <label for="morning3">1.5h: Emails personalizados (13)</label>
                        </div>
                    </div>

                    <div class="card">
                        <h3>🌆 Tarde (4 horas)</h3>
                        <div class="checklist-item">
                            <input type="checkbox" id="afternoon1">
                            <label for="afternoon1">1h: Follow-ups diversos</label>
                        </div>
                        <div class="checklist-item">
                            <input type="checkbox" id="afternoon2">
                            <label for="afternoon2">1.5h: Prospecção ativa (7 LinkedIn)</label>
                        </div>
                        <div class="checklist-item">
                            <input type="checkbox" id="afternoon3">
                            <label for="afternoon3">1h: WhatsApp (8) + social selling</label>
                        </div>
                        <div class="checklist-item">
                            <input type="checkbox" id="afternoon4">
                            <label for="afternoon4">0.5h: Atualização CRM</label>
                        </div>
                    </div>
                </div>

                <div class="metric-box">
                    LinkedIn: <input type="number" class="metric-input" value="0" max="15" placeholder="0"> / 15
                </div>
                <div class="metric-box">
                    Emails: <input type="number" class="metric-input" value="0" max="25" placeholder="0"> /
