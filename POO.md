📌 Exercício 1 - Criando uma Classe Livro
Objetivo: Criar uma classe Livro com atributos e métodos básicos.

📌 O que você vai praticar?
✅ Definição de classes e objetos
✅ Métodos de exibição

📌 O que fazer?
Crie a classe Livro com os atributos:
titulo (string)
autor (string)
preco (float)
Adicione um método exibir_info() que exibe os detalhes do livro.
📌 Exemplo de uso esperado:
python
Copiar
Editar
livro1 = Livro("O Senhor dos Anéis", "J.R.R. Tolkien", 99.90)
livro1.exibir_info()
Saída esperada:

makefile
Copiar
Editar
Título: O Senhor dos Anéis  
Autor: J.R.R. Tolkien  
Preço: R$99.90  
📌 Exercício 2 - Criando uma Biblioteca
Objetivo: Criar uma classe Biblioteca que gerencia uma lista de livros.

📌 O que você vai praticar?
✅ Listas dentro de classes
✅ Métodos para adicionar e exibir objetos

📌 O que fazer?
Crie a classe Biblioteca com um atributo livros (lista).
Adicione um método adicionar_livro(livro).
Adicione um método exibir_livros() que imprime os livros cadastrados.
📌 Exemplo de uso esperado:
python
Copiar
Editar
biblioteca = Biblioteca()
biblioteca.adicionar_livro(Livro("1984", "George Orwell", 45.00))
biblioteca.adicionar_livro(Livro("A Revolução dos Bichos", "George Orwell", 30.00))
biblioteca.exibir_livros()
Saída esperada:

yaml
Copiar
Editar
Título: 1984 | Autor: George Orwell | Preço: R$45.00  
Título: A Revolução dos Bichos | Autor: George Orwell | Preço: R$30.00  
📌 Exercício 3 - Calculando o Total da Biblioteca
Objetivo: Adicionar um método para calcular o total gasto em livros.

📌 O que você vai praticar?
✅ Uso de sum() com listas de objetos
✅ Retorno de valores em métodos

📌 O que fazer?
Adicione um método calcular_total() na classe Biblioteca.
Esse método deve somar o preço de todos os livros e retornar o valor total.
📌 Exemplo de uso esperado:
python
Copiar
Editar
total = biblioteca.calcular_total()
print(f"Total gasto em livros: R${total:.2f}")
Saída esperada:

nginx
Copiar
Editar
Total gasto em livros: R$75.00
📌 Exercício 4 - Aplicando Desconto nos Livros
Objetivo: Criar um método para aplicar descontos nos livros.

📌 O que você vai praticar?
✅ Modificação de atributos com métodos
✅ Uso de porcentagem para cálculos

📌 O que fazer?
Adicione um método aplicar_desconto(percentual) na classe Livro.
Esse método deve reduzir o preço do livro com base na porcentagem informada.
📌 Exemplo de uso esperado:
python
Copiar
Editar
livro = Livro("Dom Quixote", "Miguel de Cervantes", 50.00)
livro.aplicar_desconto(20)
livro.exibir_info()
Saída esperada:

makefile
Copiar
Editar
Título: Dom Quixote  
Autor: Miguel de Cervantes  
Preço: R$40.00  
🚀 Dicas para estudar melhor:
Estude um exercício por dia e tente refazê-lo sem olhar as respostas.
Modifique os exercícios, adicionando novos atributos ou métodos.
Tente explicar o código em voz alta, como se estivesse ensinando alguém.


-----------------------------------------------------------------------------



📌 Exercício 1 - Criando uma Classe ProdutoEstoque
Objetivo: Criar uma classe para representar um produto com estoque disponível.

📌 O que você vai praticar?
✅ Definição de classes e atributos
✅ Métodos para exibir informações

