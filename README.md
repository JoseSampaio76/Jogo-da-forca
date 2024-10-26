# Jogo-da-forca
Brincadeira de infância
import random

# Lista de palavras para o jogo
palavras = ["python", "desenvolvimento", "tecnologia", "computador", "programacao"]

# Escolhe uma palavra secreta aleatoriamente
palavra_secreta = random.choice(palavras)
letras_acertadas = ["_"] * len(palavra_secreta)  # Inicia a lista com "_" para cada letra
letras_tentadas = []  # Lista de letras tentadas pelo jogador
tentativas_erradas = 0
max_tentativas = 6  # Número máximo de tentativas

# Função para exibir o estado atual do jogo
def exibir_jogo():
    print("\nPalavra: " + " ".join(letras_acertadas))
    print("Tentativas restantes:", max_tentativas - tentativas_erradas)
    print("Letras tentadas:", ", ".join(letras_tentadas))

# Loop do jogo
while "_" in letras_acertadas and tentativas_erradas < max_tentativas:
    exibir_jogo()

    # Solicita uma letra ao jogador
    letra = input("Digite uma letra: ").lower()

    # Verifica se a letra já foi tentada
    if letra in letras_tentadas:
        print("Você já tentou essa letra! Tente outra.")
        continue  # Pula para a próxima iteração do loop

    letras_tentadas.append(letra)  # Adiciona a letra na lista de tentativas

    # Processa a jogada
    if letra in palavra_secreta:
        # Se a letra está na palavra secreta, revelar todas as ocorrências
        for i, char in enumerate(palavra_secreta):
            if char == letra:
                letras_acertadas[i] = letra  # Substitui "_" pela letra correta
    else:
        # Se a letra não estiver na palavra, incrementar tentativas erradas
        tentativas_erradas += 1

# Verificação final: vitória ou derrota
if "_" not in letras_acertadas:
    print("\nParabéns, você venceu! A palavra era:", palavra_secreta)
else:
    print("\nQue pena, você perdeu! A palavra era:", palavra_secreta)
