📌 Exercício - CRUD de Funcionários com SQLite
Objetivo: Criar um sistema de cadastro de funcionários, onde possamos Criar, Ler, Atualizar e Deletar (CRUD) registros no banco de dados.

📌 O que você vai praticar?
✅ Uso do banco de dados SQLite com Python
✅ CRUD (Create, Read, Update, Delete)
✅ Uso da biblioteca sqlite3
✅ Manipulação de bancos relacionais
✅ Boas práticas para trabalhar com SQL em Python

📌 O que fazer?
Criar um sistema para gerenciar funcionários de uma empresa com um banco SQLite. Ele deve ter as operações básicas:
1️⃣ Criar um banco de dados chamado empresa.db
2️⃣ Criar uma tabela chamada funcionarios com:

id (chave primária, autoincremento)
nome (texto)
cargo (texto)
salario (float)
3️⃣ Criar as funções para:
Cadastrar funcionário
Listar funcionários
Atualizar salário de um funcionário
Remover um funcionário
📌 Código base
Aqui está o código que você pode usar como referência:

python
Copiar
Editar
import sqlite3

# Conectar ao banco de dados (ou criar se não existir)
conn = sqlite3.connect("empresa.db")
cursor = conn.cursor()

# Criar a tabela funcionários se não existir
cursor.execute("""
CREATE TABLE IF NOT EXISTS funcionarios (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    nome TEXT NOT NULL,
    cargo TEXT NOT NULL,
    salario REAL NOT NULL
)
""")
conn.commit()


# Função para adicionar um funcionário
def adicionar_funcionario(nome, cargo, salario):
    cursor.execute("INSERT INTO funcionarios (nome, cargo, salario) VALUES (?, ?, ?)", (nome, cargo, salario))
    conn.commit()
    print(f"Funcionário {nome} adicionado com sucesso!")


# Função para listar todos os funcionários
def listar_funcionarios():
    cursor.execute("SELECT * FROM funcionarios")
    funcionarios = cursor.fetchall()
    
    if not funcionarios:
        print("Nenhum funcionário cadastrado.")
    else:
        for f in funcionarios:
            print(f"ID: {f[0]} | Nome: {f[1]} | Cargo: {f[2]} | Salário: R${f[3]:.2f}")


# Função para atualizar o salário de um funcionário
def atualizar_salario(id_funcionario, novo_salario):
    cursor.execute("UPDATE funcionarios SET salario = ? WHERE id = ?", (novo_salario, id_funcionario))
    conn.commit()
    
    if cursor.rowcount > 0:
        print(f"Salário atualizado com sucesso para o funcionário ID {id_funcionario}!")
    else:
        print("Funcionário não encontrado.")


# Função para remover um funcionário
def remover_funcionario(id_funcionario):
    cursor.execute("DELETE FROM funcionarios WHERE id = ?", (id_funcionario,))
    conn.commit()
    
    if cursor.rowcount > 0:
        print(f"Funcionário ID {id_funcionario} removido com sucesso!")
    else:
        print("Funcionário não encontrado.")


# TESTANDO AS FUNÇÕES
if __name__ == "__main__":
    while True:
        print("\n===== MENU CRUD FUNCIONÁRIOS =====")
        print("1 - Adicionar Funcionário")
        print("2 - Listar Funcionários")
        print("3 - Atualizar Salário")
        print("4 - Remover Funcionário")
        print("5 - Sair")

        opcao = input("Escolha uma opção: ")

        if opcao == "1":
            nome = input("Nome do funcionário: ")
            cargo = input("Cargo do funcionário: ")
            salario = float(input("Salário: "))
            adicionar_funcionario(nome, cargo, salario)

        elif opcao == "2":
            listar_funcionarios()

        elif opcao == "3":
            id_funcionario = int(input("ID do funcionário: "))
            novo_salario = float(input("Novo salário: "))
            atualizar_salario(id_funcionario, novo_salario)

        elif opcao == "4":
            id_funcionario = int(input("ID do funcionário: "))
            remover_funcionario(id_funcionario)

        elif opcao == "5":
            print("Saindo...")
            break

        else:
            print("Opção inválida. Tente novamente.")

