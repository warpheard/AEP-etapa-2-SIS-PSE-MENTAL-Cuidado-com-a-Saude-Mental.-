# SIS-PSE MENTAL — Cuidado com a Saúde Mental

Sistema em linguagem C, executado no terminal, para cadastro e acompanhamento básico de estudantes no contexto do **Programa Saúde na Escola (PSE)**.

Projeto desenvolvido para a disciplina de Linguagem e Técnicas de Programação do curso de **Análise e Desenvolvimento de Sistemas** da **UNICESUMAR** (Atividade AEP, 2ª etapa).

**Integrantes:**
Letícia Caumo Botelho – R.A: 26008981-2
Mateus Beza – R.A: 25361132-2
Victor Gabriel Pereira Garcia - RA: 26012693-2
Pedro Roberto Waldhelm da Silva - RA: 26015133-2

---

## Objetivo

O PSE integra as áreas de saúde e educação, mas o registro manual dos estudantes causa extravio de dados e lentidão no acompanhamento. Este programa é o protótipo da base de cadastro desse fluxo: permite registrar estudantes por escola e turma, consultá-los, corrigir dados e obter um resumo por turma.

## Funcionalidades

| Opção | Funcionalidade | Descrição |
|:-----:|----------------|-----------|
| 1 | Cadastrar estudante | Registra código, nome, turma e escola |
| 2 | Listar estudantes | Exibe todos os estudantes cadastrados |
| 3 | Buscar estudante por código | Exibe os dados de um estudante específico |
| 4 | Alterar dados do estudante | Atualiza nome, turma e/ou escola (Enter mantém o valor atual) |
| 5 | Remover estudante | Exclui um registro, com confirmação |
| 6 | Resumo por turma | Mostra a quantidade de estudantes de cada turma |
| 0 | Sair | Encerra o programa |

## Validações e tratamento de erros

- **Registro inexistente:** buscar, alterar e remover informam quando o código não existe.
- **Código duplicado:** o cadastro recusa um código já utilizado.
- **Limite de armazenamento:** o sistema aceita no máximo **50 estudantes**; ao atingir o limite, novos cadastros são bloqueados com uma mensagem.
- **Entradas inválidas:** letras no lugar de números, códigos menores ou iguais a zero, campos de texto vazios e opções de menu inexistentes são rejeitados sem encerrar o programa.

## Requisitos

- Compilador C com suporte ao padrão C99 (por exemplo, **GCC**).
- Terminal (Linux, macOS ou Windows com MinGW/MSYS2 ou WSL).

O código foi compilado com `-Wall -Wextra -pedantic` sem nenhum aviso e testado com GCC no Linux.

## Como compilar

```bash
gcc -Wall -Wextra -std=c99 -o sis_pse sis_pse.c
```

## Como executar

Linux e macOS:

```bash
./sis_pse
```

Windows (PowerShell ou Prompt de Comando):

```bash
sis_pse.exe
```

> No Windows, se o compilador gerar o arquivo sem a extensão, use `gcc -o sis_pse.exe sis_pse.c`.

## Exemplos de uso

**Menu principal**

```text
=================================
         SIS-PSE MENTAL
   Cuidado com a Saude Mental
=================================
1 - Cadastrar estudante
2 - Listar estudantes
3 - Buscar estudante por codigo
4 - Alterar dados do estudante
5 - Remover estudante
6 - Resumo por turma
0 - Sair

Escolha uma opcao:
```

**Cadastro de um estudante**

```text
===== CADASTRO DE ESTUDANTE =====
Codigo do estudante: 10
Nome do estudante: Ana Souza
Turma: 5A
Escola: Escola Municipal Sol

Estudante cadastrado com sucesso!
```

**Tentativa de cadastrar um código duplicado**

```text
Codigo do estudante: 10

Ja existe um estudante com o codigo 10.
```

**Busca de um registro inexistente**

```text
===== BUSCAR ESTUDANTE =====
Codigo do estudante: 99

Estudante com codigo 99 nao encontrado.
```

**Resumo por turma**

```text
===== RESUMO POR TURMA =====
Turma 5A: 2 estudante(s)
Turma 7C: 1 estudante(s)
Total geral: 3 estudante(s)
```

## Estrutura do repositório

```text
.
├── sis_pse.c      # código-fonte completo
├── README.md      # este arquivo
└── docs/          # diagrama de casos de uso, manual e demais artefatos
```

## Casos de uso

![Diagrama de casos de uso](docs/diagrama_casos_de_uso_sis_pse.png)

## Limitações conhecidas

- Os dados ficam apenas na memória: ao encerrar o programa, os cadastros são perdidos.
- Capacidade fixa de 50 estudantes.
- Textos maiores que o limite de cada campo (nome e escola: 99 caracteres; turma: 29) são cortados.
- As mensagens não usam acentos, para evitar problemas de codificação em terminais diferentes.

## Possibilidades de melhoria

- Gravar e carregar os cadastros em arquivo, para não perder os dados.
- Registrar triagens de saúde (como acuidade visual e saúde mental) e gerar alertas.
- Aumentar a capacidade com alocação dinâmica de memória.
- Integrar com os sistemas da Atenção Primária, como proposto na 1ª etapa do projeto.
