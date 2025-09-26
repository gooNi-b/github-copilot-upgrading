# legacy와 upgraded 폴더 구조 분석

## 공통 폴더 및 파일 구조

- `MANIFEST.in`, `README.rst`, `setup.py`, `distribute_setup.py`, `distribute-0.6.10.tar.gz`
  - 프로젝트 메타 정보, 설치 스크립트, 배포 관련 파일
- `docs/`
  - 프로젝트 문서 및 Sphinx 기반 빌드 결과물 포함
  - `build/` (HTML, doctree 등 빌드 산출물)
  - `source/` (문서 원본 및 설정)
- `guachi/`
  - 실제 Python 패키지 소스 코드
  - `__init__.py`, `config.py`, `database.py` 등 핵심 모듈
  - `tests/` (테스트 코드: 여러 테스트 파일 포함)
- `guachi.egg-info/`
  - 패키지 메타데이터 (빌드/설치 시 생성)
- 기타
  - 프로젝트에 필요한 추가 파일 및 폴더

## 분석 및 특징

- **구조적 동일성**: `legacy`와 `upgraded`는 파일 및 폴더 구조가 동일합니다. 이는 업그레이드 작업을 위한 복사본으로, 기존 코드를 최신 Python 환경에 맞게 수정·테스트하기 위한 목적입니다.
- **문서화 및 테스트**: `docs` 폴더에 Sphinx 기반 문서가 포함되어 있고, `guachi/tests`에 단위 및 통합 테스트가 존재합니다. 이는 기능 검증과 업그레이드 후 테스트에 활용됩니다.
- **패키징 및 배포**: `setup.py`, `MANIFEST.in`, `guachi.egg-info` 등은 Python 패키지로 배포하기 위한 표준 구조입니다.
- **레거시 요소**: `distribute_setup.py`, `distribute-0.6.10.tar.gz` 등은 Python 2.x 시대의 패키징 도구로, 업그레이드 시 modern Python 패키징(`pyproject.toml` 등)으로 변경이 필요합니다.

## 활용 방안

- `upgraded` 폴더에서 최신 Python 문법, 패키징, 테스트 프레임워크(Pytest 등)로 점진적으로 코드와 설정을 변경·검증할 수 있습니다.
- 구조가 동일하므로, 변경 전/후 비교 및 테스트가 용이합니다.
- 문서와 테스트가 잘 갖춰져 있어 기능 단위로 slice 작업 및 검증이 가능합니다.

---

추가적으로 각 폴더/파일의 상세 역할이나, 업그레이드 시 주의할 점이 궁금하다면 말씀해 주세요.
