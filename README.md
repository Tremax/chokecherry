# Chokecherry

Обертка над **lager**, которая не зависимо от вида **backend** осуществляет ограничение количества выводимых сообщений.

Вызовы **chokecherry:info**, **chokecherry:warning**, **chokecherry:error** транслируются в **lager:info**, **lager:warning**,
**lager:error** соответсвенно с соблюдением арности.

Для добавления в лог название модуля откуда произошел вызов и Pid вызывающего процесса можно использовать один из двух способов:

* указываем опцию для компилятора непосредственно в файле, в котором используем:

```
-compile([{parse_transform, chokecherry_transform}]).
```

**Внимание**: данная строчка должна предшествовать

```
-compile([{parse_transform, lager_transform}]).
```

* указываем опцию для компилятора в главном rebar.config проекта:

```
{erl_opts, [
    % ...
    {parse_transform, chokecherry_transform},
    {parse_transform, lager_transform}
    % ...
}.
```

**Внимание**: *chokecherry_transform* должен предшествовать *lager_transform*.