📌 O que fazer?
Crie a classe ProdutoEstoque com os atributos:
nome (string)
preco (float)
quantidade (int) → quantidade disponível no estoque
Adicione um método exibir_info() que imprime os detalhes do produto.
📌 Exemplo de uso esperado:
python
Copiar
Editar
produto = ProdutoEstoque("Monitor Gamer", 1200.00, 10)
produto.exibir_info()
Saída esperada:

makefile
Copiar
Editar
Produto: Monitor Gamer  
Preço: R$1200.00  
Quantidade em estoque: 10  
📌 Exercício 2 - Criando um Sistema de Estoque
Objetivo: Criar uma classe Estoque que gerencia uma lista de produtos.

📌 O que você vai praticar?
✅ Listas dentro de classes
✅ Métodos para adicionar e exibir objetos

📌 O que fazer?
Crie a classe Estoque com um atributo produtos (lista).
Adicione um método adicionar_produto(produto).
Adicione um método exibir_estoque() que imprime todos os produtos cadastrados.
📌 Exemplo de uso esperado:
python
Copiar
Editar
estoque = Estoque()
estoque.adicionar_produto(ProdutoEstoque("Teclado Mecânico", 250.00, 15))
estoque.adicionar_produto(ProdutoEstoque("Mouse Sem Fio", 180.00, 20))
estoque.exibir_estoque()
Saída esperada:

yaml
Copiar
Editar
Produto: Teclado Mecânico | Preço: R$250.00 | Quantidade: 15  
Produto: Mouse Sem Fio | Preço: R$180.00 | Quantidade: 20  
📌 Exercício 3 - Gerenciando Pedidos e Reduzindo Estoque
Objetivo: Criar um sistema onde podemos comprar produtos e reduzir a quantidade em estoque.

📌 O que você vai praticar?
✅ Atualização de atributos dentro de métodos
✅ Verificação de disponibilidade antes de realizar ações

📌 O que fazer?
Crie um método realizar_pedido(nome_produto, quantidade) dentro da classe Estoque.
O método deve:
Verificar se o produto existe na lista.
Verificar se a quantidade desejada está disponível.
Se estiver, reduzir o estoque e exibir uma mensagem de compra realizada.
Se não houver estoque suficiente, exibir uma mensagem de erro.
📌 Exemplo de uso esperado:
python
Copiar
Editar
estoque.realizar_pedido("Mouse Sem Fio", 5)
estoque.realizar_pedido("Teclado Mecânico", 20)  # Estoque insuficiente
estoque.exibir_estoque()
Saída esperada:

yaml
Copiar
Editar
Pedido realizado: 5x Mouse Sem Fio  
Estoque insuficiente para: Teclado Mecânico  
Produto: Teclado Mecânico | Preço: R$250.00 | Quantidade: 15  
Produto: Mouse Sem Fio | Preço: R$180.00 | Quantidade: 15  
🚀 Como estudar melhor esses exercícios?
✅ Faça um por dia e tente explicá-lo em voz alta.
✅ Modifique os exercícios: adicione métodos, permita cancelar pedidos, etc.
✅ Tente criar um menu interativo para gerenciar o estoque.



-----------------------------------------------------------------------------




📌 Exercício 1 - Criando uma Classe Aluno
Objetivo: Criar uma classe para representar um aluno com nome e notas.

📌 O que você vai praticar?
✅ Definição de classes e atributos
✅ Métodos para exibir informações

📌 O que fazer?
Crie a classe Aluno com os atributos:
nome (string)
notas (lista de floats)
Adicione um método exibir_info() que imprime o nome do aluno e suas notas.
📌 Exemplo de uso esperado:
python
Copiar
Editar
aluno = Aluno("Carlos", [8.5, 7.0, 9.2])
aluno.exibir_info()
Saída esperada:

makefile
Copiar
Editar
Aluno: Carlos  
Notas: [8.5, 7.0, 9.2]  
📌 Exercício 2 - Criando um Sistema de Turma
Objetivo: Criar uma classe Turma que gerencia uma lista de alunos.

