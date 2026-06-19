# 🎓 Banco de Dados — Reforma do Ensino Médio em Araçatuba-SP

Banco de dados relacional construído a partir de dados reais extraídos da dissertação de mestrado:

> **"Trabalho Docente no Contexto da Reforma do Ensino Médio: reflexões, práticas e relatos em duas escolas de Araçatuba-SP (2022-2024)"**
> Autor: Gustavo Aparecido de Paula — ProfSocio/UEL (2024)

---

## 📌 Contexto

A Lei nº 13.415/2017 (Novo Ensino Médio) reduziu drasticamente a presença de disciplinas humanistas no currículo paulista. Este banco de dados estrutura essa evidência empiricamente, permitindo análises sobre a distribuição de aulas por disciplina, escola e série.

---

## 🗄️ Estrutura do Banco

| Tabela | Descrição | Registros |
|--------|-----------|-----------|
| `escola` | Escolas estaduais de Araçatuba-SP | 4 |
| `disciplina` | Disciplinas do currículo paulista 2024 | 20 |
| `grade_curricular` | Matrizes curriculares homologadas | 2 |
| `aula_grade` | Carga horária por disciplina e série | 28 |
| `indicador_educacional` | Dados IBGE — Brasil, SP e Araçatuba | 9 |
| `categoria_docente` | Categorias do magistério público paulista | 10 |

---

## 🔍 Queries de Destaque

**Sociologia vs Matemática no Novo Ensino Médio:**
```sql
SELECT d.nome, ag.serie_1, ag.serie_2, ag.serie_3,
       (ag.serie_1 + ag.serie_2 + ag.serie_3) AS total_aulas
FROM aula_grade ag
JOIN disciplina d ON ag.disciplina_id = d.id
WHERE ag.grade_id = 2
AND d.nome IN ('Sociologia', 'Filosofia', 'Matemática', 'Língua Portuguesa')
ORDER BY total_aulas DESC;
```

**Resultado:**

---

## 📊 Arquivos CSV

Exportados para uso no Looker Studio / Power BI:
- `aulas_novo_ensino_medio.csv`
- `indicadores.csv`
- `categorias_docentes.csv`

---

## 🛠️ Tecnologias

![SQLite](https://img.shields.io/badge/SQLite-003B57?style=flat&logo=sqlite&logoColor=white)
![DBeaver](https://img.shields.io/badge/DBeaver-372923?style=flat&logo=dbeaver&logoColor=white)

---

## 👤 Autor

**Gustavo Aparecido de Paula**
Professor de Sociologia em transição para Análise de Dados
[GitHub](https://github.com/gustavodepaula86-oss)
