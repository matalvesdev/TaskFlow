# TaskFlow ✅

Sistema de gerenciamento de tarefas desenvolvido em Java com interface de linha de comando (CLI).  Permite adicionar, remover, listar, finalizar e pesquisar tarefas de forma simples e eficiente.

## 📋 Sobre o Projeto

TaskFlow é uma aplicação Java console que oferece um sistema completo de gerenciamento de tarefas.   O sistema utiliza estruturas de dados eficientes (HashMap) para armazenar e manipular tarefas, permitindo operações rápidas de CRUD e busca por descrição.

## ✨ Funcionalidades

- ➕ **Adicionar Tarefa** - Criar novas tarefas com ID único e descrição
- ❌ **Remover Tarefa** - Deletar tarefas pelo ID
- 📋 **Listar Tarefas** - Visualizar todas as tarefas cadastradas
- ✔️ **Marcar como Concluída** - Finalizar tarefas em andamento
- 🔍 **Procurar Tarefa** - Buscar tarefas por descrição (busca parcial)
- 🏷️ **Status de Tarefas** - Controle de tarefas "EM ANDAMENTO" e "FINALIZADA"
- 🔢 **ID Único** - Validação para evitar duplicação de IDs

## 🛠️ Tecnologias Utilizadas

- **Java 21** - Linguagem de programação
- **Maven** - Gerenciador de dependências e build
- **Collections Framework** - HashMap para armazenamento eficiente
- **Scanner** - Entrada de dados do usuário

## 🏗️ Arquitetura do Projeto

```
TaskFlow/
├── src/
│   └── main/
│       └── java/
│           └── org/
│               └── example/
│                   ├── Tarefa.java
│                   ├── GerenciadorTarefa.java
│                   └── Main.java
├── pom.xml
└── README. md
```

## 📦 Classes Principais

### Tarefa.java

Representa uma tarefa individual no sistema.

**Atributos:**
| Atributo | Tipo | Descrição |
|----------|------|-----------|
| `id` | String | Identificador único da tarefa |
| `descricao` | String | Descrição da tarefa |
| `finalizada` | boolean | Status da tarefa (false = EM ANDAMENTO, true = FINALIZADA) |

**Métodos:**
- `Tarefa(String id, String descricao)` - Construtor
- `getId()` - Retorna o ID
- `getDescricao()` - Retorna a descrição
- `isFinalizada()` - Verifica se está finalizada
- `finalizarTarefa()` - Marca como finalizada
- `toString()` - Formatação personalizada

### GerenciadorTarefa.java

Classe responsável pelo gerenciamento das tarefas.

**Estrutura de Dados:**
```java
private Map<String, Tarefa> tarefas = new HashMap<>();
```

**Métodos:**

#### adicionarTarefa(String id, String descricao)
Adiciona uma nova tarefa ao sistema.

**Validações:**
- Verifica se o ID já existe
- Impede duplicação de IDs

**Exemplo:**
```java
gerenciador.adicionarTarefa("T001", "Estudar Java");
// Output: Tarefa [Estudar Java] adicionada com sucesso! 
```

#### removerTarefa(String id)
Remove uma tarefa pelo ID.

**Validações:**
- Verifica se a tarefa existe antes de remover

**Exemplo:**
```java
gerenciador.removerTarefa("T001");
// Output: Tarefa [T001] removida com sucesso! 
```

#### imprimirTarefas()
Lista todas as tarefas cadastradas. 

**Exemplo de Saída:**
```
========================
Imprimindo Tarefas: 
Tarefa [id=T001] [descrição=Estudar Java] [EM ANDAMENTO]
Tarefa [id=T002] [descrição=Fazer exercícios] [FINALIZADA]
========================
```

#### finalizarTarefa(String id)
Marca uma tarefa como finalizada.

**Exemplo:**
```java
gerenciador.finalizarTarefa("T001");
// Output: Tarefa [T001] [Estudar Java] foi finalizada com sucesso!
```

#### procurarTarefa(String descricao)
Busca tarefas que contenham a descrição fornecida (busca parcial).

**Exemplo:**
```java
gerenciador.procurarTarefa("Java");
// Output: 
// Tarefa encontrada! 
// Tarefa [id=T001] [descrição=Estudar Java] [EM ANDAMENTO]
```

### Main.java

Classe principal com interface de menu interativo.

**Fluxo do Programa:**
1. Inicializa Scanner e GerenciadorTarefa
2. Exibe menu de opções
3. Lê seleção do usuário
4. Executa funcionalidade correspondente
5. Repete até o usuário sair

## 🚀 Como Executar

### Pré-requisitos

- Java 21 ou superior
- Maven 3.6+

### Passo 1: Clone o repositório

```bash
git clone https://github.com/matalvesdev/TaskFlow.git
cd TaskFlow
```

### Passo 2: Compile o projeto

```bash
mvn clean compile
```

### Passo 3: Execute o programa

```bash
mvn exec:java -Dexec.mainClass="org.example.Main"
```

Ou compile e execute diretamente:

```bash
mvn clean package
java -cp target/TaskFlow-1.0-SNAPSHOT.jar org.example.Main
```

## 💻 Menu Interativo

Ao executar o programa, você verá o seguinte menu:

```
Bem vindo ao TaskFlow! 
#################################
Escolha uma opção: 
1. Adicionar Tarefa
2. Remover Tarefa por ID
3. Listar Tarefas
4. Marcar tarefa como concluida
5. Procurar tarefa
6. Sair do TaskFlow
#################################
```

