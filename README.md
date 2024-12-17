# lab2

## Как начать

### 1. Инициализация роли Docker с помощью Ansible Galaxy

Для начала необходимо сгенерировать структуру роли с помощью команды:

```bash
ansible-galaxy init Docker
```

2. Создание роли для установки Docker
Вынесите все задачи, связанные с установкой Docker, из основного плейбука в роль Docker. Роль будет параметризована с использованием переменных, что позволит настраивать её для различных окружений.

3. Параметризация роли
Для удобства использования, роль будет параметризована с помощью переменных, таких как версия Docker, репозиторий, имя контейнера и другие настройки.

# Пример переменных для роли Docker
```
docker_version: "20.10"
docker_container_name: "my_docker_container"
```

4. Создание репозитория для ролей
Создайте репозиторий на GitLab для хранения ролей. После этого запушьте роль Docker в репозиторий.

```bash
git init
git remote add origin <github_repo_url>
git add .
git commit -m "Initial commit for Docker role"
git push -u origin main
```

5. Создание requirements.yml
В файле requirements.yml укажите репозиторий, где находится ваша роль, чтобы её можно было установить с помощью команды ansible-galaxy.
```yaml
# requirements.yml
roles:
  - name: docker
    src: https://gitlab.com/<your_gitlab_group>/Docker
    version: main
    scm: git
```

6. Развертывание приложения с ролью Docker
Запустите плейбук, используя роль Docker, для развертывания приложения на нодах группы app. Для этого используйте команду:

```bash
ansible-playbook -i hosts lab2.yml
```
Плейбук установит Docker на целевых нодах и развернёт приложение в контейнере.
