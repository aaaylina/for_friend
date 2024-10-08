# Создание Git-репозитория

---

---

### 1. Инициализируем репозиторий

   Создай папку:

```bash
mkdir my_project
```

   Перейди в созданную директорию:

```bash
cd my_project
```

  Сделай её Git-репозиторием:

```bash
git init
```

  Чтобы посмотреть текущее состояние репозитория используй команду `git status`

#### 2. Добавляем файлы в репозиторий

  В ранее созданной папке **my_project** создай файл **my_file**

```bash
cd my_project
touch my_file
```

  Запусти `git status`, чтобы посмотреть, что изменилось. Git сообщит, что в папке **my_project** есть ешё неотслеживаемые файлы. Чтобы отслеживать состояние файл, используй одну из команд:

```bash
git add --all
git add my_file
git add .
```

  Команада `git add` только запоминает текущее содержимое файла, сохранения пок ане произошло.

#### 4. Делаем коммит

  Откройте файл **my_file**, добавьте туда какой-либо текст. Далее используйте команду `git add`:

```bash
git add my_file
```

  Сделайте коммит с подходящим сообщением:

```bash
git commit -m "Добавлен текст"
```

#### 5. Просматриваем историю коммитов

  Чтобы отслеживать историю коммитов, используй команду `git log`:

```bash
git log
```

#### 6. Создаем удалённый репозиторий

  Зарегестрируйся на **GitHub**: https://github.com/ и далее зайди в свой профиль по ссылке https://github.com/username , где **username** - имя, которое ты указал при регистрации.

  Создайте репозиторий. Для этого перейдите на вкладку **Repositories**, а затем нажмите на зелёную кнопку **New** справа.

  Открылось окно создания нового репозитория. Назови его **my_project**.

  Нажими на зелёную кнопку **Create repository** внизу.

#### 7. Генерируем SSH-ключ

  Перейди в домашнюю директорию:

```bash
cd ~
```

  Используй один из алгоритмов для генерации SSH-ключа:

```bash
ssh-keygen -t ed25519 -C "электронная почта, к которой привязан ваш аккаунт на GitHub"
ssh-keygen -t rsa -b 4096 -C "электронная почта, к которой привязан ваш аккаунт на GitHub" 
```

  Укажи место хранения ключей или же нажми `Enter`, чтобы сделать домашний каталог пользователя путём по умолчанию.

  Программа запросит кодовую фразу для доступа к SSH-ключу. Ты можешь оставить поле пустым. Для этого нажми  `Enter`, а затем ещё раз `Enter` для подтверждения.

  Проверь, что ключи действительно сгенерировались:

```bash
ls -a ~/.ssh
```

#### 8. Привязываем SSH-ключ к GitHub

  Скопируй содержимое файла **pub.** .

  Перейди на **GitHub** и выберите пункт **Settings** в меню аккаунта. В меню слева нажмит на пункт **SSH and GPG keys**. В открывшейся вкладке выбери **New SSH key**. В поле **Title** напиши название ключа. Например, **Personal key**. В поле **Key type** должно быть **Authentication Key**. В поле **Key** скопируй ключ из буфера обмена. Нажми на кнопку **Add SSH key**. 

  Проверь правильность ключа с помощью следующей команды:

```bash
ssh -T git@github.com 
```

#### 9. Связываем локальный и удаленный репозитории

  Перейди на страницу удалённого репозитория, выберите тип `SSH` и скопируй URL. Кнопка справа позволит сделать это мгновенно.

  Открой консоль, перейди в каталог локального репозитория и введи команду:

```bash
cd my_project
git remote add origin git@github.com:%ИМЯ_АККАУНТА%/first-project.git 
```

  Убедись, что все работает с помощью следующей команды:

```bash
git remote -v
```

 Ты должен увидеть две строчки, анлогичные этим:

`origin git@github.com:%ИМЯ_АККАУНТА%/%ИМЯ-ПРОЕКТА%.git (fetch)
 origin git@github.com:%ИМЯ_АККАУНТА%/%ИМЯ-ПРОЕКТА%.git (push)`

#### 10. Синхронизируем удаленный и локальный репозитории

 Загрузи содержимое локального репозитория с помощью команды `git push`.

В первый раз эту команду нужно вызвать с флагом `-u` и параметрами `origin` (имя удалённого репозитория) и `main` или `master` (название текущей ветки):

```bash
git push -u origin main
```

  Зайди в репозиторий **my_project**на GitHub. Ты увидишь, что в репозитории появились файлы с изменениями.