# Fechar conexão com o banco ao sair do programa
conn.close()
📌 Como testar e evoluir esse código?
🚀 Desafios extras para você evoluir:
✅ Adicionar busca por nome: Criar uma função que busca um funcionário pelo nome.
✅ Criar um campo "data de contratação" e permitir a atualização desse campo.
✅ Ordenar funcionários por salário ou nome ao listar.
✅ Gerar um relatório com a média salarial da empresa.
✅ Usar um banco de dados SQLite externo (exemplo: SQLiteStudio).



---------------------------------------------------------------------------------





🚀 Desafio Final: Sistema de Controle de Pedidos
Objetivo: Criar um sistema onde uma empresa pode gerenciar seus pedidos, vinculando clientes, produtos e compras de maneira eficiente.

📌 O que você vai aprender e praticar?
✅ POO Avançado: Relacionamento entre classes (Cliente, Produto, Pedido).
✅ Banco de Dados SQLite: Múltiplas tabelas e relações.
✅ CRUD completo: Criar, Listar, Atualizar e Remover registros.
✅ Relacionamento entre tabelas: Um cliente pode fazer vários pedidos.
✅ Boas práticas: Código modular, organizado e legível.

📌 O que você precisa implementar?
1️⃣ Criar tabelas no banco de dados SQLite para armazenar:

clientes (id, nome, email)
produtos (id, nome, preço)
pedidos (id, cliente_id, data)
itens_pedido (id, pedido_id, produto_id, quantidade)
2️⃣ Criar classes Python que representem os objetos do sistema:

Cliente
Produto
Pedido
ItemPedido
3️⃣ Criar um CRUD completo para:

Cadastrar clientes
Cadastrar produtos
Criar pedidos associando clientes e produtos
Listar todos os pedidos com detalhes (cliente, produtos, total do pedido)
Remover um pedido
📌 Código base
1️⃣ Criando o Banco de Dados e Tabelas
python
Copiar
Editar
import sqlite3

# Conectar ao banco
conn = sqlite3.connect("loja.db")
cursor = conn.cursor()

# Criar tabelas
cursor.executescript("""
CREATE TABLE IF NOT EXISTS clientes (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    nome TEXT NOT NULL,
    email TEXT NOT NULL UNIQUE
);

CREATE TABLE IF NOT EXISTS produtos (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    nome TEXT NOT NULL,
    preco REAL NOT NULL
);

CREATE TABLE IF NOT EXISTS pedidos (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    cliente_id INTEGER NOT NULL,
    data TEXT NOT NULL,
    FOREIGN KEY(cliente_id) REFERENCES clientes(id)
);

CREATE TABLE IF NOT EXISTS itens_pedido (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    pedido_id INTEGER NOT NULL,
    produto_id INTEGER NOT NULL,
    quantidade INTEGER NOT NULL,
    FOREIGN KEY(pedido_id) REFERENCES pedidos(id),
    FOREIGN KEY(produto_id) REFERENCES produtos(id)
);
""")
conn.commit()
2️⃣ Criando as Classes
python
Copiar
Editar
class Cliente:
    def __init__(self, nome, email):
        self.nome = nome
        self.email = email

    def salvar(self):
        cursor.execute("INSERT INTO clientes (nome, email) VALUES (?, ?)", (self.nome, self.email))
        conn.commit()
        print(f"Cliente {self.nome} cadastrado com sucesso!")


class Produto:
    def __init__(self, nome, preco):
        self.nome = nome
        self.preco = preco

    def salvar(self):
        cursor.execute("INSERT INTO produtos (nome, preco) VALUES (?, ?)", (self.nome, self.preco))
        conn.commit()
        print(f"Produto {self.nome} cadastrado com sucesso!")


