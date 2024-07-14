Diario Interativo - analisando sentimentos ;)

## 📒 Descrição
Breve descrição do seu projeto.
Coleta de Dados: Permitir que o usuário insira suas entradas de diário.

Análise de Sentimentos: Usar uma biblioteca como TextBlob ou VADER para analisar o sentimento das entradas.

Armazenamento de Dados: Guardar as entradas e os resultados da análise em um arquivo ou banco de dados.

Geração de Relatórios: Fornecer insights sobre as emoções ao longo do tempo, como gráficos ou resumos.

## 🤖 Tecnologias Utilizadas
Liste as IAs Generativas e outras ferramentas usadas
CHATGPT, PYTHON, 

## 🧐 Processo de Criação
Descreva como você criou o conteúdo.
Solicitei idéias ao chatgpt , ele me trouxe uma lista e escolhi um, e comecei o desenvolmento 

## 🚀 Resultados
Apresente os resultados do seu projeto


# analise-de-sentimento
desafioDio-analise de sentimento 

Coleta de Dados: Permitir que o usuário insira suas entradas de diário.

Análise de Sentimentos: Usar uma biblioteca como TextBlob ou VADER para analisar o sentimento das entradas.

Armazenamento de Dados: Guardar as entradas e os resultados da análise em um arquivo ou banco de dados.

Geração de Relatórios: Fornecer insights sobre as emoções ao longo do tempo, como gráficos ou resumos.

Opções de Entrada.

- Positivas:

"Hoje foi um dia incrível! Fui ao parque e passei tempo com amigos."
"Sinto-me muito feliz e realizado com as conquistas que tive esta semana."
"O sol estava brilhando, e a energia positiva me inspirou a ser produtivo."

- Neutras:
  
"Hoje trabalhei em alguns projetos e fiz algumas tarefas domésticas."
"Comi uma nova receita que encontrei online."
"Fui ao supermercado e comprei algumas coisas."


-Negativas:

"Hoje foi um dia estressante no trabalho, não consegui realizar tudo que planejei."
"Estou me sentindo triste e desmotivado ultimamente."
"A chuva constante me deixou um pouco desanimado."



from textblob import TextBlob
import matplotlib.pyplot as plt
import datetime

# Função para analisar o sentimento
def analisar_sentimento(texto):
    analise = TextBlob(texto)
    return analise.sentiment.polarity  # Retorna um valor entre -1 (negativo) e 1 (positivo)

# Função para adicionar entrada ao diário
def adicionar_entrada(diary):
    entrada = input("Digite sua entrada de diário: ")
    data = datetime.datetime.now().strftime("%Y-%m-%d %H:%M:%S")
    sentimento = analisar_sentimento(entrada)
    diary.append((data, entrada, sentimento))

# Função para gerar relatório
def gerar_relatorio(diary):
    datas = [entry[0] for entry in diary]
    sentimentos = [entry[2] for entry in diary]
    
    plt.figure(figsize=(10, 5))
    plt.plot(datas, sentimentos, marker='o')
    plt.title("Análise do Humor ao Longo do Tempo")
    plt.xlabel("Data")
    plt.ylabel("Sentimento")
    plt.xticks(rotation=45)
    plt.axhline(0, color='red', linestyle='--')  # Linha para indicar o sentimento neutro
    plt.show()

# Diário
diary = []

# Loop principal
while True:
    print("\n1. Adicionar entrada ao diário")
    print("2. Gerar relatório")
    print("3. Sair")
    escolha = input("Escolha uma opção: ")

    if escolha == '1':
        adicionar_entrada(diary)
    elif escolha == '2':
        gerar_relatorio(diary)
    elif escolha == '3':
        break
    else:
        print("Opção inválida, tente novamente.")
