# data_center.py
import csv
# Função para ler o arquivo CSV e retornar uma lista de preços
def ler_precos_do_csv(nome_arquivo):
    precos = []
    with open(nome_arquivo, mode='r') as file:
        csv_reader = csv.DictReader(file)
        for row in csv_reader:
            precos.append(float(row['Preco']))  # Supondo que a coluna de preços no CSV é chamada 'Preco'
    return precos

# Função para calcular a média dos preços
def calcular_media(precos):
    return sum(precos) / len(precos) if precos else 0

# Função para identificar o servidor mais caro e o mais barato
def identificar_servidores_extremos(precos):
    if not precos:
        return None, None
    mais_caro = max(precos)
    mais_barato = min(precos)
    return mais_caro, mais_barato

# Caminho para o arquivo CSV
nome_arquivo = 'precos_servidores.csv'

# Ler os preços do arquivo CSV
precos = ler_precos_do_csv(nome_arquivo)

# Calcular a média dos preços
media_precos = calcular_media(precos)
print(f'Média dos preços dos servidores: R${media_precos:.2f}')

# Identificar o servidor mais caro e o mais barato
mais_caro, mais_barato = identificar_servidores_extremos(precos)
print(f'Servidor mais caro: R${mais_caro:.2f}')
print(f'Servidor mais barato: R${mais_barato:.2f}')
