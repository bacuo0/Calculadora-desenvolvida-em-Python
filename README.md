# Calculadora-desenvolvida-em-Python
Calculadora desenvolvida em Python com suporte a operações matemáticas básicas e avançadas, incluindo adição, subtração, multiplicação, divisão, potência, raiz quadrada, porcentagem e resto da divisão. O projeto conta com validação de entradas, tratamento de erros e histórico de operações.


import math

historico = []


def somar(a, b):
    return a + b


def subtrair(a, b):
    return a - b


def multiplicar(a, b):
    return a * b


def dividir(a, b):
    if b == 0:
        raise ZeroDivisionError("Não é possível dividir por zero.")
    return a / b


def potencia(a, b):
    return a ** b


def raiz_quadrada(a):
    if a < 0:
        raise ValueError("Não existe raiz quadrada real de número negativo.")
    return math.sqrt(a)


def porcentagem(valor, percentual):
    return valor * (percentual / 100)


def resto_divisao(a, b):
    if b == 0:
        raise ZeroDivisionError("Não é possível dividir por zero.")
    return a % b


def ler_numero(mensagem):
    while True:
        try:
            return float(input(mensagem).replace(",", "."))
        except ValueError:
            print("Entrada inválida. Digite um número válido.")


def mostrar_historico():
    if not historico:
        print("\nNenhuma operação realizada.")
        return

    print("\n--- HISTÓRICO ---")
    for i, operacao in enumerate(historico, start=1):
        print(f"{i}. {operacao}")


def adicionar_historico(expressao):
    historico.append(expressao)


while True:
    print("\n==============================")
    print("       CALCULADORA PYTHON")
    print("==============================")

    print("1 - Adição")
    print("2 - Subtração")
    print("3 - Multiplicação")
    print("4 - Divisão")
    print("5 - Potência")
    print("6 - Raiz quadrada")
    print("7 - Porcentagem")
    print("8 - Resto da divisão")
    print("9 - Ver histórico")
    print("10 - Limpar histórico")
    print("0 - Sair")

    opcao = input("\nEscolha uma opção: ").strip()

    try:

        if opcao == "1":
            a = ler_numero("Primeiro número: ")
            b = ler_numero("Segundo número: ")

            resultado = somar(a, b)

            print(f"\nResultado: {resultado}")

            adicionar_historico(
                f"{a} + {b} = {resultado}"
            )

        elif opcao == "2":
            a = ler_numero("Primeiro número: ")
            b = ler_numero("Segundo número: ")

            resultado = subtrair(a, b)

            print(f"\nResultado: {resultado}")

            adicionar_historico(
                f"{a} - {b} = {resultado}"
            )

        elif opcao == "3":
            a = ler_numero("Primeiro número: ")
            b = ler_numero("Segundo número: ")

            resultado = multiplicar(a, b)

            print(f"\nResultado: {resultado}")

            adicionar_historico(
                f"{a} × {b} = {resultado}"
            )

        elif opcao == "4":
            a = ler_numero("Dividendo: ")
            b = ler_numero("Divisor: ")

            resultado = dividir(a, b)

            print(f"\nResultado: {resultado}")

            adicionar_historico(
                f"{a} ÷ {b} = {resultado}"
            )

        elif opcao == "5":
            base = ler_numero("Base: ")
            expoente = ler_numero("Expoente: ")

            resultado = potencia(base, expoente)

            print(f"\nResultado: {resultado}")

            adicionar_historico(
                f"{base} ^ {expoente} = {resultado}"
            )

        elif opcao == "6":
            numero = ler_numero("Número: ")

            resultado = raiz_quadrada(numero)

            print(f"\nResultado: {resultado}")

            adicionar_historico(
                f"√{numero} = {resultado}"
            )

        elif opcao == "7":
            valor = ler_numero("Digite o valor: ")
            percentual = ler_numero("Digite a porcentagem: ")

            resultado = porcentagem(valor, percentual)

            print(
                f"\n{percentual}% de {valor} = {resultado}"
            )

            adicionar_historico(
                f"{percentual}% de {valor} = {resultado}"
            )

        elif opcao == "8":
            a = ler_numero("Primeiro número: ")
            b = ler_numero("Segundo número: ")

            resultado = resto_divisao(a, b)

            print(f"\nResto da divisão: {resultado}")

            adicionar_historico(
                f"{a} % {b} = {resultado}"
            )

        elif opcao == "9":
            mostrar_historico()

        elif opcao == "10":
            historico.clear()
            print("\nHistórico apagado.")

        elif opcao == "0":
            print("\nCalculadora encerrada.")
            break

        else:
            print("\nOpção inválida.")

    except ZeroDivisionError as erro:
        print(f"\nErro: {erro}")

    except ValueError as erro:
        print(f"\nErro: {erro}")

    except OverflowError:
        print("\nErro: resultado muito grande.")
