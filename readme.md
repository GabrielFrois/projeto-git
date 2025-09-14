# Como usar o Git

## Comandos Git

- `git --version`: Verifica a versão do git instalado.
- `git init`: Cria um repositório git vazio no diretório do projeto
- `git add <nomedoarquivo>`: Prepara os arquivos para o próximo `commit`, caso queira enviar todos os arquivos, basta colocar um "." ao invés do nome dos arquivos
- `git status`: Mostra as próximas mudanças a serem feitas
- `git commit -m "Mensagem do commit"`: Faz o commit, acompanhado de uma mensagem
- `git branch -M "novonome"`: Para renomear a branch
- `git remote add origin <linkdorepositorio>`: Cria a conexão do repositório local com o repositório do github com o nome origin
- `git push -u origin main`: Mando o commit para o github
- `git checkout -b "Nome da nova branch"`: Cria uma nova branch, e com o `checkout`, muda para essa nova branch

## Como criar uma chave SSH

1. Verifique se já não existe uma chave: `ls -al ~/.ssh`
   - Se você ver os nomes `id_rsa.pub`, `id_ecdsa.pub`, ou `id_ed25519.pub`, você já tem uma chave e pode pular para o **Passo 3**.
2. Gere uma nova chave SSH: `ssh-keygen -t ed25519 -C "seu_email@exemplo.com"`
   - Quando o terminal perguntar onde salvar o arquivo, apenas pressione Enter para aceitar o local padrão, em seguida, defina uma senha.
3. Copie sua chave SSH Pública:

```bash
# Para Windows (usando Git Bash ou WSL)
cat ~/.ssh/id_ed25519.pub | clip.exe

# Para Linux
xclip -selection clipboard < ~/.ssh/id_ed25519.pub
```

    - Se esses comandos não funcionarem, abra o arquivo `id_ed25519.pub` com um editor de texto e copie manualmente todo o conteúdo dele.

4.  Adicione a chave à sua conta do GitHub:
    - No menu lateral esquerdo das configurações do GitHub, clique em **SSH and GPG keys** (Chaves SSH e GPG).
    - Clique no botão **New SSH key** (Nova chave SSH).
    - Dê um **Title** (Título) para a chave (ex: "Meu PC de Trabalho", "PC do Gabriel").
    - Cole a chave pública que você copiou no campo **Key** (Chave).
    - Clique em **Add SSH key** (Adicionar chave SSH).
5.  Testando a conexão:
    - Digite no terminal: `ssh -T git@github.com`
    - Se der certo você verá a mensagem: Hi seu-usuario! You've successfully authenticated, but GitHub does not provide shell access.
