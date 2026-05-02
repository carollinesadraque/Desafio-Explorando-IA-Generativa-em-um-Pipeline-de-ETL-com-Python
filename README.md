Desafio  Explorando IA Generativa em um Pipeline de ETL com Python

# Projeto ETL com Python

Este projeto foi desenvolvido com **ETL (Extract, Transform, Load)** utilizando Google Colab.

A ideia principal é mostrar como os dados passam por um fluxo completo:

1. São **extraídos** de um arquivo
2. São **transformados** 
3. São **carregados** em um novo formato

Mesmo sendo um projeto simples, ele representa exatamente o que acontece em sistemas reais de dados.

🧠 O que é ETL?

ETL é um processo muito usado em dados:

- **Extract (Extrair)** → pegar os dados (CSV)
- **Transform (Transformar)** → modificar os dados (regras / IA)
- **Load (Carregar)** → salvar os dados (JSON)


## 📂 Estrutura do projeto


etl-ia-dio/
│
├── data/
│ ├── users.csv # Dados de entrada
│ └── output.json # Resultado final
│
├── notebook/
│ └── projeto.ipynb # Código feito no Google Colab
│
├── README.md


---

## 📊 Etapa 1 — Extract (Extração)

Os dados foram criados em um arquivo CSV com informações de clientes:

Exemplo:


id,name,account_balance,account_limit,card_limit
1,Romilda,700.00,2000.00,4000.00
2,Cremilda,512.00,3000.00,4000.00


No código, usamos:

```python
import pandas as pd

df = pd.read_csv("users.csv")
users = df.to_dict(orient="records")

👉 Aqui transformamos o CSV em uma lista de usuários no Python

🔄 Etapa 2 — Transform (Transformação)

Nesta etapa, simulamos o uso de Inteligência Artificial usando regras simples (if/else).

Exemplo:

def generate_message(user):
    if user['account_limit'] >= 3000:
        return f"{user['name']}, você tem acesso a benefícios exclusivos!"
    
    elif user['account_balance'] < 500:
        return f"{user['name']}, temos crédito rápido disponível para você!"
    
    else:
        return f"{user['name']}, confira nossas opções personalizadas!"

Depois aplicamos isso a todos os usuários:

for user in users:
    user["message"] = generate_message(user)

👉 Cada cliente recebe uma mensagem personalizada

💾 Etapa 3 — Load (Carregamento)

Por fim, salvamos os dados transformados em um arquivo JSON:

import json

with open("output.json", "w", encoding="utf-8") as f:
    json.dump(users, f, indent=4, ensure_ascii=False)

👉 Esse arquivo é o resultado final do pipeline

📈 Resultado

Cada usuário agora tem uma mensagem personalizada:

{
  "name": "Romilda",
  "message": "Romilda, você tem acesso a benefícios exclusivos!"
}
🚨 Observação importante

Inicialmente, foi planejado o uso de IA com API externa, mas devido a limitações de quota, foi implementada uma simulação com regras condicionais.

👉 Isso mantém o foco no aprendizado do ETL, que é o objetivo principal.

🛠️ Tecnologias utilizadas
Python
Pandas
Google Colab
🎯 Aprendizados

Com este projeto foi possível aprender:

Como ler arquivos CSV
Como trabalhar com dados no Python
Como aplicar regras de negócio
Como estruturar um pipeline ETL
Como salvar dados em JSON
🚀 Como executar
Abra o projeto no Google Colab
Faça upload do arquivo users.csv
Execute as células na ordem:
Extract
Transform
Load
Baixe o arquivo output.json
💡 Próximos passos

Melhorias futuras:

Usar API real de IA
Criar interface (web)
Conectar com banco de dados
Criar dashboard
👩‍💻 Autor

Projeto desenvolvido para fins de estudo e prática em dados.


---

# 🎯 RESULTADO

Com esse README você mostra:

✔ que entende ETL  
✔ que sabe explicar (muito importante)  
✔ que sabe estruturar projeto  
✔ que resolve problemas (mesmo sem API)


Se quiser dar um upgrade final, posso:

👉 adaptar esse README para parecer nível empresa  
👉 ou montar descrição perfeita pro LinkedIn  

Só falar: *“quero versão recrutador”* 😎
