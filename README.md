# Explorando-IA-Generativa-em-um-Pipeline-de-ETL-com-Python-

import pandas as pd

df = pd.read_csv('userID.csv')
user_ids = df['UserID'].tolist()
print(user_ids)

import requests
import json

UserID_api_url = "https://exemplo.com"

def get_user(id):
    return {
        "id": id,
        "name": f"User {id}",
        "news": []
    }

users = [user for id in user_ids if (user := get_user(id)) is not None]
print(json.dumps(users, indent=2))

# Documentação Oficial da API OpenAI: https://platform.openai.com/docs/api-reference/introduction
# Informações sobre o Período Gratuito: https://help.openai.com/en/articles/4936830

# Para gerar uma API Key:
# 1. Crie uma conta na OpenAI
# 2. Acesse a seção "API Keys"
# 3. Clique em "Create API Key"
# Link direto: https://platform.openai.com/account/api-keys

# Substitua o texto TODO por sua API Key da OpenAI, ela será salva como uma variável de ambiente.
openai_api_key = 'testetesteteste'

import random

# ===============================
# USUÁRIOS REAIS (mock)
# ===============================

users = [
    {
        "id": 1,
        "name": "Giovana",
        "news": []
    },
    {
        "id": 2,
        "name": "Carlos",
        "news": []
    }
]

# ===============================
# FUNÇÃO DE GERAÇÃO DE MENSAGEM
# ===============================

def generate_ai_news(user):
    templates = [
        f"{user['name']}, investir cedo é o caminho mais seguro para tranquilidade financeira.",
        f"{user['name']}, pequenos investimentos hoje constroem grandes conquistas amanhã.",
        f"{user['name']}, investir com planejamento transforma sonhos em objetivos reais.",
        f"{user['name']}, consistência nos investimentos vale mais do que pressa."
    ]

    return random.choice(templates)

# ===============================
# PROCESSAMENTO
# ===============================

for user in users:
    news = generate_ai_news(user)

    user["news"].append({
        "description": news
    })

# ===============================
# RESULTADO
# ===============================

for user in users:
    print(f"\nUsuário: {user['name']}")
    for item in user["news"]:
        print("-", item["description"])

def update_user(user):
    print(f"Usuário {user['name']} atualizado com sucesso (mock).")
    return True

for user in users:
  success = update_user(user)
  print(f"User {user['name']} updated? {success}!")s
