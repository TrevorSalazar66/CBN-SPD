# CBN-SPD: Roadmap e Registro de Tarefas

> **Projeto:** CBN-SPD (Cataclysm: Bright Nights com melhorias e mecânicas portadas do CDDA)  
> **Fork Oficial:** [TrevorSalazar66/CBN-SPD](https://github.com/TrevorSalazar66/CBN-SPD)  
> **Upstream CBN:** [cataclysmbn/Cataclysm-BN](https://github.com/cataclysmbn/Cataclysm-BN)  
> **Referência CDDA Local:** `/home/ultratelecom/Documentos/Prjts/cdda` ([CleverRaven/Cataclysm-DDA](https://github.com/CleverRaven/Cataclysm-DDA))  
> **Data de Atualização:** 20/10/2026  

---

## 📌 Situação Atual do Projeto

O projeto foi estruturado com base no **Cataclysm: Bright Nights (CBN)** devido à sua melhor jogabilidade para dispositivos móveis, maior fluidez, menor microgerenciamento de inventário e desempenho superior na CPU.

O repositório local está conectado ao fork oficial no GitHub (`TrevorSalazar66/CBN-SPD`) e configurado com o upstream para puxar atualizações futuras.

---

## ✅ O Que Foi Feito Recentemente

1. **Configuração do Repositório e Remotes:**
   - [x] Clone e conexão ao repositório [TrevorSalazar66/CBN-SPD](https://github.com/TrevorSalazar66/CBN-SPD).
   - [x] Configuração dos remotes `origin` (fork pessoal) e `upstream` (Bright Nights oficial).
   - [x] Ajuste da identidade do autor git local.

2. **Port e Adaptação das Novas Facções do CDDA para o CBN:**
   - [x] Importadas **9 novas facções** em `data/json/npcs/factions.json`:
     - `exodii` (The Exodii - ciborgues interdimensionais)
     - `balthazar_fac` (Balthazar - robôs/mercenários em bunker)
     - `isolated_artisans` (Artesãos rurais)
     - `the_great_library` (A Grande Biblioteca - acadêmicos com moeda `FlatCoin`)
     - `GM_militia_faction` (Grey Moose Militia)
     - `fisherman_family` (Família de pescadores)
     - `slaves` (Indivíduos escravizados)
     - `prisoners` (Prisioneiros foragidos)
     - `robofac_auxiliaries_chop_shop` (Mercenários do Hub 01)
   - [x] Importadas e adaptadas **3 facções de monstros** em `data/json/monster_factions.json`:
     - `exodii`, `balthazar`, `isolated_artisans`
   - [x] Adicionados **29 epílogos de facções** em `data/json/snippets/epilogue_factions.json`.
   - [x] **Adaptações de compatibilidade executadas:**
     - Substituição do complexo `fac_food_supply` (calorias/vitaminas do CDDA) por `food_supply` inteiro aceito pelo CBN.
     - Remoção de campos incompatíveis com o parser do CBN (ex: `price_rules`).
     - Validação completa com `./build-scripts/lint-json.sh`.
     - Commit atômico gerado: `feat(faction): port CDDA factions and epilogues to CBN`.

3. **Análise Comparativa de Mecânicas (CBMs & Mutações):**
   - [x] **CBMs:** Comparados os sistemas de instalação manual, autodoc, anestesia geral/local, slots por membro e o serviço de cirurgia de Rubik (Exodii).
   - [x] **Mutações:** Comparados os modelos de anatomia dinâmica (CDDA: 883 mutações) vs clássica (CBN: 575 mutações), e o sistema de "Primers + Catalisadores" vs "Soros/Mutagênicos Diretos".

---

## 📋 Próximas Tarefas em Sequência

### Fase 1: Atualização e Adaptação de Mutações

- [ ] **1.1 Novas Categorias de Mutação:**
  - Portar para o CBN as categorias criadas no CDDA:
    - `BATRACHIAN` (Anfíbios / Rãs)
    - `CHIROPTERAN` (Morcegos)
    - `CRUSTACEAN` (Crustáceos / Caranguejos)
    - `GASTROPOD` (Caracóis / Lesmas)
    - `INTERSTICE` (Nether / Dimensional)
    - `HUMAN` (Aprimoramento humano pós-limiar)
- [ ] **1.2 Criação dos Mutagênicos e Soros:**
  - Criar as receitas e itens correspondentes (mutagênicos simples e soros de injeção direta) sem a complexidade de primers/metabolismo do CDDA.
- [ ] **1.3 Port de Mutações Chave:**
  - Portar mutações temáticas dessas linhagens adaptando traços de anatomia para a estrutura estável de 12 membros do CBN.
- [ ] **1.4 Validação:**
  - Rodar o linter de JSON (`./build-scripts/lint-json.sh`) e commitar as alterações.
Vamos

---

### Fase 2: Análise e Atualização da Parte de Itens

- [ ] **2.1 Auditoria Comparativa de Itens:**
  - Mapear novos tipos de itens adicionados ao CDDA (armas, armaduras, ferramentas, eletrônicos, novos materiais).
- [ ] **2.2 Filtragem e Seleção:**
  - Selecionar itens que agregam valor e mantêm a filosofia de ação/sobrevivência do CBN sem adicionar tédio desnecessário.
- [ ] **2.3 Port das Definições e Receitas:**
  - Trazer JSONs de itens, grupos de drop (`item_groups`) e receitas de fabricação.
- [ ] **2.4 Validação:**
  - Testar integridade dos dados e commitar.

---

### Fase 3: Mecânica de Instalação de CBMs (Exodii / Rubik)

- [ ] **3.1 Diálogos e Serviço de Rubik:**
  - Portar os diálogos e rotinas para que o NPC Rubik ofereça instalação cirúrgica de CBMs ao jogador.
- [ ] **3.2 Ajustes no Autodoc & Anestesia:**
  - Avaliar opções de anestesia local vs geral nos Autodocs para CBMs avançados.

---

### Fase 4: Port do Sistema Completo de Z-Levels (Verticalidade 3D) do CDDA
- [ ] **4.1 Visão e Renderização 3D:** Campo de visão vertical completo (renderização contínua de telhados, fossos e múltiplos andares simultâneos com transparência/sombreamento e oclusão de luz solar).
- [ ] **4.2 Balística e Projéteis em 3D:** Disparos de armas e arremessos em múltiplos níveis verticais (atirar de telhados/torres para o térreo e vice-versa, lançar granadas por claraboias/janelas).
- [ ] **4.3 Propagação de Som e Cheiro em 3D:** Som de passos e tiros atravessando pisos/tetos, e rastro de odor (scent) vertical para atração de zumbis entre andares.
- [ ] **4.4 Movimentação, Queda e IA em 3D:** Física de queda com dano cinético realista, rapel, paraquedas, tetos desmoronando, e pathfinding de monstros navegando por escadas, rampas e saltando de bordas.
- [ ] **4.5 Física de Veículos em Z-Levels:** Suporte a rampas e travessia de veículos entre andares (pontes elevadas, viadutos e garagens subterrâneas).

