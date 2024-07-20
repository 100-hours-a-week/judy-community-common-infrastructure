### `common-infrastructure` `README.md`

# Judy Community Infrastructure

Judy Community 프로젝트의 모든 서비스 및 애플리케이션을 관리하는 Docker Compose 설정을 포함하고 있습니다. 이 레포지토리는 프로젝트의 공통 인프라를 설정하고 관리하기 위한 목적으로 사용됩니다.

## 구조

```
common-infrastructure/
├── docker-compose.yml
├── .env
├── README.md
└── scripts/
    ├── init-db.sh
    ├── start-services.sh
    └── stop-services.sh
```

## 기능

- MySQL 데이터베이스 설정 및 초기화
- 각 서비스 및 애플리케이션의 Docker Compose 설정
- 서비스 시작 및 중지를 위한 스크립트 제공

## 설치 및 실행

### 사전 요구 사항

- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/install/)

### Docker Compose 설정 시작

1. `.env` 파일을 생성하여 필요한 환경 변수를 설정합니다. 예:

    ```env
    MYSQL_ROOT_PASSWORD=root_password
    MYSQL_DATABASE=judy_community
    MYSQL_USER=judy_user
    MYSQL_PASSWORD=judy_password
    ```

2. Docker Compose를 사용하여 모든 서비스를 시작합니다:

    ```bash
    docker-compose up -d
    ```

    이 명령은 MySQL 데이터베이스 및 다른 공유 서비스를 시작합니다.

3. 각 서비스 컨테이너의 로그를 확인하려면 다음 명령을 사용합니다:

    ```bash
    docker-compose logs -f
    ```

### 데이터베이스 초기화

데이터베이스를 초기화하기 위한 스크립트가 `scripts/` 디렉토리에 포함되어 있습니다. 이 스크립트를 실행하여 데이터베이스를 초기화할 수 있습니다.

```bash
./scripts/init-db.sh
```

### 서비스 시작 및 중지

서비스를 시작하거나 중지하려면 다음 스크립트를 사용할 수 있습니다:

- 서비스 시작: `./scripts/start-services.sh`
- 서비스 중지: `./scripts/stop-services.sh`

## CI/CD 설정

CI/CD 파이프라인은 GitHub Actions를 사용하여 설정되어 있습니다. 워크플로우는 `.github/workflows` 디렉토리에 정의되어 있습니다. 이 워크플로우에는 Docker 이미지를 빌드하고 테스트하며 Docker Hub에 배포하는 단계가 포함됩니다.

GitHub 레포지토리 설정에서 다음과 같은 시크릿을 구성해야 합니다:

- `DOCKER_USERNAME`: Docker Hub 사용자명
- `DOCKER_PASSWORD`: Docker Hub 비밀번호

## 기여하기

커뮤니티의 기여를 환영합니다. 기여하려면 다음 단계를 따르세요:

1. 레포지토리를 포크합니다.
2. 새 브랜치를 만듭니다 (`git checkout -b feature/YourFeature`).
3. 변경 사항을 커밋합니다 (`git commit -m 'Add YourFeature'`).
4. 브랜치에 푸시합니다 (`git push origin feature/YourFeature`).
5. 새 Pull Request를 만듭니다.
