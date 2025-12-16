# CI/CD Study Repository

GitHub Actions와 Docker를 활용한 CI/CD 학습용 레포지토리입니다.

## 🚀 빠른 시작

### 로컬 개발

```bash
# 1. MySQL DB 실행
docker-compose -f docker-compose.dev.yml up -d

# 2. 애플리케이션 실행
./gradlew bootRun
```

### CI/CD

GitHub에 push하면 자동으로 빌드 및 Docker 이미지가 GitHub Container Registry에 푸시됩니다.

## 📋 프로젝트 구조

```
cicd-study/
├── .github/workflows/ci-cd.yml  # CI/CD 파이프라인
├── Dockerfile                    # Docker 이미지 빌드
├── docker-compose.dev.yml        # 로컬 개발용 DB
├── src/                          # 소스 코드
└── build.gradle                  # Gradle 빌드 설정
```

## 🔗 참고 자료

- [GitHub Actions 문서](https://docs.github.com/en/actions)
- [Docker 문서](https://docs.docker.com/)
- [Spring Boot 문서](https://spring.io/projects/spring-boot)
