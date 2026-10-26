# ReVeste — Plataforma de Venda, Revenda e Marketplace de Moda

> **Documento de Referência:** Documento de Requisitos de Software (DRS) — Versão 1.0 (Outubro de 2026)  
> **Desenvolvimento do site: Develup**  
> Vitor Avelar • Gabriel Andrade • Rafael Santana • Bruno dos Santos • João Gabriel • Gustavo Giovani Silva

---

## 🌟 Visão Geral do Projeto

A **ReVeste** é um projeto de plataforma e marketplace de moda circular e consciente criada para integrar a venda de peças novas autorais, a revenda curada de brechós parceiros e o desapego direto por clientes cadastrados (C2C).

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
./index.html
```
Ou abrir no navegador (Google Chrome, Microsoft Edge, Firefox).

### Opção 2: Servidor Local via Node.js
Se preferir rodar em um servidor web HTTP local:
```powershell
cd reveste-professional
npx serve
```
Ou pelo PowerShell:
```powershell
Start-Process "./index.html"
```

---

## 🗺️ Mapeamento Completo de Requisitos do DRS

| Requisito | Nome | Implementação na Plataforma ReVeste |
|---|---|---|
| **RF-01** | Manter produtos | Catálogo interativo com filtros por categoria, condição, cores, tamanhos e gestão no painel admin. |
| **RF-02** | Gerenciar estoque | Baixa automática do estoque após cada compra; alerta visual de estoque crítico. |
| **RF-03** | Integrar planilha de estoque | Módulo no painel administrativo para importar planilhas CSV (`sample-estoque.xlsx`), validar e sincronizar. |
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

## 🧪 Testes de aceite

Os testes de aceite e a especificação técnica continuam pertencendo ao material interno de desenvolvimento; eles não são exibidos como páginas da navegação pública do marketplace.

---

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
├── sample-estoque.xlsx      # Planilha CSV pronta para teste de importação de estoque
└── README.md               # Esta documentação
```

---

*ReVeste — Moda que se reinventa, veste e ReVeste.*


## Desenvolvimento
O site da ReVeste foi desenvolvido pela **Develup**. A Develup é a equipe responsável pela criação da experiência web e não faz parte da equipe interna da ReVeste.


## Atualização de interface — outubro de 2026

- Adicionado o formulário **Criar conta** para cadastrar perfis de cliente de demonstração. Os perfis são salvos no `localStorage` deste navegador; este formulário não é autenticação de produção e não armazena a senha.
- Substituído o retrato usado como logotipo por um símbolo SVG próprio da ReVeste, inspirado em cabide e moda circular.
- A página pública não exibe mais a seção de apresentação da equipe de desenvolvimento.


## Melhorias de experiência — edição profissional

- Alerta de preço fora da faixa: o sistema compara o preço sugerido com a mediana dos produtos ativos da mesma categoria (limite de alerta: maior entre R$ 500 e 2,5× a mediana).
- O alerta explica que preços muito altos podem reduzir a procura e oferece duas escolhas: revisar o valor ou publicar mesmo assim.
- A calculadora de repasse 80/20 e a orientação de preço atualizam-se ao mudar o valor ou a categoria.
- Foram refinados estados de foco, microinterações, animações de entrada e hover, responsividade do alerta e suporte a `prefers-reduced-motion`.

**Observação:** a referência de preço é uma heurística local baseada no catálogo de demonstração, não uma avaliação de mercado nem garantia de venda. O protótipo mantém dados no navegador e não substitui autenticação, pagamentos ou armazenamento de produção no servidor.


## Planilha de estoque profissional

O arquivo `sample-estoque.xlsx` substitui a planilha de demonstração simples e inclui:
- Aba **Estoque** com tabela formatada, filtros, cabeçalhos fixos, validação de dados e sinalização de estoque baixo.
- Aba **Resumo** com indicadores automáticos de produtos, unidades e valor total em estoque.
- Aba **Como usar** com instruções para edição e importação.
- Colunas de ID e SKU, categoria, tamanho, cor, preço, quantidade, estoque mínimo, status, tipo de venda, vendedor e valor total por item.

No painel administrativo, importe o arquivo `.xlsx`; a plataforma já aceita planilhas Excel por meio do leitor XLSX incluído no site.
