# PowerShell

help <command>


## Índice

```
Function (?)

function.....................................................


Commands

-Get-Process.................................................
-Invoke-Item.................................................
-New-Item....................................................
-Remove-Item.................................................
-Set-Alias...................................................
```


## function

resumo do que explorei de functions até o momento

São literalmente funções que podem ser usadas para executar uma lista de tarefas ou o que for necessário, de maneira automatizada.

Meu objetivo era criar alias para alguns comandos git, através do cmdlet `Set-Alias`, porém não é possível aplicar um alias a um comando externo ao PowerShell. Descobri que este problema poderia ser resolvido através das functions.

function [name] { body }

```
function git-status { git status }
```

Agora o comando `git-status` é reconhecido como `cmdlet` e é parâmetro válido para o Set-Alias. Porém, assim como Set-Alias, function só existe durante a sessão atual ativa do PowerShell.





## Get-Process

Get-Process é utilizado para retornar todas as tarefas que estão sendo executadas pelo sistema, como o gerenciador de tarefas.

Para receber esse retorno, simplesmente executamos o comando `Get-Process` ou um de seus pseudônimos

pseudônimos:
```
gps
ps
```


## Invoke-Item

Invoke-Item executa a ação predefinida no item especificado. Por exemplo, executa um ficheiro executável ou abre um ficheiro de documento na aplicação associada ao tipo do ficheiro, também podemos abrir diretórios.

`Invoke-Item c:\Github`

Esse comando abrirá, no explorer, o diretório Github que está dentro de C:

pseudônimos:
```
ii
```



## New-Item

New-Item é usado para criar qualquer recurso dentro do sistema e quando criamos arquivos podemos inserir um valor inicial.

Abreviadamente podemos criar um novo arquivo de texto no diretório local da seguinte forma:

`New-Item arquivo.txt`

Mas é possível especificar tipo de arquivo ou diretório, caminho onde será criado e outras coisas que podem ser consultadas na documentação.

Podemos utilizar o pseudônimos `ni` para executar o comando e os parâmetros -Path (string), -Name (string) e -ItemType (string) para criar um novo diretório e em seguida um novo arquivo dentro deste diretório, sem que seja necessário abrir este diretório.

`ni -Path ".\" -Name "logfiles" -ItemType "directory"`

```
    Diretório: C:\usr\vinc\GitHub\powershell


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d-----        12/07/2023     02:26                logfiles
```

`ni -Path ".\logfiles" -Name "log1.txt" -ItemType "file"`

```
    Diretório: C:\Users\vinic\GitHub\powershell\logfiles


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----        12/07/2023     02:45              0 log1.txt
```

pseudônimos: 
```
ni
```



## Remove-Item

Remove-Item é usado para deletar qualquer recurso dentro do sistema. Podemos interagir com a pasta que estamos utilizando no momento ou especificar um caminho para deletar este recurso de qualquer pasta do sistema.

`Remove-Item -Path ".\powershell\data.txt"

Deletar arquivos de documentos em um diretório:
`Remove-Item * -Include *.doc -Exclude *1*`

Este exemplo deleta todos os arquivos com extensão `.doc` e quualquer nome que não inclua `*1*` do diretório atual.
Utilizamos o caractere `*` para especificar o conteúdo do diretório atual e utilizamos `-Include` e `-Exclude` para especificar os arquivos a serem deletados.

Deletar arquivos ocultos e somente-leitura:
`Remove-Item -Path C:\Test\hidden-RO-file.txt -Force`

Este comando usa o parâmetro `-Path` para especificar o arquivo. Também é utilizado o parâmetro `-Force` para deletá-lo. Não podemos deletar arquivos `ocultos` e arquivos `somente-leitura` sem a utilização do parâmetro `-Force`.

Quando precisamos deletar uma pasta que contém diversos arquivo dentro dela, a recursão é acionada e o para executar essa tarefa:

``` 
Confirmar
O item em C:\Users\vinic\GitHub\powershell\test tem filhos e o parâmetro Recurse não foi especificado. Se você
continuar, todos os filhos serão removidos com o item. Tem certeza de que deseja continuar?
[S] Sim  [A] Sim para Todos  [N] Não  [T] Não para Todos  [U] Suspender  [?] Ajuda (o padrão é "S"):
```

Podemos executar a recursão manualmente para evitar a mensagem de prevenção de erros com o seguinte comando:

`Remove-Item C:\Users\vinic\GitHub\powershell\test -Recurse`

pseudônimos: 
```
ri
rm
rmdir
del
erase
rd
```


## Set-Alias

Set-Alias [-Name] <string> [-Value] <string>

Define um apelido para qualquer qualquer cmdlet ou comando existente na sessão atual do PowerShell.

O Set-Alias cmdlet cria ou altera um alias para um cmdlet ou um comando, como uma função, script, arquivo ou outro executável. 

Um alias criado ou alterado por Set-Alias não é permanente e só está disponível durante a sessão atual do PowerShell. Quando a sessão do PowerShell é fechada, o alias é removido.
















Bibliografia

*Functions      https://learn.microsoft.com/pt-br/powershell/module/microsoft.powershell.core/about/about_functions?view=powershell-7.3
*Invoke-Item    https://learn.microsoft.com/pt-pt/powershell/module/microsoft.powershell.management/invoke-item?view=powershell-7.3&viewFallbackFrom=powershell-6
*New-Item       https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.management/new-item?view=powershell-7.3
*Remove-Item    https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.management/remove-item?view=powershell-7.3
*Set-Alias      https://learn.microsoft.com/pt-br/powershell/module/microsoft.powershell.utility/set-alias?view=powershell-7.3


