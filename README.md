# SGBD_PeixeBom_Sao_Francisco
Neste repositório, consta um desafio de desenvolvimento de um banco de dados de gerenciamento de produção de peixes e o respectivo processo de comercialização da empresa.

Em completude da criação e gerenciamento do banco, segue de forma descritiva os passos e demais questionamentos constantes na atividade.

Questão 1 - Criando o banco de dados:
---
    create database PeixeBom_Sao_Francisco

Questão 2 - Criação das tabelas
---

* Tabela 1

      create table Fornecedores(
      id_fornecedor INT PRIMARY KEY AUTO_INCREMENT,
      nome VARCHAR (100),
      telefone VARCHAR (20),
      cidade VARCHAR (60),
      produto_fornecido VARCHAR (80)
      );

* Tabela 2

      create table Tanques(
      id_tanque INT PRIMARY KEY AUTO_INCREMENT,
      identificação VARCHAR(30),
      capacidade INT,
      localizacao VARCHAR(80),
      status VARCHAR(30)
      );

* Tabela 3
    
      create table Produção(
      id_producao INT PRIMARY KEY AUTO_INCREMENT,
      id_tanque INT,
      especie VARCHAR(60),
      quantidade_peixes INT,
      peso_medio DECIMAL (10,2),
      data_registro DATE,
  
      FOREIGN KEY (id_tanque) references Tanques (id_tanque)
      );

 * Tabela 4
   
        create table Clientes(
        id_cliente INT PRIMARY KEY AUTO_INCREMENT,
        nome VARCHAR(100),
        telefone VARCHAR(20),
        cidade VARCHAR (60),
        tipo_cliente VARCHAR(40)
        );

* Tabela 5
    
      create table Vendas(
      id_venda INT PRIMARY KEY AUTO_INCREMENT,
      id_cliente INT,
      especie VARCHAR (60),
      quantidade_kg DECIMAL(10,2),
      preco_kg DECIMAL (10,2),
      valor_total DECIMAL (10,2),
      data_venda DATE,
  
      FOREIGN KEY (id_cliente) references Clientes (id_cliente)
      );
      
Questão 3 - Inserir dados
---

* 1° inserção

      INSERT INTO Fornecedores
        (nome, telefone, cidade, produto_fornecido)
      VALUES
        ('Antonio José', '87999363699', 'Petrolina', 'Peixes'),
        ('Carlos Macedo', '74988222288', 'Juazeiro', 'Ração'),
        ('Fernanda Souza', '8712345678', 'Petrolina', 'Estrutura e equipamentos'),
        ('Paulo Mendes', '8755667788', 'Lagoa Grande', 'Insumos aquáticos')

* 2° inserção

      INSERT INTO Tanques
        (identificação, capacidade, localizacao, status)
      VALUES
        ('Tanque 1', '3000', 'Lote 1', 'Ativo'),
        ('Tanque 2', '3000', 'Lote 2', 'Ativo'),
        ('Tanque 3', '5000', 'Lote 3', 'Ativo'),
        ('Tanque 4', '2000', 'Lote 4', 'Ativo'),
        ('Tanque 5', '1000', 'Lote 5', 'Inativo')

* 3° inserção
    
      INSERT INTO Produção
        (id_tanque, especie, quantidade_peixes, peso_medio, data_registro)
      values
        ('1', 'Tilápia', '450', '100', '2026-11-02'),
        ('2', 'Tambaqui', '326', '350', '2026-11-02'),
        ('3', 'Pacu', '1000', '150', '2026-11-04'),
        ('4', 'Cari', '140', '250', '2026-11-06'),
        ('1', 'Tilápia', '700', '200', '2026-11-06'),
        ('2', 'Tambaqui', '680', '450', '2026-11-06'),
        ('1', 'Tilápia', '1000', '300', '2026-11-08'),
        ('3', 'Pacu', '2500', '300', '2026-11-11')

* 4° inserção

      INSERT INTO Clientes
        (nome, telefone, cidade, tipo_cliente)
      values
        ('José Carlos', '87988881515', 'Petrolina', 'Consumidor individual'),
        ('Nord Haus', '74933225566', 'Juazeiro', 'Restaurante'),
        ('Pedro Augusto', '87998896226', 'Petrolina', 'Peixaria'),
        ('Peixonauta', '87992226454', 'Lagoa Grande', 'Restaurante'),
        ('Ana Cristina', '87991155554', 'Petrolina', 'Consumidor individual'),
        ('Manoel Gomes', '8799997777', 'Rajada', 'Consumidor individual')

* 5° inserção

      INSERT INTO Vendas
        (id_cliente, especie, quantidade_kg, preco_kg, valor_total, data_venda)
      values
        ('1', 'Tilápia','2','32','64.00','2026-11-11'),
        ('2', 'Tambaqui','500','26','13000','2026-11-11'),
        ('3', 'Tambaqui','100','26','2600','2026-11-12'),
        ('4', 'Cari','120','18','2160','2026-11-12'),
        ('6', 'Tilápia','10','32','320','2026-11-12'),
        ('5', 'Tambaqui','10','26','260','2026-11-12'),
        ('4', 'Tilápia','200','32','6400','2026-11-12'),
        ('2', 'Tilápia','460','32','14720','2026-11-12')

Questão 4 - Edição e atualização
---

* 4.1 - Atualização de telefone, no cadastro de fornecedores

      update Fornecedores set telefone = '8798554321' where id_fornecedor = '4'

* 4.2 - Manutenção de um tanque

      update Tanques set status = 'Em manutenção' where id_tanque = '5'

* 4.3 - Quantidade de peixes

      update Produção set quantidade_peixes = '260' where id_producao = '4'

* 4.4 - Reajuste no kg da tilápia

      update Vendas set preco_kg = '35' where id_venda = '1'
      update Vendas set preco_kg = '35' where id_venda = '5'
      update Vendas set preco_kg = '35' where id_venda = '7'
      update Vendas set preco_kg = '35' where id_venda = '8'

      update Vendas set valor_total = '16100' where id_venda = '1'
      update Vendas set valor_total = '16100' where id_venda = '5'
      update Vendas set valor_total = '16100' where id_venda = '7'
      update Vendas set valor_total = '16100' where id_venda = '8'

* 4.5 - Tipo de cadastro

      update Clientes set tipo_cliente = 'Restaurante' where id_cliente = '6'


Questão 5 - SELECT
---

* 5.1 - Fornecedores cadastrados

      select * from Fornecedores
Resposta: Antonio José, Carlos Macedo, Fernando Souza, Paulo Mendes


* 5.2 - Tanques disponíveis

      select * from Tanques where status = 'Ativo'
Resposta: 4


* 5.3 - Tanques em manutenção

      select * from Tanques where status = 'Em manutenção'
Resposta: 1


* 5.4 - Espécies regitradas

      select * from Produção
Resposta: 4


* 5.5 - Clientes que compraram

      select * from Vendas
Resposta: 1 - José Carlos, 2 - Nord Haus, 3 - Pedro Augusto, 4 - Peixonauta, 5 - Ana Cristina, 6 - Manoel Gomes


* 5.6 - Vendas superiores a R$ 1.000,00

      select * from Vendas where valor_total > '1000'
Resposta: 1, 2, 3, 4, 5, 7, 8


* 5.7 - Quantidade total de quilos comercializados

      select sum(quantidade_kg)
      from Vendas
Resposta: 14023
