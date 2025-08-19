# 📘 Guia Rápido de Git – Commits

## 📑 Índice

1. [Criar um commit](#-1-criar-um-commit)  
2. [Alterar mensagem do último commit (sem push)](#-2-alterar-mensagem-do-último-commit-sem-push)  
3. [Alterar mensagem do último commit (já com push)](#-3-alterar-mensagem-do-último-commit-já-com-push)  
4. [Alterar mensagem do penúltimo commit](#-4-alterar-mensagem-do-penúltimo-commit)  
5. [Alterar mensagem de commits mais antigos](#-5-alterar-mensagem-de-commits-mais-antigos)  
6. [Cancelar último commit (mas manter alterações)](#-6-cancelar-último-commit-mas-manter-alterações)  
7. [Cancelar último commit (e também remover alterações)](#-7-cancelar-último-commit-e-também-remover-alterações)  
8. [Ver histórico de commits](#-8-ver-histórico-de-commits)  
9. [Desfazer alterações de um arquivo específico (não commitado)](#-9-desfazer-alterações-de-um-arquivo-específico-não-commitado)  
10. [Criar commit vazio (só mensagem, sem alterações)](#-10-criar-commit-vazio-só-mensagem-sem-alterações)  
11. [Boas práticas](#-11-boas-práticas)  
12. [Ver diferenças antes de commitar](#-12-ver-diferenças-antes-de-commitar)  
13. [Corrigir último commit (adicionando arquivos esquecidos)](#-13-corrigir-último-commit-adicionando-arquivos-esquecidos)  
14. [Reverter um commit específico](#-14-reverter-um-commit-específico)  
15. [Mudar commits de ordem ou juntar commits](#-15-mudar-commits-de-ordem-ou-juntar-commits)  
16. [Remover último commit mas guardar alterações](#-16-remover-último-commit-mas-guardar-alterações)  
17. [Guardar alterações temporariamente (stash)](#-17-guardar-alterações-temporariamente-stash)  
18. [Commit parcial (só parte de um arquivo)](#-18-commit-parcial-só-parte-de-um-arquivo)

---

## 🔹 1. Criar um commit

```bash
git add arquivo.txt           # adiciona um arquivo específico
git add .                     # adiciona todas as alterações
git commit -m "Mensagem clara e objetiva"

🔹 2. Alterar mensagem do último commit (sem push)
git commit --amend -m "Nova mensagem"

🔹 3. Alterar mensagem do último commit (já com push)
git commit --amend -m "Nova mensagem"
git push origin minha-branch --force


⚠️ Use --force só em branches pessoais.

🔹 4. Alterar mensagem do penúltimo commit
git rebase -i HEAD~2

🔹 5. Alterar mensagem de commits mais antigos
git rebase -i HEAD~5

🔹 6. Cancelar último commit (mas manter alterações)
git reset --soft HEAD~1

🔹 7. Cancelar último commit (e também remover alterações)
git reset --hard HEAD~1

🔹 8. Ver histórico de commits
git log --oneline

🔹 9. Desfazer alterações de um arquivo específico (não commitado)
git checkout -- arquivo.txt

🔹 10. Criar commit vazio (só mensagem, sem alterações)
git commit --allow-empty -m "Marca versão X"

✅ 11. Boas práticas

Mensagens curtas e objetivas (até 50 caracteres).

Use imperativo: "Adiciona", "Corrige", "Remove".

Se precisar, detalhe no corpo da mensagem:

Corrige validação do formulário

- Ajusta regex de email
- Melhora mensagem de erro para usuário

🔹 12. Ver diferenças antes de commitar
git diff


Mostra o que foi alterado mas ainda não foi adicionado com git add.

git diff --staged


Mostra o que já está pronto para o próximo commit.

🔹 13. Corrigir último commit (adicionando arquivos esquecidos)

Às vezes você commita e esquece um arquivo.

git add arquivo_esquecido.txt
git commit --amend --no-edit


Mantém a mesma mensagem do commit, mas inclui o arquivo junto.

🔹 14. Reverter um commit específico

Em vez de apagar histórico, você pode desfazer as alterações de um commit, criando um novo commit que anula ele:

git revert abc123


Útil em branches compartilhadas, pois não reescreve histórico.

🔹 15. Mudar commits de ordem ou juntar commits

Via rebase interativo:

git rebase -i HEAD~5


pick → mantém

reword → altera mensagem

squash ou s → junta commits

drop → remove commit

🔹 16. Remover último commit mas guardar as alterações para depois
git reset --mixed HEAD~1


Parecido com o --soft, mas deixa as alterações no working directory (sem staged).

🔹 17. Guardar alterações temporariamente (stash)

Às vezes você está no meio de algo mas precisa trocar de branch sem commitar:

git stash
git checkout outra-branch


Quando voltar:

git stash pop

🔹 18. Commit parcial (só parte de um arquivo)
git add -p


Permite escolher trechos específicos de um arquivo para entrar no commit.
Isso ajuda a manter commits mais limpos e organizados.
```
