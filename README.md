# 🛍️ Sistema Administrativo: Controle de Estoque, Insumos e Análise de Lucro

Este projeto tem como objetivo desenvolver um **sistema web de gerenciamento comercial** para **lojas de vestuário**, reunindo em uma única plataforma funções essenciais como **controle de produtos, vendas, entregas e usuários**.

---

## 👥 Integrantes do Grupo

- Ayssa Gabriely Andrade da Silva  
- Enrico Azevedo de Carvalho  
- José Rafael Alejandro Casique Reyes
- Miguel Miada dos Santos
- Mariel Alejandra de Jesus Casique Reyes
- Pedro Henrique Alencar Gonçalves Monteiro  
- Rita Gabrieli Rodrigues da Cunha  
- 
- **Orientador:** Prof. Me. José Picovsky  

---

## 🧠 Tecnologias Utilizadas

- **Frontend:** React + TypeScript  
- **Prototipagem:** Figma  
- **Banco de Dados:** MySQL  
- **Ferramentas:** Node.js, HTML5, CSS3  
- **Versionamento:** Git e GitHub  

---

## 📐 Modelagem do Banco de Dados
O banco de dados foi desenvolvido para garantir a integridade e o relacionamento entre as informações do sistema.  
A modelagem foi dividida em duas etapas: o *Diagrama Entidade-Relacionamento (DER)* e o *Modelo Lógico*.

### Modelo Conceitual(DER) ![modelo conceitual](https://github.com/user-attachments/assets/8a28fd72-1023-4ff3-98bf-70ee05f22b30)


### Modelo Lógico![modelo lógico](https://github.com/user-attachments/assets/0df5622f-d267-4f28-8314-8ade71dc3c2d)
## 💾 Script SQL — Criação das Tabelas

```sql
-- CRIAÇÃO DAS TABELAS DO BANCO DE DADOS

CREATE TABLE CLIENTE (
    ID_CLIENTE NUMBER PRIMARY KEY,
    NOME VARCHAR2(100) NOT NULL,
    SOBRENOME VARCHAR2(100),
    EMAIL VARCHAR2(100),
    ENDERECO VARCHAR2(200),
    DATA_REGISTRO DATE
);

CREATE TABLE TELEFONE (
    ID_TEL NUMBER PRIMARY KEY,
    TEL1 VARCHAR2(20),
    TEL2 VARCHAR2(20),
    ID_CLIENTE NUMBER,
    CONSTRAINT FK_TELEFONE_CLIENTE FOREIGN KEY (ID_CLIENTE)
        REFERENCES CLIENTE(ID_CLIENTE)
);

CREATE TABLE VENDEDOR (
    ID_VENDEDOR NUMBER PRIMARY KEY,
    NOME VARCHAR2(100) NOT NULL,
    SOBRENOME VARCHAR2(100),
    EMAIL VARCHAR2(100),
    ENDERECO VARCHAR2(200),
    TELEFONE VARCHAR2(20),
    DATA_CONTRATACAO DATE
);

CREATE TABLE PRODUTO (
    ID_PRODUTO NUMBER PRIMARY KEY,
    NOME_PRODUTO VARCHAR2(100) NOT NULL,
    DESCRICAO VARCHAR2(255),
    CATEGORIA VARCHAR2(100),
    TAMANHO VARCHAR2(50),
    COR VARCHAR2(50),
    PRECO NUMBER(10,2),
    DATA_INGRESSO DATE,
    ESTOQUE_DISPONIVEL NUMBER
);

CREATE TABLE PEDIDO (
    ID_PEDIDO NUMBER PRIMARY KEY,
    DATA_PEDIDO DATE,
    ENDERECO VARCHAR2(200),
    QUANTIDADE NUMBER,
    ID_CLIENTE NUMBER,
    ID_VENDEDOR NUMBER,
    CONSTRAINT FK_PEDIDO_CLIENTE FOREIGN KEY (ID_CLIENTE)
        REFERENCES CLIENTE(ID_CLIENTE),
    CONSTRAINT FK_PEDIDO_VENDEDOR FOREIGN KEY (ID_VENDEDOR)
        REFERENCES VENDEDOR(ID_VENDEDOR)
);

CREATE TABLE DETALHE_PEDIDO (
    ID_DETALHE NUMBER PRIMARY KEY,
    ID_PEDIDO NUMBER,
    ID_PRODUTO NUMBER,
    QUANTIDADE NUMBER,
    PRECO_UNITARIO NUMBER(10,2),
    SUBTOTAL NUMBER(10,2),
    CONSTRAINT FK_DETALHE_PEDIDO FOREIGN KEY (ID_PEDIDO)
        REFERENCES PEDIDO(ID_PEDIDO),
    CONSTRAINT FK_DETALHE_PRODUTO FOREIGN KEY (ID_PRODUTO)
        REFERENCES PRODUTO(ID_PRODUTO)
);

CREATE TABLE REPARTIDOR (
    ID_REPARTIDOR NUMBER PRIMARY KEY,
    NOME VARCHAR2(100) NOT NULL,
    SOBRENOME VARCHAR2(100),
    VEICULO VARCHAR2(100),
    PLACA VARCHAR2(20)
);

CREATE TABLE ENTREGA (
    ID_ENTREGA NUMBER PRIMARY KEY,
    DATA_ENTREGA DATE,
    ENDERECO_ENTREGA VARCHAR2(200),
    ESTADO_ENTREGA VARCHAR2(50),
    COMPROVANTE_ENTREGA VARCHAR2(100),
    ID_PEDIDO NUMBER,
    ID_REPARTIDOR NUMBER,
    CONSTRAINT FK_ENTREGA_PEDIDO FOREIGN KEY (ID_PEDIDO)
        REFERENCES PEDIDO(ID_PEDIDO),
    CONSTRAINT FK_ENTREGA_REPARTIDOR FOREIGN KEY (ID_REPARTIDOR)
        REFERENCES REPARTIDOR(ID_REPARTIDOR)
);



---

## 💻 Telas do Sistema

### Telas <img width="4880" height="1870" alt="figma-pi 2 0 (2)" src="https://github.com/user-attachments/assets/5a7ddfa2-d7b3-4b35-b94d-b26ad2885df2" />


---

## ⚙️ Funcionalidades

- Cadastro e controle de produtos  
- Registro de vendas  
- Gestão de entregas e clientes  
- Controle de estoque em tempo real  
- Relatórios gerenciais  
- Controle de acesso por usuários  

---

## 🧩 Estrutura do Projeto
📦 pi-fam
├── database/         → Modelagem e scripts SQL
├── frontend/         → Prototipagem e imagens das telas
├── docs/             → Artigo e documentação
├── assets/           → Logos e imagens gerais
└── README.md         → Descrição do projeto

## 📚 Documentação

- [📄 Artigo do Projeto](docs/DOC-Artigo fam.pdf)

---

## 🚀 Objetivo

A solução busca *agilizar o processo de gestão comercial, promovendo **organização, eficiência e segurança* nas operações diárias das lojas.  
O sistema é totalmente responsivo e pode ser acessado por diferentes dispositivos.

---

## 🏁 Resultado Final

O sistema demonstrou-se eficaz na *automação das rotinas comerciais*, otimizando o controle de produtos, vendas e entregas, além de oferecer suporte à tomada de decisões estratégicas.
