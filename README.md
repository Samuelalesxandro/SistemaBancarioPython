# SistemaBancarioPython
criei um sistema bancário  a partir da linguagem python
class SistemaBancario:
    def __init__(self, saldo_inicial):
        self.saldo = saldo_inicial
        self.depositos = []
        self.saques = []
        self.transferencias = []

    def depositar(self, valor):
        if valor > 0:
            self.saldo += valor
            self.depositos.append(valor)
            print(f'Depósito de R${valor:.2f} realizado com sucesso.')
        else:
            print('O valor do depósito deve ser positivo.')

    def sacar(self, valor):
        if valor > 0:
            if self.saldo >= valor:
                self.saldo -= valor
                self.saques.append(valor)
                print(f'Saque de R${valor:.2f} realizado com sucesso.')
            else:
                print('Saldo insuficiente para realizar o saque.')
        else:
            print('Valor de saque inválido.')

    def consultar_saldo(self):
        print(f'Seu saldo atual é de R${self.saldo:.2f}')

    def transferencia(self, valor, destinatario):
        if valor > 0:
            if self.saldo >= valor:
                self.saldo -= valor
                self.transferencias.append(valor)
                destinatario.depositar(valor)
                print(f'Transferência de R${valor:.2f} realizada para {destinatario.nome} com sucesso.')
            else:
                print('Saldo insuficiente para realizar a transferência.')
        else:
            print('Valor de transferência inválido.')

    def pagar_conta(self, valor, descricao):
        if valor > 0:
            if self.saldo >= valor:
                self.saldo -= valor
                print(f'Conta de {descricao} no valor de R${valor:.2f} paga com sucesso.')
            else:
                print('Saldo insuficiente para pagar a conta.')
        else:
            print('Valor de conta inválido.')

    def recarga_celular(self, numero, valor):
        if valor > 0:
            if self.saldo >= valor:
                self.saldo -= valor
                print(f'Recarga de celular para o número {numero} no valor de R${valor:.2f} realizada com sucesso.')
            else:
                print('Saldo insuficiente para realizar a recarga.')
        else:
            print('Valor de recarga inválido.')

    def extrato(self):
        print('--- Extrato ---')
        print('Depósitos:')
        for deposito in self.depositos:
            print(f'R${deposito:.2f}')
        print('Saques:')
        for saque in self.saques:
            print(f'R${saque:.2f}')
        print('Transferências:')
        for transferencia in self.transferencias:
            print(f'R${transferencia:.2f}')
        print(f'Saldo atual: R${self.saldo:.2f}')


# Exemplo de uso interativo:
sistema = SistemaBancario(3500)

print("Seu saldo inicial é de R$3500.")

while True:
    print("\nOpções:")
    print("1. Depositar")
    print("2. Sacar")
    print("3. Consultar Saldo")
    print("4. Transferência")
    print("5. Pagar Conta")
    print("6. Recarga de Celular")
    print("7. Consultar Financiamento de Imóvel")
    print("8. Consultar Financiamento de Veículo")
    print("9. Extrato")
    print("10. Sair")

    escolha = input("Escolha uma opção: ")

    if escolha == "1":
        valor_deposito = float(input("Digite o valor do depósito: "))
        sistema.depositar(valor_deposito)
    elif escolha == "2":
        valor_saque = float(input("Digite o valor do saque: "))
        sistema.sacar(valor_saque)
    elif escolha == "3":
        sistema.consultar_saldo()
    elif escolha == "4":
        valor_transferencia = float(input("Digite o valor da transferência: "))
        destinatario = input("Digite o nome do destinatário: ")
        # Aqui você precisaria ter uma instância do sistema bancário do destinatário para fazer a transferência.
        # Exemplo: sistema.transferencia(valor_transferencia, destinatario)
        print("Opção não implementada.")
    elif escolha == "5":
        valor_conta = float(input("Digite o valor da conta a ser paga: "))
        descricao_conta = input("Digite a descrição da conta: ")
        sistema.pagar_conta(valor_conta, descricao_conta)
    elif escolha == "6":
        numero_celular = input("Digite o número de celular: ")
        valor_recarga = float(input("Digite o valor da recarga: "))
        sistema.recarga_celular(numero_celular, valor_recarga)
    elif escolha == "7":
        sistema.consultar_financiamento_imovel()
    elif escolha == "8":
        sistema.consultar_financiamento_veiculo()
    elif escolha == "9":
        sistema.extrato()
    elif escolha == "10":
        print("Saindo do sistema bancário...")
        break
    else:
        print("Opção inválida. Por favor, escolha uma opção válida.")
esse foi o codigo que utilizei para a criação desse sistema bancario
