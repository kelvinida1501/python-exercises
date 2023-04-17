## Exercício 1

```python
número = input ("Digite um número:")
número = int(número)

if número % 2 == 0:
    print(número, "é par")
elif número % 2 != 0:
    print(número, "é ímpar")
else:
    print("Erro")
```

## Exercício 2

```python
palavra = input ("Digite uma palavra:")
palavra = str(palavra)

if palavra[:] == palavra [::-1]:
    print(palavra, "é um palíndromo")
else:
    print(palavra, "não é um palíndromo")
```

## Exercício 3

```python
while True:
    print("pedra - papel - tesoura")
    jogador1 = input("Jogador 1 digite sua escolha:")
    resposta1 = str(jogador1)
    jogador2 = input("Jogador 2 digite sua escolha:")
    resposta2 = str(jogador2)

    if resposta1 == resposta2:
        print("Empate!")
    elif resposta1 == 'pedra' and resposta2 == 'papel':
        print("Jogador 2 ganhou com", resposta2, "x", resposta1, "de Jogador 1")
    elif resposta1 == 'papel' and resposta2 == 'pedra':
        print("Jogador 1 ganhou com", resposta1, "x", resposta2, "de Jogador 2")
    elif resposta1 == 'pedra' and resposta2 == 'tesoura':
        print("Jogador 1 ganhou com", resposta1, "x", resposta2, "de Jogador 2")
    elif resposta1 == 'tesoura' and resposta2 == 'pedra':
        print("Jogador 2 ganhou com", resposta2, "x", resposta1, "de Jogador 1")
    elif resposta1 == 'papel' and resposta2 == 'tesoura':
        print("Jogador 2 ganhou com", resposta2, "x", resposta1, "de Jogador 1")
    elif resposta1 == 'tesoura' and resposta2 == 'papel':
        print("Jogador 1 ganhou com", resposta1, "x", resposta2, "de Jogador 2")
    else:
        print("Por favor digite pedra, papel ou tesoura")

    sair = input("Quer continuar jogando? (s/n)")
    sair = str(sair)

    if sair != 's':
        break
```

## Exercício 4

```python
import random 

while True:
    numero = random.randint(1,9)
    print('O programa gerou um número!')
    resposta = input('Qual numero você acha que é?')
    resposta = int(resposta)

    if resposta == numero:
        print('Parabéns você acertou o número era', str(numero))
        sair = input("Quer continuar jogando? (s/n)")
        if sair != 's':
            break
    elif resposta > numero:
        print('O número que você inseriu é maior do que o programa')
    else:
        print('O número que você inseriu é menor do que o programa')

```

## Exercício 5

```python
def remover_copia(remover):
    sem_copia=list(remover)
    sem_copia=set(remover)
    return sem_copia
    
nomes = ['Ricardo','Roberto','Roberto','Ricardo','Matheus','Mateus','Matheus','Cléber']
sem_copia = remover_copia(nomes)
print(sem_copia)

```

## Exercício 6

```python
from random import choice
import string

qtd_digitos = input("Quantos dígitos você quer na sua senha? ")
qtd_digitos = int(qtd_digitos)
tipo_da_senha = input("Senha fraca, média ou forte? ")
caracteres_fracos = string.ascii_letters 
caracteres_médios = string.ascii_letters + string.digits 
caracteres_fortes = string.ascii_letters + string.digits + string.punctuation

senha_aleatoria = ''

if tipo_da_senha == 'fraca':
    for i in range(qtd_digitos):
        senha_aleatoria += choice(caracteres_fracos)
        
elif tipo_da_senha == 'média':
    for i in range(qtd_digitos):
        senha_aleatoria += choice(caracteres_médios)
        
elif tipo_da_senha == 'forte':
    for i in range(qtd_digitos):
        senha_aleatoria += choice(caracteres_fortes)

print("A senha gerada é: ", senha_aleatoria)
```

## Exercício 7

```python
with open('names.txt', 'r') as arquivo:
    nomes = arquivo.readlines()

repetições = {}
for rep in nomes:
    if rep not in repetições:
        repetições[rep] = 1
    else:
        repetições[rep] += 1

for rep, quantidade in repetições.items():
    print(f'O nome {rep} aparece {quantidade} vezes no arquivo.')
```

## Exercício 8

```python
import requests
from bs4 import BeautifulSoup

url = 'https://www.nytimes.com/'
r= requests.get(url)
raw_html = r.text

soup = BeautifulSoup(raw_html)
title = soup.find("title").string

for artigos in soup.find_all('article'):
    headline = artigos.find('h3')
    if headline:
        print(headline.text())

```

## Exercício 9

```python
import requests
from bs4 import BeautifulSoup

url = 'https://www.nytimes.com/'
r = requests.get(url)
raw_html = r.text

soup = BeautifulSoup(raw_html, 'html.parser')
title = soup.find("title").string

with open("hard-coded.txt", "w") as open_file:
    for artigos in soup.find_all('article'):
        headline = artigos.find('h2')
        if headline:
            open_file.write(headline.text() + "\n")
```


