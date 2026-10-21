# ReVeste — Plataforma de Venda, Revenda e Marketplace de Moda

> **Documento de Referência:** Documento de Requisitos de Software (DRS) — Versão 1.0 (Outubro de 2026)  
> **Equipe de Desenvolvimento / Autores:**  
> Vitor Avelar • Gabriel Andrade • Rafael Santana • Bruno dos Santos • João Gabriel • Gustavo Giovani Silva

---

## 🌟 Visão Geral do Projeto

A **ReVeste** é uma plataforma e marketplace de moda circular e consciente criada para integrar a venda de peças novas autorais, a revenda curada de brechós parceiros e o desapego direto por clientes cadastrados (C2C).

O sistema resolve os principais desafios operacionais descritos no DRS:
1. **Controle e Sincronização Automática de Estoque** (via arquivos de planilha/CSV e baixa automática no fechamento de compras).
2. **Divisão Transparente de Comissões (20% ReVeste / 80% Vendedor)** com auditoria visual de repasses.
3. **Portal do Cliente "Quero Revender"** para incentivar a moda circular.
4. **Organização de Pedidos Nacionais e Internacionais** com transportadoras específicas e cálculo de frete.
5. **Rastreamento de Entregas em Tempo Real** com timeline de movimentação e códigos de rastreio.
6. **Segurança com Autenticação em Dois Fatores (2FA)** e controle de acesso baseado em perfis (RBAC).
7. **Central Interativa do DRS** com suíte executável de casos de teste de aceite (CT-01 a CT-08).

---

## 🚀 Como Executar o Website

O projeto foi construído para funcionar de maneira imediata, sem necessidade de build complexo.

### Opção 1: Abertura Direta no Navegador
Basta dar dois cliques no arquivo:
```
C:\Users\EBB2NL116\reveste-platform\index.html
```
Ou abrir no navegador (Google Chrome, Microsoft Edge, Firefox).

### Opção 2: Servidor Local via Node.js
Se preferir rodar em um servidor web HTTP local:
```powershell
cd C:\Users\EBB2NL116\reveste-platform
npx serve
```
Ou pelo PowerShell:
```powershell
Start-Process "C:\Users\EBB2NL116\reveste-platform\index.html"
```

---

## 🗺️ Mapeamento Completo de Requisitos do DRS

| Requisito | Nome | Implementação na Plataforma ReVeste |
|---|---|---|
| **RF-01** | Manter produtos | Catálogo interativo com filtros por categoria, condição, cores, tamanhos e gestão no painel admin. |
| **RF-02** | Gerenciar estoque | Baixa automática do estoque após cada compra; alerta visual de estoque crítico. |
| **RF-03** | Integrar planilha de estoque | Módulo no painel administrativo para importar planilhas CSV (`sample-estoque.csv`), validar e sincronizar. |
| **RF-04** | Manter usuários | Cadastro de contas com atribuição de perfis (Cliente, Parceiro, Admin, Estoque). |
| **RF-05** | Registrar pedidos | Fluxo de checkout com itens, quantidades, endereço, frete e dados do comprador. |
| **RF-06** | Acompanhar entrega | Aba "Rastreamento" com busca por código (`BR938210492BR`, `DHL74829104EU`) e timeline. |
| **RF-07** | Calcular divisão da venda | Painel do Parceiro e modal de produto com transparência de 80% parceiro / 20% ReVeste. |
| **RF-08** | Permitir revenda | Aba "Quero Revender" com envio de peças pelo cliente e simulação de ganhos. |
| **RF-09** | Pedidos nacionais e internacionais | Classificação automática pelo destino, com fretes e transportadoras dedicadas. |
| **RF-10** | Consultar pedidos | Extrato de pedidos com filtros e detalhamento para cliente e administrador. |
| **RF-11** | Administrar acessos | Controle de acesso por perfil (RBAC) com bloqueio de funções administrativas para clientes. |
| **RF-12** | Consultar relatórios | Métricas consolidadas de vendas, repasses, taxas da plataforma e inventário. |

### Requisitos Não Funcionais (RNF)
- **RNF-01 (Segurança):** Simulação de 2FA obrigatório com token de 6 dígitos no fechamento da compra.
- **RNF-02 (Usabilidade):** Design moderno, tipografia editorial (Playfair Display + Plus Jakarta Sans) e paleta sofisticada em Verde Esmeralda (Emerald Green) e Bege/Tan/Areia.
- **RNF-03 (Compatibilidade):** Layout 100% responsivo para smartphones, tablets e desktops.
- **RNF-04 (Organização):** Pedidos nacionais e internacionais distinguidos com tags visuais e transportadoras.
- **RNF-05 (Integridade):** Validação matemática estrita de soma de parcelas (80% + 20% = 100%) e controle de estoque.
- **RNF-06 (Privacidade):** Acesso a relatórios segmentado por perfil.
- **RNF-07 (Rastreabilidade):** Histórico de sincronizações de planilha e logs de movimentação de frete.

---

## 🧪 Casos de Teste de Aceite Interativos (CT-01 a CT-08)

Na aba **Central DRS**, você pode clicar em **"Executar Todos os Testes"** para validar em tempo real:
- **CT-01:** Sincronização e atualização de estoque via planilha.
- **CT-02:** Bloqueio de compra ao tentar solicitar quantidade acima do estoque.
- **CT-03:** Divisão transparente de valores com base configurada.
- **CT-04:** Validação matemática dos 20% de comissão e 80% de repasse.
- **CT-05:** Disponibilidade de rastreamento com código e eventos físicos.
- **CT-06:** Exigência de 2FA no fluxo de compra.
- **CT-07:** Responsividade em celulares e telas pequenas.
- **CT-08:** Bloqueio de acesso administrativo para perfis de cliente (RBAC).

---

## 🖼️ Gerenciamento de Imagens & Fallbacks Vetoriais

Para garantir que o site nunca apresente caixas ou divs vazias:
1. **Fallback Automático Vetorial SVG:** Cada peça possui um gerador de ilustrações vetoriais em tons Esmeralda e Tan que é acionado automaticamente em caso de falha de conexão ou ausência de link, exibindo o ícone da categoria (*Casacos, Vestidos, Bolsas, etc.*), nome da peça, cor e selo de curadoria.
2. **Alteração de Imagem pelo Administrador:**
   - No **Painel Administrativo & Estoque**, na tabela de inventário, clique no botão **`[🖼️ Imagem]`** ou na miniatura do produto.
   - No catálogo ou no modal do produto, o administrador tem um botão direto para editar a foto.
   - São fornecidas três opções simples:
     - **Carregar do Computador:** selecione qualquer imagem local (*.jpg, *.png, *.webp*) para conversão direta em Data URL.
     - **URL Personalizada:** cole qualquer link da web.
     - **Galeria de Presets:** escolha com 1 clique entre 12 opções prontas de moda curada ou a ilustração vetorial SVG.
   - As alterações são salvas instantaneamente no navegador (`localStorage`).

---

## 📁 Estrutura de Arquivos

```
reveste-platform/
│
├── index.html              # Interface principal completa e responsiva
├── styles.css              # Sistema de design, paleta de cores e animações
├── app.js                  # Lógica interativa, dados, regras de negócio e testes
├── sample-estoque.csv      # Planilha CSV pronta para teste de importação de estoque
└── README.md               # Esta documentação
```

---

*ReVeste — Moda que se reinventa, veste e ReVeste.*
