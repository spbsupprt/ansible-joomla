# Развертывание Joomla с помощью Ansible

Этот репозиторий содержит Ansible-плейбук для автоматической установки и настройки CMS Joomla.

## Требования

Перед началом работы убедитесь, что на управляющем узле (Control Node) установлены:
* **Git**
* **Ansible** (версии 2.10 или выше)
* **SSH-доступ** к целевым серверам (рекомендуется настроить аутентификацию по SSH-ключам)

## Установка и запуск

### 1. Клонирование репозитория

Скачайте проект с GitHub и перейдите в его директорию:

```bash
git clone https://github.com/spbsupprt/ansible-joomla
cd ansible-joomla
```

### 2. Настройка инвентаря

Откройте файл `inventory.yaml` и укажите IP-адреса или доменные имена ваших серверов, а также параметры подключения (пользователя, путь к SSH-ключу и т.д.):

```bash
nano inventory.yaml

echo "joomla_vault_password" > .vault_pass
chmod 600 .vault_pass

```

### 3. Проверка подключения

Убедитесь, что Ansible успешно подключается к указанным серверам:

```bash
ansible -i inventory.yaml all -m ping
```

### 4. Запуск плейбука

Запустите процесс развертывания:

```bash
ansible-playbook -i inventory.yaml site.yaml
```

### 5. Переходим по адресу из inventory и вводим название нашего сайта и учетные данные пользователя.

<img width="694" height="561" alt="image" src="https://github.com/user-attachments/assets/14c99b44-191c-4ca4-974b-e267e7eb6950" />


### 6. Необходимо выбрать Тип Баз данных и логин\пароль

<img width="651" height="864" alt="image" src="https://github.com/user-attachments/assets/ffb56675-17b1-48ed-959f-374431922498" />

и учетные данные БД (посмотреть пароль можно командой)

```bash
ansible-vault view passwords.vault
```

Имя и префикс оставить по дефолту.

### 6. Дождаться установки и наслаждаться результатом.

<img width="659" height="633" alt="image" src="https://github.com/user-attachments/assets/3e1bb353-d6b9-40e7-a69f-adea5da743bd" />

