# CLAUDE.md

Este arquivo orienta o Claude Code ao trabalhar neste repositório.

## Visão geral

**tacataca** é um jogo de pixel art escrito em Python usando [pygame](https://www.pygame.org/). O projeto é gerenciado com [uv](https://docs.astral.sh/uv/).

## Stack

- Python >= 3.12 (versão fixada em `.python-version`)
- Engine de jogo: `pygame`
- Gerenciador de pacotes/ambiente: `uv`
- Build backend: `uv_build`

## Estrutura

```
src/tacataca/__init__.py   # pacote principal; define main() (entry point)
pyproject.toml             # metadados, dependências e script `tacataca`
```

O código fica em layout `src/`. O comando `tacataca` aponta para `tacataca:main`.

## Comandos

```bash
uv sync                    # cria/atualiza o .venv com as dependências
uv run tacataca            # executa o jogo
uv add <pacote>            # adiciona dependência de runtime
uv add --dev <pacote>      # adiciona dependência de desenvolvimento
uv remove <pacote>         # remove dependência
uv run python -m <modulo>  # executa um módulo no ambiente do projeto
```

## Convenções

- Use sempre `uv` (nunca `pip` diretamente) para gerenciar dependências; commite o `uv.lock`.
- Código novo vai em `src/tacataca/`.
- Estilo pixel art: renderize em uma superfície interna de baixa resolução e escale por fator inteiro para a janela, com escala sem suavização (`pygame.transform.scale`, nunca `smoothscale`), para manter os pixels nítidos.
- Sprites e assets em formato PNG com fundo transparente; mantenha-os em uma pasta de assets dedicada.
- Use type hints nas assinaturas de funções.
- Comentários e documentação do projeto em português; identificadores de código em inglês.
