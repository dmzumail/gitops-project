# GitOps Project

## Архитектура
![diagram](https://via.placeholder.com/600x200?text=GitOps+Flow)

## Стек
- Yandex Managed Kubernetes
- Argo CD
- GitHub Actions
- Yandex Container Registry

## Как развернуть
1. Создайте кластер через Terraform
2. Установите Argo CD
3. Создайте Application → укажите этот репозиторий
4. Готово!

## CI/CD
При пуше в `main`:
- Собирается образ
- Пушится в Container Registry
- Argo CD автоматически обновляет Deployment