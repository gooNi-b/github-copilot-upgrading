# distribute_setup.py 및 setup.py Python 3 포팅 수정 내역

## 1. distutils → setuptools 변경
- Python 3.12부터 distutils가 제거되어, distribute_setup.py에서 distutils 대신 setuptools 사용하도록 변경함.

## 2. setuptools.logger → logging 모듈 변경
- 최신 setuptools에는 logger 모듈이 없어, logging 모듈로 로그 처리하도록 변경함.

## 3. tarfile 관련 디렉터리 속성 설정 코드 제거
- _extractall 함수에서 chown, utime, chmod 등 디렉터리 속성 설정 코드 제거하여 Python 3 호환성 확보.

## 4. setuptools 설치
- pip install setuptools 명령으로 setuptools 패키지 설치.

## 5. egg 빌드 실패
- distribute 및 distutils 의존성으로 인해 egg 빌드가 실패함. 이는 distribute가 더 이상 지원되지 않기 때문임.

## 6. modern packaging 권장
- setup.py에서 distribute_setup 의존성을 제거하고, pyproject.toml 기반 modern packaging으로 전환 필요.

---

이 문서는 Python 3.12 이상 환경에서 레거시 패키징 코드를 포팅하며 발생한 주요 수정 내역과 원인을 정리한 것입니다.
