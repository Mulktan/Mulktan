# Mulktan — Copilot Instructions

## REGRA ABSOLUTA — IDIOMA
- SEMPRE responder em Português do Brasil (pt-BR)
- SEMPRE gerar docstrings em Português (pt-BR)
- SEMPRE gerar comentários em Português (pt-BR)
- NUNCA usar inglês em docstrings, comentários ou explicações
- Se o código tiver comentários em inglês, traduza para pt-BR

## Identidade do Projeto
- Operador: Mulktan
- Stack principal: Python, SQL, Excel/VBA, LaTeX
- Ambiente: Windows 11, VS Code, GitHub (SSH)
- Estilo: Código limpo, bem documentado, profissional

## Regras de Python
- Sempre usar type hints nas funções
- Docstrings no padrão Google Style
- Variáveis e funções em snake_case
- Classes em PascalCase
- Preferir list comprehensions quando legível
- Sempre tratar exceções com try/except específico
- Imports organizados: stdlib → third-party → local

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
- Palavras-chave em MAIÚSCULO (SELECT, FROM, WHERE)
- Aliases sempre com AS explícito
- Sempre incluir comentários em queries complexas
- Preferir CTEs (WITH) em vez de subqueries aninhadas
- Indentação de 4 espaços

## Exemplo de padrão SQL esperado:
```sql
-- Busca clientes ativos com pedidos recentes
WITH clientes_ativos AS (
    SELECT
        c.id AS cliente_id,
        c.nome AS cliente_nome,
        COUNT(p.id) AS total_pedidos
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

## Regras Gerais
- Sempre responder em Português (pt-BR)
- Comentários no código em Português
- Nunca expor dados sensíveis ou credenciais
- Priorizar legibilidade sobre esperteza
- Sempre sugerir tratamento de erros
- Commits seguem padrão: tipo(escopo): descrição