# SEO Audit & Improvement

Skill reutilizável para auditar, planear, implementar e validar melhorias SEO com base em evidência. Foi desenhada para trabalhar tanto sobre o código como sobre o resultado renderizado, sem inventar domínio, identidade, conteúdo, dados comerciais ou resultados externos.

## Princípio central

> Avançar com tudo o que pode ser provado; expor claramente o que falta; nunca transformar uma lacuna numa suposição.

Quando falta informação, a skill distingue o que consegue fazer já, o que fica bloqueado, o que seria ideal melhorar primeiro e qual é a pergunta mínima para continuar. A falta de um dado bloqueia apenas o artefacto dependente, não toda a auditoria.

## Modos

- **AUDIT** — inspeção e relatório sem alterações.
- **IMPLEMENT** — alterações locais pedidas e validação proporcional.
- **ADVISORY** — prioridades, pré-requisitos e sequência sem editar o projeto.

## Cobertura

- crawlability, indexability, estados HTTP e redirects;
- títulos, descriptions, headings, conteúdo e links internos;
- robots, sitemap, canonicals e hreflang;
- JavaScript SEO e HTML renderizado;
- imagens e texto alternativo;
- structured data e SEO local baseados em factos visíveis;
- Core Web Vitals, performance e observabilidade com limites honestos;
- Open Graph, favicons e `llms.txt` corretamente separados do SEO essencial;
- Search Console, Analytics e Business Profile apenas com acesso e evidência real.

## Informação em falta

A skill nunca publica placeholders ou valores “prováveis”. Para cada lacuna relevante apresenta:

```text
Entregável
Consigo fazer agora
Informação ou acesso em falta
Porque é necessário
Ordem ideal
Pergunta mínima
```

Exemplo: se não existir um domínio de produção confirmado, pode auditar as rotas e preparar a arquitetura do sitemap, mas não inventa canonicals absolutos. Explica que primeiro deve ser escolhido o hostname preferido, depois alinhados redirects/canonicals/sitemap e, por fim, validadas as respostas publicadas.

## Estrutura

```text
seo-audit/
├── SKILL.md
├── README.md
├── agents/
│   └── openai.yaml
├── references/
│   ├── audit-rubric.md
│   ├── evidence-and-input-contract.md
│   ├── implementation-and-validation.md
│   └── official-sources.md
└── tests/
    └── forward-testing.md
```

## Uso e validação

Invoca a skill com pedidos como:

```text
Use $seo-audit para auditar este site sem alterar código.
Use $seo-audit para implementar as correções SEO comprováveis e listar os dados que faltam.
```

Para validação estrutural, executa o `quick_validate.py` fornecido pela `skill-creator` sobre a raiz desta skill.

Os casos em `tests/forward-testing.md` servem para avaliação independente do comportamento. A fonte e a instalação descoberta pelo Codex devem continuar separadas.
