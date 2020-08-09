
# GIT

## Editor

Configurações GIT:  
1. system (para todos os usuários e projetos na máquina atual)
2. global (seu usuário na máquina atual)
3. local (somente projeto atual)

```
git config
```

Para ver as configurações do GIT na máquina:

```
git config --list                       
```

Alterar o editor de texto das configurações para vscode:

```
git config --global core.editor code    
```

Editar as configurações em modo global: 

```
git config --global --edit              
```

Formatando o log:
>%C(cor)  
>%h: hash do commit reduzido  
>%d: branch  
>%s: mensagem  
>%cn: quem fez o commit  
>%cr: data commit  

Exemplo de configuração (adicionar ao arquivo .gitconfig):

```
git log --pretty=format:'%C(blue)%h%C(red)%d %C(white)%s - %C(cyan)%cn, %C(green)%cr' 
```

Exemplo no .gitconfig:

```
[core]
	editor = code --wait //para que o git tenha tempo de carregar os dados no arquivo antes de abrir

[alias]
    s = !git status -s //associa o comando git status -s (status resumido) ao alias s
    c = !git add --all && git commit -m // para usar: 'git c "mensagem"'
    l = !git log --pretty=format:'%C(blue)%h%C(red)%d %C(white)%s - %C(cyan)%cn, %C(green)%cr'
```

## Commits
Existe uma convenção para commits, que pode ser consultada abaixo em **conventionalcommits.org**

Para fazer um commit mesclado com o anterior, usando a mesma mensagem:

```
git commit --amend --no-edit
```

Como no padrão TDD sempre desenvolvemos primeiro o teste e depois criamos o código para fazer o teste passar, no commit fazemos o contrário. Primeiro um commit de feat com os arquivos de código e depois do test, com os respectivos arquivos.  


# NPM

Inicia o npm com as configs default:

```
npm init -m                         
```

## Pacotes

Garantir que os commits seguindo o conventional commits:

```
npm i -D git-commit-msg-linter      
```

Typescript e type definitions:

```
npm i -D typescript @types/node     
```

Para adicionar tarefas antes ou depois de commits, push, etc:

```
npm i -D husky                      
```

Para rodar o eslint somente nos arquivos com status staged do git:

```
npm i -D lint-staged
```

Se após rodar a tarefa configurada no lintstagedrc.json os arquivos não foram adicionados ao staged automaticamente, adicione a config abaixo após o trecho "eslint 'src/**' --fix":  

```json
', "git add"'
```

Para atualizar pacotes NPM. Como é instalada globalmente (-g), não vincula ao projeto:

```
npm install -g npm-check
```

Exemplo de utilização. *-s* para pular as libs 'não usadas' e *-u* para atualizar:

```
npm-check -s -u                 
```

### Jest

Jest para testes e os seus type definitions:

```
npm i -D jest @types/jest ts-jest
```

Configurando o jest:
```
jest --init                     
```
    
>Precisei criar o arquivo de configuração na mão ("jest.config.js") e alterar a propriedade  "test" do package.json para:

```json
 "test": "jest"
```

>Se tiver algum erro para rodar o teste com jest, tente limpar o cache com:

```
 jest --clearCache
 ```

