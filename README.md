# D@ta-Vence
# Projeto de Gerenciamento de Estoque

Este projeto é uma aplicação web desenvolvida em PHP e MySQL para gerenciamento de estoque. Ele evolui por versões, adicionando funcionalidades e melhorias de interface, sempre focando na simplicidade, clareza e eficiência.

---

## 📦 Versão 1.0 – Estrutura Inicial

### Descrição
A versão 1.0 estabelece a base do sistema, fornecendo recursos essenciais de cadastro, listagem e controle de produtos.

### Principais Funcionalidades
- **Cadastro de Produtos**  
  - Página: `index.php`  
  - Campos:  
    - Nome (string)  
    - Quantidade (inteiro)  
    - Preço (decimal)  
    - Data de Fabricação (date)  
    - Data de Validade (date)  
  - Processamento: `salvar.php` grava os dados no MySQL.

- **Listagem de Produtos**  
  - Página: `listar.php`  
  - Exibe tabela com colunas: ID, Nome, Quantidade, Preço Original, Preço Final, Data de Fabricação, Data de Validade.  
  - Ordenação fixa por data de validade (crescente).  
  - **Descontos Automáticos**:  
    - Vencimento < 7 dias → 50% off  
    - Vencimento entre 7 e 29 dias → 20% off  
    - ≥ 30 dias → sem desconto  
  - **Cores de Destaque**:  
    - Vermelho claro (50%)  
    - Amarelo claro (20%)  
    - Verde claro (sem desconto)

- **Filtragem de Exibição**  
  - Dropdown para ocultar/exibir:  
    - Todos produtos  
    - Com desconto  
    - Com 50%  
    - Com 20%  
    - Sem desconto

- **Edição de Produtos**  
  - Página: `editar.php`  
  - Permite alterar Nome e Preço.  
  - Botão “Remover Produto” com confirmação JavaScript.

- **Remoção de Quantidade**  
  - Página: `remover_quantidade.php`  
  - Subtrai valor informado, sem permitir quantidade negativa.

### Uso na Versão 1.0
1. Execute `index.php` e preencha o formulário para cadastrar um produto.  
2. Clique em **Salvar** para gravar no banco.  
3. Acesse `listar.php` para visualizar, editar ou remover produtos.  
4. Use “Remover Qtde” para decrementar estoque.

---

## 🚀 Versão 2.0 – Ordenação e Filtros Avançados

### Descrição
A versão 2.0 aprimora a listagem com ordenação dinâmica e filtragem mais granular.

### Novas Funcionalidades
- **Ordenação Dinâmica**  
  - Cabeçalhos de coluna clicáveis: ID, Nome, Quantidade, Preço, Fabricação, Validade.  
  - Alternância ASC/DESC mantida via parâmetros na URL.

- **Filtros com Checkboxes**  
  - Substituem dropdown, permitindo múltiplas seleções simultâneas.  
  - Categorias:  
    - Vencidos (preço final R$ 0,00; fundo roxo)  
    - 0-7 dias (50%; vermelho)  
    - 8-30 dias (20%; amarelo)  
    - +30 dias (sem desconto; verde)  
  - Estado dos filtros preservado no envio do formulário.

- **Tratamento de Vencidos**  
  - Itens expirados claramente destacados.  
  - Preço final forçado a R$ 0,00.

- **Formato de Data**  
  - Apresentação no formato `dd/mm/YYYY`.

### Uso na Versão 2.0
1. Em `listar.php`, clique nos cabeçalhos para ordenar.  
2. Selecione/desmarque checkboxes para filtrar conforme validade.  
3. Produtos vencidos são destacados em roxo automaticamente.

---

## 🧭 Versão 3.0 – Painel de Resumo e Layout Avançado

### Descrição
Foco na experiência de cadastro, adicionando um dashboard resumo e novo layout na página principal.

### Novas Funcionalidades
- **Dashboard "ATENÇÃO" em `index.php`**  
  - Painel lateral exibindo contagem de produtos por categoria de validade:  
    - Vencidos  
    - 0-7 dias (50%)  
    - 8-30 dias (20%)  
    - +30 dias  
  - Cada bloco usa cor correspondente ao sistema de listagem.

- **Layout de Duas Colunas**  
  - Coluna esquerda: formulário de cadastro.  
  - Coluna direita: painel de resumo + logo do sistema (`logo.png`).

- **Inclusão de Logo**  
  - Imagem `logo.png` incorporada no painel.

### Estilização e Arquivos
- CSS embarcado em `index.php` para o painel e grid.  
- `styles.css` mantém estilos globais e cores de destaque na listagem.

### Uso na Versão 3.0
1. Abra `index.php` para acessar o formulário e visualizar o painel “ATENÇÃO”.  
2. Cadastre produtos normalmente; observe as atualizações em tempo real no painel.  
3. Use `listar.php` como nas versões anteriores para visualizar, ordenar e filtrar.

---

## 🎨 Versão 4.0 – Interface Moderna com Bootstrap

### Descrição
Integração completa com Bootstrap 4.6.2 para responsividade e consistência visual.

### Novas Funcionalidades
- **Bootstrap em Todas as Páginas**  
  - `index.php`, `listar.php`, `editar.php`, `remover_quantidade.php`, `salvar.php` usam componentes Bootstrap.

- **Cabeçalho de Navegação Comum**  
  - Inclui logo e links rápidos para cadastro e listagem.

- **Layouts com Grid Bootstrap**  
  - `index.php`: duas colunas responsivas.  
  - `listar.php`: filtros à esquerda, tabela à direita.  
  - Formulários e mensagens adaptados com classes Bootstrap.

- **Estilos Complementares**  
  - `styles.css` ajustado para harmonizar com Bootstrap.

### Uso na Versão 4.0
1. Acesse qualquer página via cabeçalho de navegação.  
2. Formulários agora estilizados com Bootstrap.  
3. Utilize painel “ATENÇÃO” e sistema de filtros responsivo.  
4. Teste edição e remoção em ambiente visualmente aprimorado.

---

## 📂 Estrutura do Banco de Dados

- **Banco:** `estoque`  
- **Tabela:** `produtos`  
  - `id` INT PK AI  
  - `nome` VARCHAR  
  - `quantidade` INT  
  - `preco` DECIMAL  
  - `data_fabricacao` DATE  
  - `data_validade` DATE  

(*Estrutura inalterada desde a versão 1.0*)

---

## 🗂️ Arquivos do Projeto

- `index.php`  
- `salvar.php`  
- `listar.php`  
- `editar.php`  
- `remover_quantidade.php`  
- `estoque.sql`  
- `styles.css`  
- `logo.png`  

---

## 🚀 Como Usar o Programa

1. **Cadastro de Produtos**  
   - Navegue até `index.php`.  
   - Preencha o formulário e clique em **“Salvar”**.  
   - Observe o painel de resumo (v3+/v4+) ou formatação simples (v1/ v2).

2. **Visualização e Ações**  
   - Acesse `listar.php`.  
   - Ordene clicando nas colunas.  
   - Filtre por validade com checkboxes.  
   - Use **“Editar”** ou **“Remover Qtde”** conforme necessidade.

3. **Edição e Remoção**  
   - Em `editar.php`, modifique ou exclua produtos.  
   - Em `remover_quantidade.php`, subtraia unidades do estoque.

---

## 📚 Dependências

- PHP ≥ 7.4  
- Servidor Web (Apache)  
- MySQL / MariaDB  
- Bootstrap 4.6.2 (CDN)

---
