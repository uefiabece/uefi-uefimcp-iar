# uefi-uefimcp-iar

Servidor MCP de **Engenharia de Instrumentação, Automação e Robótica**, UFABC. Nível: **curso** (segundo ciclo, acessado a partir do BCT).

## Origem

Derivado de [`uefi-uefimcp-engenharias`](https://github.com/uefiabece/uefi-uefimcp-engenharias)
por `git clone` (o histórico inclui o template `uefi-uefimcp`), sem importar materiais acadêmicos.
O repositório das Engenharias cobre a família de cursos; este cobre apenas Engenharia de Instrumentação, Automação e Robótica,
por isso as ferramentas curriculares são de curso único (sem o parâmetro `curso`).
A camada compartilhada (PDF, SDK MCP v1, `scripts/check_mcp.py`) vem de `uefi-uefimcp-bct` e `uefi-uefimcp-neuro`.

```text
uefi-uefimcp
  └── uefi-uefimcp-engenharias
      └── uefi-uefimcp-iar
          └── (disciplinas de Engenharia de Instrumentação, Automação e Robótica)
```

## Executar

Requer Python 3.11 ou superior. No diretório deste repositório:

```sh
python -m venv .venv
.venv/Scripts/python -m pip install -e ".[pdf,math]"
.venv/Scripts/python run.py
```

O processo usa transporte **stdio**: deve ser iniciado por um cliente MCP.
Em Linux/macOS, use `.venv/bin/python`.

## Conectar

```sh
claude mcp add --scope user uefi-uefimcp-iar -- "CAMINHO_ABSOLUTO/uefi-uefimcp-iar/.venv/Scripts/python.exe" "CAMINHO_ABSOLUTO/uefi-uefimcp-iar/run.py"
```

Outros clientes: veja `config/mcp.example.json`.

## Ferramentas

17 ferramentas:

- **Conteúdo / ensino / exercícios (template):** `get_syllabus`, `get_bibliography`, `get_past_exams`, `search_content`, `get_notes`, `explain_concept`, `get_topic_outline`, `generate_study_plan`, `get_exercises`, `solve_exercise`, `generate_exercise`, `generate_flashcards`
- **Navegação curricular:** `get_curriculum_structure`, `list_subjects_by_area`, `get_disciplinas_limitadas`, `get_progression_requirements`, `plan_academic_journey`

Prompts: `teach` e `solve`.

## Conteúdo

As pastas de `content/` estão vazias. Sugestões:

- `content/bibliography/` — PPC de Engenharia de Instrumentação, Automação e Robótica (PDF), planejamento de oferta, normas de estágio e TCC
- `content/syllabus/curriculo.md` — síntese estrutural do currículo

Ao adicionar o PPC, preencha `course_code`, `ppc_version`, `ppc_versions_available`,
`total_credits_approx` e `duration_years` em `config/subject.json`.

## Verificar

```sh
.venv/Scripts/python scripts/check_mcp.py
```
