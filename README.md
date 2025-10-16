# 🚗 Projeto EER para Oficina Mecânica - Modelo Conceitual

Modelo conceitual de banco de dados desenvolvido para um **sistema de gestão de oficina mecânica**, com foco no controle de **Ordens de Serviço (OS)**, equipes, serviços e peças utilizadas.

---

## 🧰 Sobre o Projeto

Este projeto apresenta o **modelo conceitual** de um sistema voltado à organização de uma **oficina mecânica**, onde clientes levam seus veículos para **manutenções, consertos e revisões**.  

O modelo foi construído no **MySQL Workbench**, com base na proposta do desafio da plataforma **DIO**, representando de forma clara as relações entre **clientes, veículos, ordens de serviço, equipes de mecânicos, serviços realizados e peças aplicadas**.

---

## 🧩 Contexto da Modelagem

Cada **cliente** pode ter um ou mais **veículos** cadastrados.  
Quando um veículo é encaminhado para manutenção, é gerada uma **Ordem de Serviço (OS)**, associada a uma **equipe de mecânicos** responsável pela execução.  

As **OS** registram:
- Data de emissão e conclusão  
- Valor total  
- Status  
- Equipe responsável  
- Veículo atendido  

Cada OS pode incluir **diversos serviços e peças**, compondo o valor final do atendimento.  
Os **mecânicos** têm seus dados individuais (código, nome, endereço e especialidade) e podem participar de **mais de uma equipe**.

---

## 🧠 Entidades e Atributos Principais

### 🧍‍♂️ Cliente
- `idCliente` *(PK)*  
- `Nome`  
- `Endereço`  
- `Telefone`  

### 🚘 Veículo
- `idVeiculo` *(PK)*  
- `Placa`  
- `Modelo`  
- `Ano`  
- `Cliente_idCliente` *(FK)*  

### 📄 Ordem de Serviço
- `idOrdemServico` *(PK)*  
- `Data_emissão`  
- `Data_conclusão`  
- `Valor_total`  
- `Status`  
- `Veiculo_idVeiculo` *(FK)*  
- `Equipe_idEquipe` *(FK)*  

### 🧑‍🔧 Equipe
- `idEquipe` *(PK)*  
- `Nome_equipe`  

### 👨‍🏭 Mecânico
- `idMecanico` *(PK)*  
- `Nome`  
- `Endereço`  
- `Especialidade`  

### 🛠️ Serviço
- `idServico` *(PK)*  
- `Descrição`  
- `Mao_de_obra_valor`  

### 🔩 Peça
- `idPeca` *(PK)*  
- `Descrição`  
- `Valor_unitário`  

### 🔗 Tabelas Associativas
- **OS** *(Serviço/Ordem de Serviço)* → relaciona ordens e serviços, com a quantidade de cada serviço.  
- **Peça/Ordem de Serviço** → relaciona ordens e peças, com a quantidade utilizada.  
- **Equipe/Mecânico** → define quais mecânicos fazem parte de cada equipe.  

---

## 🧮 Relacionamentos

- **Cliente 1:N Veículo**  
- **Veículo 1:N Ordem de Serviço**  
- **Ordem de Serviço N:N Serviço** *(via OS)*  
- **Ordem de Serviço N:N Peça** *(via Peça/Ordem de Serviço)*  
- **Ordem de Serviço N:1 Equipe**  
- **Equipe N:N Mecânico** *(via Equipe/Mecânico)*  

---

## 💡 Pontos de Destaque

- Um **cliente** pode possuir **vários veículos**.  
- Cada **veículo** pode ter diversas **ordens de serviço** registradas.  
- Uma **OS** pode envolver **vários serviços e peças**.  
- **Mecânicos** podem participar de **múltiplas equipes**.  
- O **valor total da OS** é a soma de **serviços + peças**.  

---

## 🛠️ Ferramentas Utilizadas

- **MySQL Workbench** → modelagem conceitual e criação do diagrama EER.  
- **MySQL** → implementação das tabelas e definição das *constraints*.  

---

## 📁 Estrutura do Repositório
📦 projeto-eer-oficina-mecanica
┣ README.md
┣ diagrama_oficina.png # Diagrama EER exportado
┗ modelo_oficina.mwb # Arquivo do MySQL Workbench


---

## ✍️ Autoria

Desenvolvido por **Cauane Melo Mamede de Souza**  
Projeto criado com base no desafio da plataforma **DIO**, com aprimoramentos e personalização no modelo e na documentação.
