📚 Mini-Projeto SQL — Gerenciamento Escolar

Projeto feito em SQLite para gerenciar e consultar informações de alunos, notas, disciplinas e desempenho escolar.
O foco é praticar consultas utilizando funções de string, data, condicionais e operações numéricas no SQL.

📌 Objetivos do Projeto

✔ Consultar dados dos alunos
✔ Calcular idade
✔ Verificar aprovação
✔ Filtrar por condições textuais e de data
✔ Aplicar funções SQL no contexto escolar

🗂 Estrutura do Banco de Dados

Tabelas utilizadas:

Alunos

id_aluno

nome_aluno

data_nascimento

Notas

id_nota

id_aluno

id_disciplina

nota

Obs: Considera-se que a disciplina História possui id_disciplina = 2.

✅ Consultas Implementadas
1️⃣ Média das notas em História
SELECT AVG(nota) AS media_historia
FROM Notas
WHERE id_disciplina = 2;

2️⃣ Alunos cujo nome começa com "A"
SELECT *
FROM Alunos
WHERE nome_aluno LIKE 'A%';

3️⃣ Alunos que fazem aniversário em fevereiro
SELECT nome_aluno, data_nascimento
FROM Alunos
WHERE STRFTIME('%m', data_nascimento) = '02';

4️⃣ Cálculo da idade dos alunos
SELECT nome_aluno,
       data_nascimento,
       CAST((JULIANDAY('now') - JULIANDAY(data_nascimento)) / 365.25 AS INTEGER) AS idade
FROM Alunos;

5️⃣ Status de aprovação dos alunos

Critério: Nota ≥ 6 → Aprovado

SELECT id_aluno,
       nota,
       CASE
           WHEN nota >= 6 THEN 'Aprovado'
           ELSE 'Reprovado'
       END AS status_aluno
FROM Notas;
