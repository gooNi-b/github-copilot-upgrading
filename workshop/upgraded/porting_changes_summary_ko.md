# legacy → upgraded Python 3.x 포팅 변경 내역

## 주요 변경 사항

1. **Python 2.x 문법 → Python 3.x 문법**
   - print 문, except 문 등 Python 3.x 문법으로 변경
   - 유니코드 리터럴(u'문자열') 제거
   - dict.keys(), dict.items() 등 반환값 관련 변경

2. **레거시 라이브러리 호환성**
   - ConfigParser → configparser
   - distribute, distutils 관련 코드 제거 및 setuptools로 통일

3. **테스트 코드 및 패키징**
   - unittest 기반 테스트에서 Pytest 호환되도록 assert 등 문법 확인
   - 테스트 코드 내 유니코드 리터럴 제거
   - setup.py에서 distribute_setup 의존성 제거, modern setuptools만 사용

4. **기타 Python 3.x 호환성**
   - 파일 인코딩, open 함수 등 기본 동작 변경
   - Sqlite3 등 DB 관련 타입 처리

## 적용 파일
- guachi/config.py
- guachi/database.py
- guachi/__init__.py
- guachi/tests/test_configmapper.py
- guachi/tests/test_configurations.py
- guachi/tests/test_database.py
- guachi/tests/test_integration.py
- setup.py

## 변경 예시
- `self.assertEqual(foo['bar'], u'beer')` → `self.assertEqual(foo['bar'], 'beer')`
- `ConfigParser` → `configparser`
- `except Exception, e:` → `except Exception as e:`
- `dict.keys()` → `list(dict.keys())` (필요시)

---

이 문서는 `/workspaces/github-copilot-upgrading/workshop/README_ko.md`의 안내에 따라 Python 3.x 환경에서 정상 작동하도록 legacy 코드를 upgraded 폴더에 반영한 주요 변경 내역을 정리한 것입니다.