## 📝 Exemplo de Uso Completo

```
Bem vindo ao TaskFlow!
#################################
Escolha uma opção: 
1. Adicionar Tarefa
2. Remover Tarefa por ID
3. Listar Tarefas
4. Marcar tarefa como concluida
5. Procurar tarefa
6. Sair do TaskFlow
#################################
1
Digite o ID: 
T001
Digite a descrição:
Estudar Java para certificação
Tarefa [Estudar Java para certificação] adicionada com sucesso! 

#################################
Escolha uma opção: 
1. Adicionar Tarefa
2. Remover Tarefa por ID
3. Listar Tarefas
4. Marcar tarefa como concluida
5. Procurar tarefa
6. Sair do TaskFlow
#################################
1
Digite o ID:
T002
Digite a descrição: 
Fazer exercícios de algoritmos
Tarefa [Fazer exercícios de algoritmos] adicionada com sucesso!

#################################
Escolha uma opção: 
1. Adicionar Tarefa
2. Remover Tarefa por ID
3. Listar Tarefas
4. Marcar tarefa como concluida
5. Procurar tarefa
6. Sair do TaskFlow
#################################
3
========================
Imprimindo Tarefas:
Tarefa [id=T001] [descrição=Estudar Java para certificação] [EM ANDAMENTO]
Tarefa [id=T002] [descrição=Fazer exercícios de algoritmos] [EM ANDAMENTO]
========================

#################################
Escolha uma opção: 
1. Adicionar Tarefa
2. Remover Tarefa por ID
3. Listar Tarefas
4. Marcar tarefa como concluida
5. Procurar tarefa
6. Sair do TaskFlow
#################################
4
Digite o ID:
T001
Tarefa [T001] [Estudar Java para certificação] foi finalizada com sucesso!

#################################
Escolha uma opção: 
1. Adicionar Tarefa
2. Remover Tarefa por ID
3. Listar Tarefas
4. Marcar tarefa como concluida
5. Procurar tarefa
6. Sair do TaskFlow
#################################
5
Digite a descrição:
Java
Tarefa encontrada!
Tarefa [id=T001] [descrição=Estudar Java para certificação] [FINALIZADA]

#################################
Escolha uma opção: 
1. Adicionar Tarefa
2. Remover Tarefa por ID
3. Listar Tarefas
4. Marcar tarefa como concluida
5. Procurar tarefa
6. Sair do TaskFlow
#################################
6
```

## 🎯 Conceitos de POO Aplicados

### Encapsulamento
- Atributos privados na classe `Tarefa`
- Acesso controlado através de getters

### Separação de Responsabilidades
- `Tarefa`: Representa os dados
- `GerenciadorTarefa`: Gerencia operações de CRUD
- `Main`: Interface com o usuário

### Uso de Collections
- `HashMap` para armazenamento eficiente (O(1) para busca por ID)
- Iteração com `for-each` nas listagens

## 📊 Diagrama de Classes

```
┌─────────────────────────┐
│       Tarefa            │
├─────────────────────────┤
│ - id: String            │
│ - descricao: String     │
│ - finalizada:  boolean   │
├─────────────────────────┤
│ + Tarefa(...)           │
│ + getId(): String       │
│ + getDescricao(): String│
│ + isFinalizada(): bool  │
│ + finalizarTarefa()     │
│ + toString(): String    │
└─────────────────────────┘
           △
           │
           │ usa
           │
┌─────────────────────────┐
│  GerenciadorTarefa      │
├─────────────────────────┤
│ - tarefas: Map<String,  │
│             Tarefa>     │
├─────────────────────────┤
│ + adicionarTarefa(...)  │
│ + removerTarefa(...)    │
│ + imprimirTarefas()     │
│ + finalizarTarefa(...)  │
│ + procurarTarefa(...)   │
└─────────────────────────┘
           △
           │
           │ usa
           │
┌─────────────────────────┐
│        Main             │
├─────────────────────────┤
│ + main(...)             │
│ - printMenu()           │
│ - adicionarTarefa(...)  │
│ - removerTarefaPorId(... │
│ - finalizarTarefa(...)  │
│ - procurarTarefa(...)   │
└─────────────────────────┘
```

## 🔮 Possíveis Melhorias Futuras

- [ ] Persistência de dados (salvar em arquivo/banco de dados)
- [ ] Adicionar data de criação e prazo nas tarefas
- [ ] Prioridade de tarefas (alta, média, baixa)
- [ ] Categorias/tags para organização
- [ ] Filtros avançados (por status, data, prioridade)
- [ ] Edição de tarefas existentes
- [ ] Interface gráfica (JavaFX)
- [ ] Exportação de tarefas para CSV/PDF
- [ ] Sistema de usuários
- [ ] Validação de entrada com try-catch
- [ ] Testes unitários com JUnit
- [ ] Ordenação personalizada das tarefas

## 🧪 Testes

```bash
mvn test
```

## 👨‍💻 Autor

Desenvolvido por [matalvesdev](https://github.com/matalvesdev)

## 📄 Licença

Este projeto está sob a licença MIT.  Veja o arquivo LICENSE para mais detalhes.

---

✅ *"Organize suas tarefas, organize sua vida!"* ✅

⭐ Se este projeto foi útil para você, considere dar uma estrela!  
