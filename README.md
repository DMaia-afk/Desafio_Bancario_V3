# 💳 Desafio Sistema Bancário DIO V3  

Bem-vindo à terceira versão do sistema bancário desenvolvido para o bootcamp da DIO! Agora, o projeto está ainda mais robusto, orientado a objetos e com recursos de autenticação, histórico de transações e múltiplas contas por cliente.  

---  

## 🚀 Novidades da Versão 3  

- **Orientação a Objetos:** Todo o sistema foi reestruturado usando classes para clientes, contas e transações.  
- **Login Seguro:** Acesso do cliente via CPF e palavra secreta.  
- **Múltiplas Contas:** Um cliente pode possuir várias contas correntes.  
- **Histórico Detalhado:** Todas as operações (depósitos, saques) são registradas e podem ser consultadas no extrato.  
- **Limite de Saques:** Controle de limite de valor e quantidade de saques diários.  
- **Validações Aprimoradas:** CPF único, dados obrigatórios e validação de entrada.  

---  

## 🏗️ Estrutura do Projeto  

A estrutura do projeto foi organizada da seguinte forma:  

- **classes/**: Módulo contendo as classes principais do sistema (Cliente, Conta, Transacao).  
- **main.py**: Script principal para execução do sistema.  
- **README.md**: Documentação do projeto.  

---  

## 📚 Instruções de Uso  

1. **Cadastro de Cliente**: Utilize a classe `Cliente` para criar um novo cliente, informando nome, data de nascimento, CPF e endereço. O CPF deve ser único.  
2. **Abertura de Conta**: Com o cliente cadastrado, utilize a classe `Conta` para criar uma nova conta corrente, vinculando-a ao cliente pelo CPF.  
3. **Depósitos e Saques**: Realize operações de depósito e saque utilizando os métodos da classe `Conta`. O sistema controla o saldo e o histórico de transações.  
4. **Consulta de Extrato**: Acesse o extrato da conta para visualizar o histórico de transações realizadas.  

---  

## 🛠️ Exemplo de Implementação  

```python  
# classes/cliente.py  

class Cliente:  
    def __init__(self, nome, data_nascimento, cpf, endereco):  
        self.nome = nome  
        self.data_nascimento = data_nascimento  
        self.cpf = cpf  
        self.endereco = endereco  

# classes/conta.py  

class Conta:  
    def __init__(self, numero_conta, cliente):  
        self.numero_conta = numero_conta  
        self.cliente = cliente  
        self.saldo = 0  
        self.historico_transacoes = []  

    def depositar(self, valor):  
        self.saldo += valor  
        self.historico_transacoes.append(f"Depósito: R${valor}")  

    def sacar(self, valor):  
        if valor > self.saldo:  
            print("❌ Saldo insuficiente!")  
        else:  
            self.saldo -= valor  
            self.historico_transacoes.append(f"Saque: R${valor}")  

    def extrato(self):  
        print(f"\n📜 Extrato da Conta {self.numero_conta}:")  
        print(f"Saldo atual: R${self.saldo}")  
        print("Histórico de Transações:")  
        for transacao in self.historico_transacoes:  
            print(f"- {transacao}")  

# main.py  

from classes.cliente import Cliente  
from classes.conta import Conta  

# Cadastro de um novo cliente  
cliente1 = Cliente("João Silva", "01/01/1990", "12345678900", "Rua das Flores, 123 - Centro - São Paulo/SP")  

# Abertura de uma nova conta para o cliente  
conta1 = Conta(1, cliente1)  

# Realizando operações na conta  
conta1.depositar(1000)  
conta1.sacar(200)  

# Consultando extrato da conta  
conta1.extrato()  
```  

---  

## ⚙️ Requisitos Técnicos  

- Python 3.8 ou superior  
- Bibliotecas: `datetime`, `getpass` (para entrada segura de senha)  

---  

## 📦 Instalação e Execução  

1. Clone o repositório: `git clone <URL_DO_REPOSITORIO>`  
2. Acesse a pasta do projeto: `cd desafio-sistema-bancario-dio-v3`  
3. Instale as dependências (se houver): `pip install -r requirements.txt`  
4. Execute o sistema: `python main.py`  

---  

## 📝 Considerações Finais  

Esta versão do sistema bancário DIO está mais segura e eficiente, aproveitando os conceitos de orientação a objetos para uma melhor organização do código. Sinta-se à vontade para explorar e aprimorar o sistema conforme necessário.  

---  

**Desenvolvido por [Diego Maia](https://www.linkedin.com/in/diego-maia-7259542aa/)**  
