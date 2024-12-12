# -meu-primeiro-repositorio
 import os

# Classe que representa um usuário
class Usuario:
    def __init__(self, nome, email, idade):
        self.nome = nome
        self.email = email
        self.idade = idade

    def __str__(self):
        return f"{self.nome} | {self.email} | {self.idade} anos"

# Funções para o programa
def listar_usuarios(usuarios):
    if not usuarios:
        print("Não há usuários cadastrados.")
    else:
        print("Usuários cadastrados:")
        for i, usuario in enumerate(usuarios, 1):
            print(f"{i}. {usuario}")

def adicionar_usuario(usuarios):
    nome = input("Digite o nome do usuário: ")
    email = input("Digite o email do usuário: ")
    idade = int(input("Digite a idade do usuário: "))
    usuario = Usuario(nome, email, idade)
    usuarios.append(usuario)
    print(f"Usuário {nome} cadastrado com sucesso!")

def editar_usuario(usuarios):
    listar_usuarios(usuarios)
    try:
        index = int(input("Escolha o número do usuário para editar: ")) - 1
        if 0 <= index < len(usuarios):
            usuario = usuarios[index]
            nome = input(f"Novo nome (atual: {usuario.nome}): ")
            email = input(f"Novo email (atual: {usuario.email}): ")
            idade = int(input(f"Nova idade (atual: {usuario.idade}): "))
            usuario.nome = nome if nome else usuario.nome
            usuario.email = email if email else usuario.email
            usuario.idade = idade if idade else usuario.idade
            print("Usuário editado com sucesso!")
        else:
            print("Usuário inválido.")
    except ValueError:
        print("Por favor, insira um número válido.")

def remover_usuario(usuarios):
    listar_usuarios(usuarios)
    try:
        index = int(input("Escolha o número do usuário para remover: ")) - 1
        if 0 <= index < len(usuarios):
            usuario = usuarios.pop(index)
            print(f"Usuário {usuario.nome} removido com sucesso!")
        else:
            print("Usuário inválido.")
    except ValueError:
        print("Por favor, insira um número válido.")

def menu():
    usuarios = []
    while True:
        print("\n=== IXC Soft - Cadastro de Usuários ===")
        print("1. Listar usuários")
        print("2. Adicionar usuário")
        print("3. Editar usuário")
        print("4. Remover usuário")
        print("5. Sair")
        
        opcao = input("Escolha uma opção (1-5): ")

        if opcao == "1":
            listar_usuarios(usuarios)
        elif opcao == "2":
            adicionar_usuario(usuarios)
        elif opcao == "3":
            editar_usuario(usuarios)
        elif opcao == "4":
            remover_usuario(usuarios)
        elif opcao == "5":
            print("Saindo... Até logo!")
            break
        else:
            print("Opção inválida. Tente novamente.")

if __name__ == "__main__":
    menu()
