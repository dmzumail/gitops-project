# GitOps Project

Проект демонстрирует полностью автоматизированный GitOps-пайплайн с использованием:
- **Yandex Managed Kubernetes**
- **Argo CD** (GitOps-оператор)
- **GitHub Actions** (CI/CD)
- **Yandex Container Registry**
- **Yandex Lockbox** (управление секретами)

При пуше в ветку `main`:
1. Собирается Docker-образ приложения
2. Пушится в Container Registry
3. Argo CD автоматически обновляет развёртывание в Kubernetes

---

## 🧱 Архитектура

```mermaid
graph LR
  A[GitHub] -->|push to main| B(GitHub Actions)
  B -->|build & push| C[Yandex Container Registry]
  D[Argo CD] -->|sync every 3 min| E[Yandex Managed Kubernetes]
  C --> E
  E --> F[(myapp Pod)]
  G[Yandex Lockbox] -->|secrets| E
