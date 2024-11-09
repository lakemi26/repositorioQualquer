# 🍃GreenFund

A **GreenFound** é uma iniciativa que conecta pessoas dispostas a contribuir com projetos sustentáveis, visando beneficiar tanto comunidades carentes quanto espaços públicos. A plataforma permite que indivíduos façam pequenas doações para financiar soluções de energia limpa, como a instalação de painéis solares em escolas, a modernização da iluminação pública com tecnologias eficientes e a implementação de sistemas de energia renovável em áreas com pouca infraestrutura.

Nosso objetivo é gerar um impacto positivo, não só no meio ambiente, mas também nas comunidades mais vulneráveis, melhorando a qualidade de vida e promovendo um futuro mais sustentável. A cada doação, os usuários podem acompanhar o progresso dos projetos, visualizar os resultados gerados e acumular pontos que podem ser trocados por recompensas simbólicas.

### **Principais funcionalidades:**

- **Doações Simples:** Contribuições rápidas para apoiar projetos de energia renovável em comunidades carentes e espaços públicos.
- **Acompanhamento de Metas:** Visualização do progresso e metas de cada projeto.
- **Sistema de Pontos e Recompensas:** Incentivos como certificados digitais e atualizações dos impactos gerados.
- **Impacto Sustentável:** Cada doação contribui para a redução de CO₂, economia de energia e benefícios sociais em áreas carentes e no espaço público.

> [!IMPORTANT]
> [**Video Pitch**](https://www.youtube.com/watch?v=_0Pf48RqSsg)

## ✒️Desenvolvedores

- RM98163 - Júlia Martins Santana Figueiredo - 2TDSA
- RM550562 - Larissa Akemi Iwamoto - 2TDSA
- RM550858 - Murilo Ribeiro Valério da Silva - 2TDSA
- RM94679 - Vinicios Becker Prediger - 2TDSS
- RM98570 - Gabriel Souza de Queiroz - 2TDSS

# :bookmark: Index

- [Autenticação](#autenticação)
- [Projetos](#projetos)
- [Sistema de Pontos e Recompensas](#sistema-de-pontos-e-recompensas)
- [Perfil do Usuário](#perfil-do-usuário)
- [Relatórios e Impacto](#relatórios-e-impacto)

---

# Endpoints

## **Autenticação**

### **POST/api/auth/register**

- Descrição: Registra um novo usuário.
- Dados:

```json
{
  "nomeCompleto": "string",
  "email": "string",
  "senha": "string"
}
```

- **Erros:**

`400 Bad Request`: Dados ausentes.

```json
{
  "Erro": "Todos os campos são obrigatórios"
}
```

`409 Conflict`: Email já registrado.

```json
{
  "Erro": "Este email já está em uso"
}
```

### **POST/api/auth/login**

- Descrição: Registra um novo usuário.
- Dados:

```json
{
  "nomeCompleto": "string",
  "email": "string",
  "senha": "string"
}
```

- **Erros:**

`400 Bad Request`: Dados ausentes.

`401 Unauthorized`: Credenciais inválidas.

```json
{
  "Erro": "Credenciais Inválidas"
}
```

---

## **Projetos**

### **GET/api/projetos**

- Descrição: Lista todos os projetos ativos.
- Retorno:

```json
{
  "idProjeto": "string",
  "nomeProjeto": "string",
  "descricao": "string",
  "valor_meta": "float",
  "progresso": "float",
  "data_inicio": "string",
  "data_termino": "string",
  "impacto_estimado": "string"
}
```

- **Erros:**

`500 Internal Server Error`: Erro ao buscar projetos.

```json
{
  "Erro": "Falha ao carrgar a lista de projetos. Tente novamente mais tarde"
}
```

### **POST/api/projetos/doacao**

- Descrição: Permite que o usuario doe para um projeto específico.
- Retorno:

```json
{
  "valorDoado": "float"
}
```

- **Erros:**

`400 Bad Request`: Valor inválido.

`404 Not Found`: Projeto não encontrado.

```json
{
  "Erro": "Projeto não encontrado"
}
```

`500 Internal Server Error`: Erro ao processar doação.

```json
{
  "Erro": "Erro interno ao processar a doação. Tente novamente mais tarde."
}
```

---

## **Sistema de Pontos e Recompensas**

### **GET/api/pontos**

- Descrição: Retorna o saldo de pontos do usuário e histórico de pontos ganhos
- Retorno:

```json
{
    {
  "pontosAcumulados": "int",
  "historicoPontos": [
    {
      "atividade": "string",
      "pontos": "int",
      "data": "string"
    }
  ]
}
}
```

- **Erros:**

`401 Unauthorized`: Usuário ão autenticado.

`500 Internal Server Error`: Erro ao buscar informações de pontos.

```json
{
  "Erro": "Erro ao recuperar histórico de pontos. Tente novamente mais tarde."
}
```

### **GET/api/recompensas**

- Descrição: Retorna o saldo de pontos do usuário e histórico de pontos ganhos
- Retorno:

```json
{
    {
  "idRecompensa": "int",
    "descricao": "string",
    "custoPontos": "int",
    "quantidadeDisponivel": "int"
}
}
```

- **Erros:**

`500 Internal Server Error`: Erro ao buscar recompensas

```json
{
  "Erro": "Erro ao procurar recompensas. Tente novamente mais tarde."
}
```

### **GET/api/recompensas/resgatar**

- Descrição: Permite que o usuário resgate recompensas

- **Erros:**

`400 Bad Request`: Recompensa inválida ou pontos insuficientes.

```json
{
  "Erro": "Saldo insuficiente"
}
```

`404 Not found`: Recompensa não encontrada

```json
{
  "Erro": "Parece que estamos sem recompensas no momento. Tente novamente mais tarde."
}
```

`500 Internal Server Error`: Erro ao buscar recompensas

```json
{
  "Erro": "Erro ao resgatar recompensas. Tente novamente mais tarde."
}
```

---

## **Perfil do Usuário**

### **GET/api/perfil**

- Descrição: Retorna os dados do perfil do usuário
- Retorno:

```json
{
  "nome_completo": "string",
  "email": "string",
  "pontos_acumulados": "int",
  "nivel": "string",
  "insignias": ["string"]
}
```

- **Erros:**

`401 Unauthorized`: Usuário ão autenticado.

`500 Internal Server Error`: Erro ao buscar perfil.

```json
{
  "Erro": "Erro ao carregar os dados do perfil. Tente novamente mais tarde."
}
```

---

## **Relatórios e Impacto**

### **GET/api/impacto**

- Descrição: Retorna os dados agregados do impacto das doações.
- Retorno:

```json
{
  "energiaGerada": "float",
  "co2Evitado": "float",
  "projetosConcluidos": "int"
}
```

- **Erros:**

`500 Internal Server Error`: Erro ao buscar dados de impacto.

```json
{
  "Erro": "Erro interno ao calcular impacto. Tente novamente mais tarde."
}
```

## 💚Expressões de Gratidão

Gostaríamos de expressar nossa sincera gratidão aos professores que contribuíram para o sucesso deste projeto. A dedicação de todos foi essencial para nosso aprendizado e crescimento. Agradecemos pelo apoio, orientação e esforço compartilhado, que foram fundamentais para superarmos desafios e alcançarmos nossos objetivos.
