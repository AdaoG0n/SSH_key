<a href="https://github.com/AdaoG0n" style="pointer-events: none;"> <img src="https://github.com/AdaoG0n/AdaoG0n/blob/main/assests/Followbutton.png" width="130" align="right"/></a>

# <a href="#" style="pointer-events: none;"><img src="https://img.shields.io/github/last-commit/AdaoG0n/GIT_Tutorial?style=flat-square&color=%2312bab9" /> </a>

![](https://github.com/AdaoG0n/AdaoG0n/blob/main/assests/bar.png)
<div align="center"> 

  # Como Configurar uma Chave SSH no Ubuntu para o GitHub
</div>

Este guia apresenta, passo a passo, como criar uma chave SSH no Ubuntu e configurá-la para funcionar com o GitHub.

---

![](https://github.com/AdaoG0n/AdaoG0n/blob/main/assests/bar.png)
<div align="center"> 
  
## 1. Verificar se já existe uma chave SSH
</div>

Antes de criar uma nova chave SSH, é necessário verificar se já existe uma:

```shell
ls -al ~/.ssh
```

- Se aparecerem ficheiros como `id_rsa` ou `id_ed25519`, significa que já existe uma chave SSH.
- Caso não seja necessário criar uma nova, pode-se avançar para a secção [Adicionar a Chave ao Agente SSH](#3-adicionar-a-chave-ssh-ao-agente-ssh).
- Se não existirem chaves, continuar para a próxima secção.

---

![](https://github.com/AdaoG0n/AdaoG0n/blob/main/assests/bar.png)
<div align="center"> 

## 2. Criar uma Nova Chave SSH
</div>

Para criar uma nova chave SSH, usar o comando abaixo:

```shell
ssh-keygen -t ed25519 -C "seu-email@example.com"
```

### Explicação:
- **`-t ed25519`**: Especifica o tipo da chave (recomendado por ser mais seguro e rápido). Caso o sistema não suporte, usar `rsa`:
  ```shell
  ssh-keygen -t rsa -b 4096 -C "seu-email@example.com"
  ```
- **`-C`**: Adiciona um comentário para identificação (normalmente, o e-mail).

### Durante a criação:
- **Caminho para guardar a chave**: Pressionar Enter para usar o valor predefinido (`~/.ssh/id_ed25519`).
- **Palavra-passe (opcional)**: Definir uma palavra-passe para proteger a chave (recomendado).

---

![](https://github.com/AdaoG0n/AdaoG0n/blob/main/assests/bar.png)
<div align="center"> 

## 3. Adicionar a Chave SSH ao Agente SSH
</div>

Para garantir que a chave funcione corretamente, é necessário adicioná-la ao agente SSH:

1. Iniciar o agente SSH:
   ```shell
   eval "$(ssh-agent -s)"
   ```

2. Adicionar a chave recém-criada:
   ```shell
   ssh-add ~/.ssh/id_ed25519
   ```

---

![](https://github.com/AdaoG0n/AdaoG0n/blob/main/assests/bar.png)
<div align="center"> 

## 4. Copiar a Chave Pública
</div>

A chave pública será adicionada ao GitHub. Para copiá-la, usar o comando:

```shell
cat ~/.ssh/id_ed25519.pub
```

Copiar o conteúdo exibido no terminal (começa com `ssh-ed25519` ou `ssh-rsa`).

---

![](https://github.com/AdaoG0n/AdaoG0n/blob/main/assests/bar.png)
<div align="center"> 

## 5. Adicionar a Chave ao GitHub
</div>

1. Aceder às [Configurações de SSH no GitHub](https://github.com/settings/keys).
2. Clicar em **"New SSH key"**.
3. Preencher:
   - **Title**: Nome para identificar a chave (ex.: "Chave SSH Ubuntu").
   - **Key**: Colar o conteúdo da chave pública copiada anteriormente.
4. Clicar em **"Add SSH key"**.

---

![](https://github.com/AdaoG0n/AdaoG0n/blob/main/assests/bar.png)
<div align="center"> 

## 6. Testar a Conexão com o GitHub
</div>

Para verificar se a configuração foi concluída com sucesso, testar a conexão:

```shell
ssh -T git@github.com
```

Se tudo estiver correto, será exibida uma mensagem semelhante a:

```plaintext
Hi username! You've successfully authenticated, but GitHub does not provide shell access.
```

---

![](https://github.com/AdaoG0n/AdaoG0n/blob/main/assests/bar.png)
<div align="center"> 

## Notas Finais
</div>

- **Segurança**: Nunca partilhar a chave privada (`id_ed25519` ou `id_rsa`). Apenas a chave pública (`.pub`) deve ser utilizada para autenticação.
- **Múltiplas Contas no GitHub**: Para utilizar várias contas, configurar ficheiros `config` no diretório `~/.ssh`. Consultar a [documentação oficial](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/managing-deploy-keys#platform-specific-setup) para mais detalhes.

---

Com estes passos, a chave SSH está configurada para trabalhar com o GitHub.


![](https://github.com/AdaoG0n/AdaoG0n/blob/main/assests/animated%20gifs/madeby.gif)

![Endpoint Badge](https://img.shields.io/endpoint?url=https%3A%2F%2Fhits.dwyl.com%2FAdaoG0n%2FSSH_key.json&style=flat-square&labelColor=black&color=blue)
