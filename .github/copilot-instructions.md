# Mulktan — Copilot Instructions

## REGRA ABSOLUTA — IDIOMA

- SEMPRE responder em Português do Brasil (pt-BR)
- SEMPRE gerar docstrings em Português (pt-BR)
- SEMPRE gerar comentários em Português (pt-BR)
- NUNCA usar inglês em docstrings, comentários ou explicações
- Se o código tiver comentários em inglês, traduza para pt-BR

## Identidade do Projeto

- Operador: Mulktan
- Stack principal: Python, SQL, HTML, CSS, Excel/VBA, LaTeX
- Ambiente: Windows 11, VS Code, GitHub (SSH), Copilot Pro
- Estilo: Código limpo, bem documentado, profissional
- Nível: Iniciante em evolução — priorizar clareza e didatismo

## Regras de Python

- Sempre usar type hints nas funções
- Docstrings no padrão Google Style em pt-BR
- Variáveis e funções em snake_case
- Classes em PascalCase
- Preferir list comprehensions quando legível
- Sempre tratar exceções com try/except específico
- Imports organizados: stdlib → third-party → local
- Sempre adicionar comentários explicativos em blocos complexos

## Exemplo de padrão Python esperado:

```python
def processar_dados(arquivo: str, limite: int = 100) -> list[dict]:
    """
    Processa dados de um arquivo CSV.

    Args:
        arquivo: Caminho para o arquivo CSV.
        limite: Número máximo de registros. Default: 100.

    Returns:
        Lista de dicionários com os dados processados.

    Raises:
        FileNotFoundError: Se o arquivo não existir.
    """
    try:
        # implementação
        pass
    except FileNotFoundError as e:
        raise FileNotFoundError(f"Arquivo não encontrado: {arquivo}") from e
```

## Regras de SQL

- Palavras-chave em MAIÚSCULO (SELECT, FROM, WHERE, JOIN)
- Aliases sempre com AS explícito
- Sempre incluir comentários explicativos em queries complexas
- Preferir CTEs (WITH) em vez de subqueries aninhadas
- Indentação de 4 espaços
- Sempre incluir ORDER BY quando a ordem importa
- Usar nomes descritivos para CTEs e aliases

## Exemplo de padrão SQL esperado:

```sql
-- Busca clientes ativos com pedidos recentes
WITH clientes_ativos AS (
    SELECT
        c.id          AS cliente_id,
        c.nome        AS cliente_nome,
        COUNT(p.id)   AS total_pedidos
    FROM clientes AS c
    INNER JOIN pedidos AS p ON c.id = p.cliente_id
    WHERE c.status = 'ativo'
    GROUP BY c.id, c.nome
)
SELECT *
FROM clientes_ativos
WHERE total_pedidos > 5
ORDER BY total_pedidos DESC;
```

## Regras de HTML/CSS

- Sempre usar HTML5 semântico (header, main, section, footer)
- Indentação de 2 espaços no HTML
- Classes CSS em kebab-case (meu-componente)
- Sempre incluir atributo alt em imagens
- Sempre incluir meta charset e viewport
- Comentários HTML para separar seções

## Exemplo de padrão HTML esperado:

```html
<!DOCTYPE html>
<html lang="pt-BR">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Título da Página</title>
  </head>
  <body>
    <!-- Cabeçalho principal -->
    <header>
      <h1>Título</h1>
    </header>

    <!-- Conteúdo principal -->
    <main>
      <section>
        <p>Conteúdo aqui</p>
      </section>
    </main>
  </body>
</html>
```

## Regras de Git — Padrão de Commits

- Formato: tipo(escopo): descrição em pt-BR
- Tipos permitidos:
  - feat: nova funcionalidade
  - fix: correção de bug
  - docs: documentação
  - style: formatação
  - refactor: refatoração
  - test: testes
  - chore: tarefas gerais

## Exemplos de commits:

```
feat(python): adicionar função de processamento de CSV
fix(sql): corrigir query de relatório mensal
docs(readme): atualizar instruções de instalação
refactor(html): reorganizar estrutura semântica
```

## Regras Gerais

- SEMPRE responder em Português (pt-BR)
- Comentários no código em Português
- Nunca expor dados sensíveis ou credenciais
- Priorizar legibilidade sobre esperteza
- Sempre sugerir tratamento de erros
- Explicar o raciocínio por trás das sugestões
- Quando houver múltiplas soluções, apresentar a mais simples primeiro
- Sempre sugerir melhorias de performance quando relevante
