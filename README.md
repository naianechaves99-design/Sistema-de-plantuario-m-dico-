import json
import requests

# === ETAPA 1: EXTRAÇÃO ===
dados_brutos = [
    {
        "name": "Naiane",
        "email": "naianechaves99@gmail.com",
        "phone": "21976603607"
    },
    {
        "name": "Naiara",
        "email": "naiarachaves32@gmail.com",
        "phone": "21978609949"
    },
    {
        "name": "Marcia",
        "email": "maria567@gmail.com",
        "phone": "21992146771"
    }
]

# === ETAPA 2: TRANSFORMAÇÃO ===
usuarios_transformados = []

for u in dados_brutos:
    nome = u['name'].strip().title()
    email = u['email'].lower()
    telefone = u['phone'].strip()

    usuarios_transformados.append({
        "username": nome,
        "email": email,
        "phone": telefone
    })

# === ETAPA 3: LOAD (ENVIO PARA API) ===
url_api = "https://petstore.swagger.io/v2/user"

for usuario in usuarios_transformados:
    resposta = requests.post(url_api, json=usuario)
    print(f"Enviando {usuario['username']}... Status: {resposta.status_code}")
    try:
        print(resposta.json())
    except:
        print("Resposta sem JSON")# Sistema-de-plantuario-m-dico-
Criando um ETL
