## Настройка Ruby для Apple Silicon Mac

Для успешного выполнения инициализации проекта на рабочей машине необходимо установить `Ruby` версии `2.7.2`. За основу брался материал из [этой статьи](https://kemalmutlu.medium.com/installing-ruby-on-rails-macbook-pro-m1-4272da855fb3 "https://kemalmutlu.medium.com/installing-ruby-on-rails-macbook-pro-m1-4272da855fb3").

Все команды выполняем через терминал.

Для начала нужно установить `homebrew`:

`/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`

Далее необходимо установить `rbenv` и `ruby-build` через `homebrew`:

`brew install rbenv ruby-build`

Следующим шагом нужно добавить автоматическую инициализацию `rbenv` в `.bash_profile` или `.zshrc`, в зависимости от используемого окружения.

Проверялось при установленном [oh-my-zsh](https://ohmyz.sh/ "https://ohmyz.sh/").

Для `.zshrc` выполняем:
```
echo 'if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi'  >> ~/.zshrc 
source ~/.zshrc # Для применения изменений в текущей сессии терминала`
```

В случае `.bash_profile`:
```
echo  'if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi'  >> ~/.bash_profile 
source ~/.bash_profile # Для применения изменений в текущей сессии терминала`
```
После этого устанавливаем `Ruby` версии `2.7.2` и устанавливаем его как `global`:

`rbenv install  2.7.2 2rbenv global 2.7.2`

После выполнения всех вышеперечисленных шагов проверяем версию `Ruby`:

`ruby -v`

Должно быть что-то вроде этого:

`ruby 2.7.2p137 (2020-10-01 revision 5445e04352)  [arm64-darwin20]`

Если вместо этого у вас версия ниже(например `2.6.0`), тогда ищем ошибку и внимательно проверяем все шаг за шагом.

Далее пробуем установить поды через `gem install cocoapods`
Из текущих особенностей, проекты, у которых зависимости в `CocoaPods`, не будут работать в симуляторах с версией `14.*.` На данный момент (май 2021, Xcode 12.5), это можно обойти, установив симулятор 13-й версии.
