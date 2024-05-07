# git-hints

## Небольшой гит-репозиторий для самостоятельной работы

`git clone https://github.com/PraktikumJava/git-hints.git`  

### Хеш — идентификатор коммита  

При вызове команды git log выводится история коммитов  
Информация о коммите — это набор данных: когда был сделан коммит, содержимое файлов в репозитории на момент коммита и ссылка на предыдущий коммит.   
Git хеширует (преобразует) эту информацию с помощью алгоритма SHA-1 и получает для каждого коммита свой уникальный хеш.  
Результат хеширования в Git — символьная строка.   
Она включает 40 символов и состоит из цифр 0—9 и латинских букв A—F.  

Хеш обладает следующими свойствами:  
* если хеш получить дважды для одного и того же набора входных данных, то результат будет одинаковый  
* если хоть что-то в исходных данных поменяется, то хеш тоже изменится   

хеш — основной идентификатор коммита.  
При работе с Git хеши можно  передавать в качестве параметра разным Git-командам, чтобы указать, с каким коммитом нужно произвести действие.  

Все хеши Git сохраняет в служебные файлы. Они находятся в скрытой папке .git в репозитории проекта.  

### Исследуем лог  

Если в репозитории много коммитов — пригодится сокращённый лог.   
Сокращённый лог вызывают командой git log с флагом --oneline («одной строкой»).  
В терминале появятся  первые несколько символов хеша каждого коммита и комментарии к ним.  
Команда git log --oneline автоматически подбирает такую длину сокращённых хешей, чтобы они были уникальными в пределах репозитория.  

### HEAD — всему голова  

HEAD — один из служебных файлов папки .git. Он указывает на коммит, который сделан последним.  
Внутри HEAD — ссылка на служебный файл: refs/heads/master (или refs/heads/main в зависимости от названия ветки).   

Когда вы делаете коммит, Git обновляет refs/heads/master — записывает в него хеш последнего коммита.   
Получается, что HEAD тоже обновляется, так как ссылается на refs/heads/master  

Мы уже упоминали, что многие команды Git принимают в качестве параметра хеш коммита. Если нужно передать последний коммит, то вместо его хеша можно просто написать слово HEAD.  

### Жизненный цикл файла в Git  

```mermaid  
graph LR;  
untracked -- "git add" --> staged;  
staged -- "git commit" --> tracked;  
staged -- "изменения" --> modified;  
tracked -- "изменения" --> modified;  
modified -- "git add" --> staged;  
```  

### Следующий заголовок