📌 O que você vai praticar?
✅ Listas dentro de classes
✅ Métodos para adicionar e exibir objetos

📌 O que fazer?
Crie a classe Turma com um atributo alunos (lista).
Adicione um método adicionar_aluno(aluno).
Adicione um método exibir_alunos() que imprime todos os alunos cadastrados.
📌 Exemplo de uso esperado:
python
Copiar
Editar
turma = Turma()
turma.adicionar_aluno(Aluno("Ana", [9.0, 8.5, 7.8]))
turma.adicionar_aluno(Aluno("Pedro", [6.5, 7.2, 8.0]))
turma.exibir_alunos()
Saída esperada:

yaml
Copiar
Editar
Aluno: Ana | Notas: [9.0, 8.5, 7.8]  
Aluno: Pedro | Notas: [6.5, 7.2, 8.0]  
📌 Exercício 3 - Calculando a Média dos Alunos
Objetivo: Criar um método para calcular a média das notas de um aluno.

📌 O que você vai praticar?
✅ Uso de sum() para calcular médias
✅ Retorno de valores em métodos

📌 O que fazer?
Adicione um método calcular_media() na classe Aluno.
Esse método deve calcular e retornar a média das notas.
📌 Exemplo de uso esperado:
python
Copiar
Editar
media = aluno.calcular_media()
print(f"Média de {aluno.nome}: {media:.2f}")
Saída esperada:

yaml
Copiar
Editar
Média de Carlos: 8.23  
📌 Exercício 4 - Determinar Situação do Aluno
Objetivo: Criar um método para verificar se o aluno foi aprovado.

📌 O que você vai praticar?
✅ Condicionais dentro de métodos
✅ Retorno de status baseado na média

📌 O que fazer?
Adicione um método verificar_situacao() na classe Aluno.
Se a média for ≥ 7.0, retorne "Aprovado".
Se for entre 5.0 e 6.9, retorne "Recuperação".
Caso contrário, retorne "Reprovado".
📌 Exemplo de uso esperado:
python
Copiar
Editar
situacao = aluno.verificar_situacao()
print(f"{aluno.nome} está {situacao}")
Saída esperada:

nginx
Copiar
Editar
Carlos está Aprovado  
📌 Exercício 5 - Calculando a Média da Turma
Objetivo: Criar um método na classe Turma para calcular a média geral dos alunos.

📌 O que você vai praticar?
✅ Iteração sobre objetos em listas
✅ Cálculo de médias de vários alunos

📌 O que fazer?
Adicione um método calcular_media_turma() na classe Turma.
Ele deve calcular a média de todos os alunos da turma.
📌 Exemplo de uso esperado:
python
Copiar
Editar
media_turma = turma.calcular_media_turma()
print(f"Média geral da turma: {media_turma:.2f}")
Saída esperada:

yaml
Copiar
Editar
Média geral da turma: 7.85  
📌 Exercício 6 - Gerando Relatório da Turma
Objetivo: Criar um método para exibir o nome, média e situação de todos os alunos.

📌 O que você vai praticar?
✅ Uso de métodos dentro de métodos
✅ Geração de relatórios formatados

📌 O que fazer?
Adicione um método gerar_relatorio() na classe Turma.
Ele deve exibir nome, média e situação de cada aluno.
📌 Exemplo de uso esperado:
python
Copiar
Editar
turma.gerar_relatorio()
Saída esperada:

makefile
Copiar
Editar
Aluno: Ana | Média: 8.43 | Situação: Aprovado  
Aluno: Pedro | Média: 7.23 | Situação: Aprovado  
Aluno: João | Média: 5.80 | Situação: Recuperação  
🚀 Dicas para estudar melhor esses desafios:
✅ Resolva um por dia e tente explicá-lo para você mesmo.
✅ Refaça sem olhar as respostas, testando variações (ex: criar uma função para adicionar várias notas).
✅ Adicione funcionalidades extras, como um método para remover alunos da turma.
