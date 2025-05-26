# senha-segura-matematica
import hashlib
import random

def gerar_senha(segredo, comprimento=16):
    # Usa uma função hash para criar um número baseado em um segredo
    hash_obj = hashlib.sha256(segredo.encode())
    hash_num = int(hash_obj.hexdigest(), 16)

    # Lista de números primos para reforçar a aleatoriedade
    primos = [2, 3, 5, 7, 11, 13, 17, 19, 23, 29]

    senha = ""
    for _ in range(comprimento):
        hash_num *= random.choice(primos)  # Multiplica por um primo aleatório
        senha += chr(33 + (hash_num % 94))  # Gera um caractere seguro (ASCII entre 33 e 126)

    return senha

# Testando a função
segredo_usuario = "MinhaFraseSecreta123"
senha_segura = gerar_senha(segredo_usuario)
print("Senha Gerada:", senha_segura)
