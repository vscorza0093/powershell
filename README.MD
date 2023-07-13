# PowerShell

help <command>


## Índice

```
-Get-Process.................................................
-New-Item....................................................
-Remove-Item.................................................
```



## Get-Process

Get-Process é utilizado para retornar todas as tarefas que estão sendo executadas pelo sistema, como o gerenciador de tarefas.

Para receber esse retorno, simplesmente executamos o comando `Get-Process` ou um de seus pseudônimos

pseudônimos:
```
gps
ps
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

Bibliografia

*New-Item       https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.management/new-item?view=powershell-7.3
*Remove-Item    https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.management/remove-item?view=powershell-7.3


