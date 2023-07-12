# PowerShell

help <command>


## Índice


-New-Item....................................................
-Remove-Item.................................................





## New-Item

New-Item é usado para criar qualquer recurso dentro do sistema e quando criamos arquivos podemos inserir um valor inicial.

Abreviadamente podemos criar um novo arquivo de texto no diretório local da seguinte forma:

`New-Item arquivo.txt`

Mas é possível especificar tipo de arquivo ou diretório, caminho onde será criado e outras coisas que podem ser consultadas na documentação.

Podemos utilizar a abreviação `ni` para executar o comando e os parâmetros -Path (string), -Name (string) e -ItemType (string) para criar um novo diretório e em seguida um novo arquivo dentro deste diretório, sem que seja necessário abrir este diretório.

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

abreviações: 
```
ni
```


## Remove-Item

abreviações: 
```
ri
rm
rmdir
del
erase
rd
```

Bibliografia

https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.management/new-item?view=powershell-7.3

