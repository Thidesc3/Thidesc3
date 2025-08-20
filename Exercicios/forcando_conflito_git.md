# Forçando Conflitos no Git e Como Resolver

## 1) Criando cenário inicial
Na branch `main`, adicionamos um arquivo com uma versão inicial.

```bash
git checkout main
echo "Versão da main" > resolucao_conflito.md
git add resolucao_conflito.md
git commit -m "main: adiciona versão inicial do arquivo"
git push origin main
```

---

## 2) Criando a feature branch com mudança diferente
Na branch de feature, fazemos uma alteração diferente no mesmo arquivo.

```bash
git checkout -b feature/resolvendo-conflito
echo "Versão da feature" > resolucao_conflito.md
git add resolucao_conflito.md
git commit -m "feature: adiciona versão alternativa do arquivo"
git push -u origin feature/resolvendo-conflito
```

---

## 3) Alterando novamente na main
Voltamos para `main` e fazemos outra alteração no mesmo arquivo, garantindo o conflito.

```bash
git checkout main
echo "Outra mudança na main" > resolucao_conflito.md
git add resolucao_conflito.md
git commit -m "main: altera o mesmo arquivo para gerar conflito"
git push origin main
```

---

## 4) Tentando merge na feature
Ao tentar mergear `origin/main` na feature, o Git gerará conflito.  
A mensagem será parecida com:

```bash
git checkout feature/resolvendo-conflito
git fetch origin
git merge origin/main

# Erro esperado:
# Auto-merging resolucao_conflito.md
# CONFLICT (content): Merge conflict in resolucao_conflito.md
# Automatic merge failed; fix conflicts and then commit the result.
```

---

## 5) Resolvendo o conflito
Edite o arquivo escolhendo a versão correta (ou mesclando manualmente), depois rode:

```bash
git add resolucao_conflito.md
git commit -m "merge: resolve conflito entre main e feature"
git push
```
