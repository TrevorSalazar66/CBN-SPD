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

### Fase 4: Sistema Completo de Z-Levels (3D Vertical) do CDDA
- [ ] **4.1 Visão Vertical e Campo de Visão 3D (3D FOV & Iluminação):**
  - Portar e refinar o sistema de visão 3D contínua do CDDA, permitindo enxergar criaturas, terrenos e itens em andares inferiores (através de telhados, escadas, grades, fossos e pisos transparentes) e superiores.
  - Ajustar a iluminação 3D para propagação de luz natural/solar e lanternas através de aberturas entre níveis.
- [ ] **4.2 Balística e Combate à Distância Vertical (3D Projectiles):**
  - Adaptar a física de projéteis (`ballistics.cpp` / `projectile.cpp`) para permitir mirar e disparar armas de fogo, arcos e arremesso em alvos em diferentes Z-levels (de telhados para o chão e vice-versa).
  - Incluir cálculo de obstrução por pisos/tetos e vantagem de altura.
- [ ] **4.3 Propagação Vertical de Som e Cheiro (3D Audio & Scent):**
  - Propagação realista de som entre andares (sons abafados por lajes sólidas, limpos através de escadarias e vãos abertos).
  - Atualização do mapa de odores para que monstros consigam rastrear o jogador em 3D (subindo escadas e rampas).
- [ ] **4.4 Física de Queda, Gravidade e Colapso Estrutural:**
  - Dinâmica de queda de criaturas e detritos entre múltiplos níveis Z, com cálculo de dano por impacto proporcional à altura e suporte a itens/traços de queda suave.
  - Colapso vertical de construções caso o suporte do piso inferior seja destruído.
- [ ] **4.5 Rampas e Movimentação de Veículos entre Z-Levels:**
  - Suporte a veículos transitando por rampas entre andares (ex: garagens de vários pavimentos, pontes elevadas).
- [ ] **4.6 Otimização de Performance para Mobile:**
  - Garantir que a renderização e caches de submapas 3D sejam otimizados para manter o consumo de bateria e FPS estáveis no Android.

