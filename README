# <center><font color="#00d771">🍃GreenFund</font></center>

A <font color="#00d771">**GreenFound**</font> é uma iniciativa que conecta pessoas dispostas a contribuir com projetos sustentáveis, visando beneficiar tanto comunidades carentes quanto espaços públicos. A plataforma permite que indivíduos façam pequenas doações para financiar soluções de energia limpa, como a instalação de painéis solares em escolas, a modernização da iluminação pública com tecnologias eficientes e a implementação de sistemas de energia renovável em áreas com pouca infraestrutura.

Nosso objetivo é gerar um impacto positivo, não só no meio ambiente, mas também nas comunidades mais vulneráveis, melhorando a qualidade de vida e promovendo um futuro mais sustentável. A cada doação, os usuários podem acompanhar o progresso dos projetos, visualizar os resultados gerados e acumular pontos que podem ser trocados por recompensas simbólicas.

### <font color="#81D4FA">**Principais funcionalidades:**</font>

- **Doações Simples:** Contribuições rápidas para apoiar projetos de energia renovável em comunidades carentes e espaços públicos.
- **Acompanhamento de Metas:** Visualização do progresso e metas de cada projeto.
- **Sistema de Pontos e Recompensas:** Incentivos como certificados digitais e atualizações dos impactos gerados.
- **Impacto Sustentável:** Cada doação contribui para a redução de CO₂, economia de energia e benefícios sociais em áreas carentes e no espaço público.

> [!IMPORTANT] <font color="#00d771">**Video Pitch**</font>
> Confira o video do pitch [aqui](https://www.youtube.com/watch?v=_0Pf48RqSsg)

## <font color="#81D4FA">✒️Desenvolvedores</font>

- RM98163 - Júlia Martins Santana Figueiredo - 2TDSA
- RM550562 - Larissa Akemi Iwamoto - 2TDSA
- RM550858 - Murilo Ribeiro Valério da Silva - 2TDSA
- RM94679 - Vinicios Becker Prediger - 2TDSS
- RM98570 - Gabriel Souza de Queiroz - 2TDSS

# :bookmark: <font color="#81D4FA">Index</font>

- [Autenticação](#autenticação)
- [Projetos](#projetos)
- [Sistema de Pontos e Recompensas](#sistema-de-pontos-e-recompensas)
- [Perfil do Usuário](#perfil-do-usuário)
- [Relatórios e Impacto](#relatórios-e-impacto)

---

# <center><font color="#52b788">Endpoints</font></center>

## <font color="#81D4FA">**Autenticação**</font>

### <font color="#00d771">**POST/api/auth/register**</font>

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

### <font color="#00d771"> **POST/api/auth/login**</font>

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

## <font color="#81D4FA">**Projetos**</font>

### <font color="#00d771"> **GET/api/projetos**</font>

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

### <font color="#00d771"> **POST/api/projetos/doacao**</font>

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

## <font color="#81D4FA">**Sistema de Pontos e Recompensas**</font>

### <font color="#00d771"> **GET/api/pontos**</font>

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

### <font color="#00d771"> **GET/api/recompensas**</font>

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

### <font color="#00d771"> **GET/api/recompensas/resgatar**</font>

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

## <font color="#81D4FA">**Perfil do Usuário**</font>

### <font color="#00d771"> **GET/api/perfil**</font>

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

## <font color="#81D4FA">**Relatórios e Impacto**</font>

### <font color="#00d771"> **GET/api/impacto**</font>

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

## 💚<font color="#00d771">Expressões de Gratidão</font>

Gostaríamos de expressar nossa sincera gratidão aos professores que contribuíram para o sucesso deste projeto. A dedicação de todos foi essencial para nosso aprendizado e crescimento. Agradecemos pelo apoio, orientação e esforço compartilhado, que foram fundamentais para superarmos desafios e alcançarmos nossos objetivos.
