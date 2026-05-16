# 📱 SoulMove — Case Study & Arquitetura do Sistema

<div align="center">
  <a href="https://sprint-front-fiap.vercel.app/" target="_blank">
    <img src="https://img.shields.io/badge/🌐_Acessar_Site_demonstrativo_do_Projeto-005571?style=for-the-badge" alt="Acessar Site">
  </a>
</div>


## 📄 Visão Geral do Projeto
O **SoulMove** é uma solução de mobilidade sustentável desenvolvida para o desafio da **SoulUp**. O ecossistema transforma deslocamentos diários em transporte público em **Pontos Ecoa** (recompensas), incentivando escolhas ecológicas e gerando dados de alto valor para o mercado ESG, tudo de forma gamificada e segura.

---

## 🏗️ 1. Arquitetura do Sistema (End-to-End)
O fluxo foi desenhado para ser leve no lado do cliente e robusto no backend, garantindo escalabilidade:

1. **Client (Mobile):** O usuário inicia a jornada e um *Background Service* ativo coleta dados de GPS de forma otimizada.
2. **API Gateway & Backend:** O aplicativo envia checkpoints em tempo real para a nossa API.
3. **Integração Externa:** O backend cruza instantaneamente os dados de geolocalização recebidos com a API oficial da **SPTrans (Olho Vivo)** para monitorar as linhas e frotas de ônibus em tempo real.
4. **Event Queue & Database:** As mensagens de validação passam por uma fila de eventos antes de persistirem no banco de dados (Jornadas, Pontos, Rankings).

---

## 🛡️ 2. Motor de Validação & Inteligência Anti-Fraude
Para garantir a justiça do sistema e mitigar fraudes em sistemas de recompensa digitais, o **SoulMove Engine** calcula um **Score de Confiabilidade** baseado em critérios analíticos rigorosos:

* **Critérios Positivos:** Proximidade real com as linhas de ônibus monitoradas, tempo mínimo em rota e velocidade compatível com o modal de transporte.
* **Critérios Negativos:** Usuário parado por tempo excessivo, pulos incongruentes de GPS (indicação de *GPS Spoofing*), movimentos impossíveis ou velocidades incompatíveis com a rota urbana.

O motor classifica a jornada em níveis de confiança (Alto, Médio ou Baixo), aplicando travas de segurança automatizadas e impedindo simulações de trajetos.

---

## 📊 3. Modelo de Pontuação Dinâmico
A engenharia por trás do cálculo de recompensas utiliza múltiplos fatores ponderados para valorizar o engajamento real:

$$\text{Pontos} = \text{Distância (km)} \times \text{Impacto } (CO_2 \text{ evitado}) \times \text{Score de Confiabilidade} \times \text{Bônus (Multiplicadores)}$$

* **Multiplicadores Estratégicos:** Frequência semanal de uso (até 1,2x), deslocamentos em horários de pico (até 1,3x) e consistência histórica do usuário (até 1,2x).

---

## 🌍 4. Valor Gerado (Ecossistema Tripartite)

| Para o Usuário | Para a SoulUp | Para o Planeta |
| :--- | :--- | :--- |
| • Recompensa por escolhas limpas<br>• Gamificação motivadora<br>• Resgate de benefícios reais | • Aumento de retenção e recorrência<br>• Dados comportamentais estruturados<br>• Diferenciação no mercado ESG | • Redução de emissão de $CO_2$<br>• Estímulo ao transporte coletivo<br>• Cidades mais inteligentes |

---

## 🛠️ Tecnologias Utilizadas no Projeto
* **Backend & APIs:** Node.js, FastAPI (Python)
* **Processamento de Dados:** Pandas, NumPy
* **Bancos de Dados & Modelagem:** Oracle Data Modeler, MySQL / PostgreSQL
* **Ferramentas de Design:** Figma (Prototipação de Alta Fidelidade)

---

<p align="center">
  <a href="./README.md">⬅️ Voltar para o perfil principal</a>
</p>
