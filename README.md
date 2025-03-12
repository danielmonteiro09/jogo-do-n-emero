class GameAgent:
    def __init__(self, secret_number, max_attempts=10):
        self.secret_number = secret_number
        self.max_attempts = max_attempts
        self.attempts = 0
        self.state = "Esperando tentativa"
        self.history = []  # Histórico de tentativas
    
    def make_guess(self, guess):
        self.attempts += 1
        self.history.append(guess)
        
        if guess == self.secret_number:
            self.state = "Acertou!"
            return "Parabéns! Você acertou o número."
        elif self.attempts >= self.max_attempts:
            self.state = "Fim do jogo"
            return f"Game Over! O número era {self.secret_number}."
        elif guess < self.secret_number:
            self.state = "Tentativa errada (muito baixo)"
            return "O número é maior. Tente novamente."
        else:
            self.state = "Tentativa errada (muito alto)"
            return "O número é menor. Tente novamente."

        self.state = "Tentativa errada"
            return "O número é um número primo. Tente novamente."
        else:
            self.state = "Tentativa errada"
            return "O número é um número composto"

# Criando um agente com um número secreto entre 1 a 70
agent = GameAgent(secret_number=random.randint(1, 70))

while agent.state not in ["Acertou!", "Fim do jogo"]:
    guess = int(input("Digite um número: "))
    print(agent.make_guess(guess))