class Pedido:
    def __init__(self, cliente_id):
        self.cliente_id = cliente_id

    def salvar(self):
        cursor.execute("INSERT INTO pedidos (cliente_id, data) VALUES (?, DATE('now'))", (self.cliente_id,))
        conn.commit()
        print("Pedido criado com sucesso!")
        return cursor.lastrowid  # Retorna o ID do pedido criado


class ItemPedido:
    def __init__(self, pedido_id, produto_id, quantidade):
        self.pedido_id = pedido_id
        self.produto_id = produto_id
        self.quantidade = quantidade

    def salvar(self):
        cursor.execute("INSERT INTO itens_pedido (pedido_id, produto_id, quantidade) VALUES (?, ?, ?)",
                       (self.pedido_id, self.produto_id, self.quantidade))
        conn.commit()
        print("Item adicionado ao pedido!")
3️⃣ Criando as Funções CRUD
python
Copiar
Editar
def listar_clientes():
    cursor.execute("SELECT * FROM clientes")
    for c in cursor.fetchall():
        print(f"ID: {c[0]} | Nome: {c[1]} | Email: {c[2]}")

def listar_produtos():
    cursor.execute("SELECT * FROM produtos")
    for p in cursor.fetchall():
        print(f"ID: {p[0]} | Nome: {p[1]} | Preço: R${p[2]:.2f}")

def listar_pedidos():
    cursor.execute("""
    SELECT pedidos.id, clientes.nome, pedidos.data
    FROM pedidos
    JOIN clientes ON pedidos.cliente_id = clientes.id
    """)
    for pedido in cursor.fetchall():
        print(f"\nPedido ID: {pedido[0]} | Cliente: {pedido[1]} | Data: {pedido[2]}")
        cursor.execute("""
        SELECT produtos.nome, itens_pedido.quantidade, produtos.preco * itens_pedido.quantidade
        FROM itens_pedido
        JOIN produtos ON itens_pedido.produto_id = produtos.id
        WHERE itens_pedido.pedido_id = ?
        """, (pedido[0],))
        total = 0
        for item in cursor.fetchall():
            print(f"  Produto: {item[0]} | Quantidade: {item[1]} | Total: R${item[2]:.2f}")
            total += item[2]
        print(f"  🔹 Total do Pedido: R${total:.2f}")

def remover_pedido(pedido_id):
    cursor.execute("DELETE FROM pedidos WHERE id = ?", (pedido_id,))
    conn.commit()
    print("Pedido removido com sucesso!")
4️⃣ Criando um Menu para Testar o CRUD
python
Copiar
Editar
while True:
    print("\n===== MENU PEDIDOS =====")
    print("1 - Cadastrar Cliente")
    print("2 - Cadastrar Produto")
    print("3 - Criar Pedido")
    print("4 - Listar Pedidos")
    print("5 - Remover Pedido")
    print("6 - Sair")

    opcao = input("Escolha uma opção: ")

    if opcao == "1":
        nome = input("Nome: ")
        email = input("Email: ")
        Cliente(nome, email).salvar()

    elif opcao == "2":
        nome = input("Nome do produto: ")
        preco = float(input("Preço: "))
        Produto(nome, preco).salvar()

    elif opcao == "3":
        listar_clientes()
        cliente_id = int(input("ID do Cliente: "))
        pedido = Pedido(cliente_id)
        pedido_id = pedido.salvar()

        while True:
            listar_produtos()
            produto_id = int(input("ID do Produto (ou 0 para finalizar): "))
            if produto_id == 0:
                break
            quantidade = int(input("Quantidade: "))
            ItemPedido(pedido_id, produto_id, quantidade).salvar()

    elif opcao == "4":
        listar_pedidos()

    elif opcao == "5":
        listar_pedidos()
        pedido_id = int(input("ID do Pedido a remover: "))
        remover_pedido(pedido_id)

    elif opcao == "6":
        break

conn.close()
📌 Como evoluir esse código?
✅ Adicionar um sistema de login para clientes.
✅ Gerar um relatório em CSV com todos os pedidos.
✅ Implementar Flask/Django para criar uma API desse sistema.
