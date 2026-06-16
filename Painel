import sys  # Importa funções do sistema (usado no flush do print)
import time  # Importa funções de tempo (usado para criar os delays)

# =====================================================================
# BANCO DE DADOS EM MEMÓRIA
# =====================================================================
lista_de_agentes = []  # Armazena os dicionários com dados dos agentes
lista_de_evidencias = []  # Armazena os textos das evidências registradas


# =====================================================================
# FUNÇÕES VISUAIS E DE EXIBIÇÃO
# =====================================================================
def digitar(texto, delay=0.03):
    """Cria o efeito 'typewriter' (máquina de escrever) no terminal."""
    for char in texto:
        print(char, end="", flush=True)
        time.sleep(delay)
    print()  # Pula uma linha ao final do texto


def pausa(segundos=2):
    """Gera uma interrupção temporária antes da próxima ação."""
    time.sleep(segundos)


def apresentacao():
    """Mostra o cabeçalho de boas-vindas inicial."""
    print("\n" + "=" * 53)
    digitar(
        "BEM-VINDO AO SEU NOVO PAINEL DE CONTROLE DE PERÍCIA",
        delay=0.03,
    )
    print("=" * 53 + "\n")
    pausa(1)


def menu():
    """Desenha as opções do painel central na tela."""
    print("\n" + "=" * 53)
    print("              SISTEMA CENTRAL DE PERÍCIA")
    print("=" * 53)
    print(" [1] -> Cadastrar Nova Evidência")
    print(" [2] -> Ver Banco de Evidências")
    print(" [3] -> Cadastrar Novo Agente")
    print(" [4] -> Ver Agentes no Sistema")
    print(" [5] -> Sair do Sistema")
    print("=" * 53)


# =====================================================================
# O PROGRAMA COMEÇA A EXECUTAR AQUI
# =====================================================================

# Faz a abertura estilosa rodar UMA vez antes de entrar no menu
apresentacao()

# LOOP PRINCIPAL DE NAVEGAÇÃO
while True:
    menu()  # Exibe o menu a cada ciclo do loop

    print()
    digitar(">>> Qual das opções você escolhe?", delay=0.03)
    print()

    # Captura a escolha do usuário e remove espaços extras com .strip()
    resposta = input("Digite aqui (1, 2, 3, 4, 5): ").strip()

    # -----------------------------------------------------------------
    # PAINEL 1: CADASTRO DE EVIDÊNCIA
    # -----------------------------------------------------------------
    if resposta == "1":
        print()
        digitar(
            "Digite sua nova evidência. Exemplos: local, data, dia, horário, nome",
            delay=0.03,
        )
        resposta1 = input("» ")

        lista_de_evidencias.append(resposta1)  # Salva o texto na lista
        print()
        digitar(">>> Evidência salva com sucesso! <<<", delay=0.03)

        print()
        input("Pressione [ENTER] para retornar ao Menu Principal...")
        continue  # Corta o bloco aqui e força o retorno para o topo do loop

    # -----------------------------------------------------------------
    # PAINEL 2: VISUALIZAR EVIDÊNCIAS
    # -----------------------------------------------------------------
    elif resposta == "2":
        print("\n" + "-" * 50)
        digitar("=== BANCO DE DADOS DE EVIDÊNCIAS ===", delay=0.03)
        print("-" * 50)

        # Checa se a lista de evidências está vazia
        if not lista_de_evidencias:
            print("Nenhuma evidência registrada até o momento.")
        else:
            # Percorre a lista numerando os itens a partir do 1
            for num, ev in enumerate(lista_de_evidencias, 1):
                print(f"{num}. {ev}")

        print()
        input("Pressione [ENTER] para retornar ao Menu Principal...")
        continue

    # -----------------------------------------------------------------
    # PAINEL 3: CADASTRO DE AGENTE
    # -----------------------------------------------------------------
    elif resposta == "3":
        print("\n" + "-" * 50)
        digitar("=== CADASTRO DE NOVOS AGENTES ===", delay=0.03)
        print("-" * 50)

        nome_do_usuario = input("Digite seu nome aqui: ")
        print()

        identificacao = input(
            f"Digite sua identificação (4 dígitos), agente {nome_do_usuario}: "
        )

        # Validação da ID: fica preso no loop se não for número ou não tiver 4 dígitos
        while not identificacao.isdigit() or len(identificacao) != 4:
            print("Erro! A ID precisa ter exatamente 4 números.")
            identificacao = input("Digite novamente: ")

        # Monta a estrutura do agente e converte a ID string para inteiro (int)
        novo_agente = {"nome": nome_do_usuario, "id": int(identificacao)}
        lista_de_agentes.append(novo_agente)  # Adiciona à lista geral

        print()
        digitar(">>> Dados salvos no sistema <<<", delay=0.05)

        print()
        input("Pressione [ENTER] para retornar ao Menu Principal...")
        continue

    # -----------------------------------------------------------------
    # PAINEL 4: VISUALIZAR AGENTES
    # -----------------------------------------------------------------
    elif resposta == "4":
        print("\n" + "-" * 50)
        digitar("=== LISTA DE AGENTES CREDENCIADOS ===", delay=0.03)
        print("-" * 50)

        # Checa se existem agentes cadastrados
        if not lista_de_agentes:
            print("Nenhum agente cadastrado no sistema.")
        else:
            # Acessa os dados de cada dicionário dentro da lista
            for agente in lista_de_agentes:
                print(f"• Nome: {agente['nome']} | ID: {agente['id']}")

        print()
        input("Pressione [ENTER] para retornar ao Menu Principal...")
        continue

    # -----------------------------------------------------------------
    # OPÇÃO 5: ENCERRAMENTO
    # -----------------------------------------------------------------
    elif resposta == "5":
        print()
        digitar(
            "Desconectando dos servidores de perícia...", delay=0.04
        )
        pausa(1)
        print("Sessão encerrada.")
        break  # Único comando que quebra o 'while True' e finaliza o script

    # -----------------------------------------------------------------
    # PROTEÇÃO CONTRA ENTRADAS INVÁLIDAS
    # -----------------------------------------------------------------
    else:
        print()
        digitar("❌ Opção inválida! Escolha um número de 1 a 5.")
        pausa(1.5)
        continue  # Ignora o erro e repita o menu na tela
