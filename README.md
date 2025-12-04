# CI/CD Study Repository

GitHub Actions와 Docker를 활용한 CI/CD 학습용 레포지토리입니다.

## 📚 학습 목표

이 레포지토리를 통해 다음을 학습할 수 있습니다:

- **GitHub Actions**: 자동화된 CI/CD 파이프라인 구축
- **Docker**: 컨테이너화 및 멀티 스테이지 빌드
- **Spring Boot**: Java 애플리케이션 빌드 및 배포

## 🏗️ 프로젝트 구조

```
cicd-study/
├── .github/
│   └── workflows/
│       └── ci-cd.yml          # GitHub Actions 워크플로우
├── src/                        # 소스 코드
├── Dockerfile                  # Docker 이미지 빌드 파일
├── .dockerignore              # Docker 빌드 시 제외할 파일
└── build.gradle               # Gradle 빌드 설정
```

## 🚀 CI/CD 파이프라인

### 워크플로우 트리거

- **Push 이벤트**: `main` 또는 `master` 브랜치에 push 시
- **Pull Request**: PR 생성/업데이트 시

### 파이프라인 단계

1. **Build and Test**
   - 코드 체크아웃
   - Java 17 환경 설정
   - Gradle 의존성 캐싱
   - 테스트 실행
   - 애플리케이션 빌드

2. **Docker Build and Push**
   - Docker 이미지 빌드
   - GitHub Container Registry에 푸시
   - 이미지 태그: `latest`, `branch-name`, `branch-sha`

## 🐳 Docker

### 로컬에서 빌드 및 실행

```bash
# Docker 이미지 빌드
docker build -t cicd-study:latest .

# 컨테이너 실행
docker run -p 8080:8080 cicd-study:latest
```

### 멀티 스테이지 빌드

Dockerfile은 두 단계로 구성됩니다:

1. **빌드 스테이지**: Gradle을 사용하여 JAR 파일 생성
2. **실행 스테이지**: JRE만 포함한 경량 이미지로 최종 배포

이를 통해 최종 이미지 크기를 최소화합니다.

## 📦 GitHub Container Registry

빌드된 Docker 이미지는 GitHub Container Registry에 자동으로 푸시됩니다.

이미지 주소: `ghcr.io/{username}/cicd-study:latest`

### 이미지 사용 방법

```bash
# GitHub Container Registry에서 이미지 가져오기
docker pull ghcr.io/{username}/cicd-study:latest

# 실행
docker run -p 8080:8080 ghcr.io/{username}/cicd-study:latest
```

## ⚙️ 설정

### GitHub Secrets (선택사항)

Docker Hub를 사용하려면 다음 secrets를 설정하세요:

- `DOCKER_USERNAME`: Docker Hub 사용자명
- `DOCKER_TOKEN`: Docker Hub 액세스 토큰

GitHub Container Registry는 `GITHUB_TOKEN`을 자동으로 사용하므로 별도 설정이 필요 없습니다.

## 🧪 테스트

로컬에서 테스트 실행:

```bash
./gradlew test
```

## 📝 참고사항

- 이 레포지토리는 학습 목적으로 만들어졌습니다.
- 실제 프로덕션 환경에 배포하기 전에 보안 설정을 확인하세요.
- 필요에 따라 워크플로우를 수정하여 사용하세요.

## 🔗 참고 자료

- [GitHub Actions 문서](https://docs.github.com/en/actions)
- [Docker 문서](https://docs.docker.com/)
- [Spring Boot 문서](https://spring.io/projects/spring-boot)

# cicd-study
