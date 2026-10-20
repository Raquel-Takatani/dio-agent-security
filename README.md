# 🛡️ DIO Agent Security

> O [DIO Agent](https://github.com/digitalinnovationone/dio-agent) especializado em cibersegurança: um mentor que **pergunta o contexto antes de agir**, avalia impacto, probabilidade e severidade e orienta a correção.

Projeto do desafio de especialização do DIO Agent. Nenhum modelo foi treinado: o agente aprende **só pelo que está escrito nos arquivos** (skill, conhecimento e persona).

---

## 🎯 A especialização e por quê

**Especialização:** análise de vulnerabilidades, com mentalidade defensiva.

Um chat genérico, ao ouvir "tenho um servidor exposto na internet", costuma despejar uma lista de comandos. Um profissional de segurança faz diferente: primeiro entende o contexto (o que é, quem acessa, que dados há, o que já protege), depois avalia o risco e só então orienta. Esse comportamento é o que o projeto ensina ao agente.

Por que isso importa:

- **O mesmo problema tem gravidade diferente conforme o cenário.** Sem contexto, qualquer severidade é palpite.
- **Aprender segurança é aprender a raciocinar sobre risco**, não decorar comandos.
- **Defesa e ética em primeiro lugar:** só código e servidores do próprio estudante, em laboratório, sem ataques prontos.

## 🗂️ O que foi criado ou alterado

| Arquivo | Tipo | O que é |
|---------|------|---------|
| [`skills/vulnerability-analysis/SKILL.md`](skills/vulnerability-analysis/SKILL.md) | **Criado** | O roteiro que o agente segue: contexto, vulnerabilidade, risco, correção, validação e relatório. Tem `name` e `description`. |
| [`skills/vulnerability-analysis/README.md`](skills/vulnerability-analysis/README.md) | **Criado** | Explica a skill para pessoas. |
| [`agent/knowledge/security-basics.md`](agent/knowledge/security-basics.md) | **Criado** | Vulnerabilidade, ameaça, risco, tríade CIA, OWASP/CWE/CVE/MITRE ATT&CK, boas práticas e ética. |
| [`agent/persona.md`](agent/persona.md) | **Alterado** | Nova seção "Quando o assunto é segurança" e um item em "O que o DIO Agent não faz". |
| [`AGENTS.md`](AGENTS.md) | **Alterado** | Nova linha na tabela de skills, novo arquivo de conhecimento listado e um limite de "Segurança com ética". |
| [`skills/README.md`](skills/README.md) | **Alterado** | Skill nova adicionada à tabela. |
| [`examples/app.py`](examples/app.py) | **Criado** | Login de laboratório propositalmente vulnerável (SQL Injection), com dados fictícios. |
| [`examples/app_corrigido.py`](examples/app_corrigido.py) | **Criado** | Versão corrigida: consulta parametrizada e senhas com hash e sal. |
| [`docs/roteiro-de-testes.md`](docs/roteiro-de-testes.md) | **Criado** | Prompts e checklist para validar a skill. |
| [`docs/prints/`](docs/prints/README.md) | **Criado** | Pasta para as evidências em imagem. |

O restante do repositório (DIO Agent original, outras skills, glossário) foi mantido.

## ▶️ Como rodar o agente no harness

1. **Instale o Hermes** pela documentação oficial: https://hermes-agent.nousresearch.com/docs
2. **Baixe este repositório:**
   ```bash
   git clone https://github.com/<seu-usuario>/dio-agent-security.git
   cd dio-agent-security
   ```
3. **Rode o `hermes` num terminal aberto na pasta do projeto** (por exemplo, o terminal do VS Code). Aberto em outro lugar, ele não encontra o `AGENTS.md` nem as skills.
4. Converse com o agente, por exemplo:
   ```
   Você é um especialista em AppSec. Analise o arquivo examples/app.py (código de laboratório meu).
   Encontre a falha, explique como ela poderia ser explorada, cite a técnica do MITRE ATT&CK
   relacionada e mostre como corrigir.
   ```

Outros harnesses compatíveis com `AGENTS.md` (Claude Code, Antigravity, Codex, Cursor, OpenCode) também funcionam. Os prompts de teste estão em [`docs/roteiro-de-testes.md`](docs/roteiro-de-testes.md).

## 🔄 Como a skill funciona

```
1. Contexto       → perguntas, uma por vez, ANTES de qualquer sugestão
2. Vulnerabilidade → onde está, por que existe, OWASP/CWE, MITRE ATT&CK
3. Risco          → impacto, probabilidade e severidade, justificados
4. Correção       → causa raiz + camadas extras de defesa
5. Validação      → nova varredura e risco residual
6. Relatório      → sempre no mesmo formato
7. Aprendizado    → o estudante explica a correção com as próprias palavras
```

## 🚀 A melhoria escolhida

**Análise sempre no mesmo formato.** Toda análise termina com um relatório padronizado (alvo, contexto, vulnerabilidade, impacto, probabilidade, severidade, correção, validação e risco residual). Assim, casos diferentes (um login vulnerável, uma configuração insegura, um servidor exposto) podem ser **comparados lado a lado**, e o estudante aprende a classificar risco com o mesmo critério.

A severidade é justificada pelo contexto: a mesma falha pode ser Crítica num serviço exposto com dados reais e Baixa num laboratório isolado.

## 🧪 Evidências

As evidências ficam em [`docs/prints/`](docs/prints/README.md): análise do `app.py`, correção validada, perguntas de contexto no cenário do servidor Ubuntu e a comparação com um chat genérico.

## ⚠️ Aviso de uso responsável

- Os testes usam **apenas código e servidores seus, de laboratório**.
- `examples/app.py` é vulnerável **de propósito**, com dados fictícios. Não use em produção nem exponha na internet.
- Testar sistemas de terceiros sem autorização é crime. O objetivo aqui é **defender**.

## 🗺️ Estrutura

```
dio-agent-security/
├── README.md
├── AGENTS.md                              (alterado)
├── CLAUDE.md
├── agent/
│   ├── persona.md                         (alterado)
│   └── knowledge/
│       ├── dio-platform.md
│       ├── learning-experiences.md
│       └── security-basics.md             (novo)
├── skills/
│   ├── README.md                          (alterado)
│   ├── vulnerability-analysis/            (novo)
│   │   ├── SKILL.md
│   │   └── README.md
│   └── ... (skills originais)
├── examples/
│   ├── app.py                             (novo, vulnerável de propósito)
│   └── app_corrigido.py                   (novo)
└── docs/
    ├── roteiro-de-testes.md               (novo)
    ├── prints/README.md                   (novo)
    └── ... (docs originais)
```

## 🙌 Créditos

Baseado no [DIO Agent](https://github.com/digitalinnovationone/dio-agent), da [DIO](https://dio.me).
