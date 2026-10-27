[README_공개배포.md](https://github.com/user-attachments/files/34000407/README_.md)
# 로케이션 현황판 공개 URL 배포 안내

## 배포 방법 (GitHub Pages)
1. github.com 로그인 후 New repository를 눌러 새 **Public** 저장소를 만듭니다. 예: `warehouse-dashboard`.
2. 이 ZIP 파일을 풀고 `index.html`, `latest.json`, `.nojekyll` 세 파일을 저장소 **최상위(root)** 에 업로드합니다. ZIP 자체를 업로드하면 동작하지 않습니다.
3. 저장소 **Settings → Pages → Build and deployment → Deploy from a branch**를 선택하고 `main` / `/(root)`로 설정 후 Save합니다.
4. 몇 분 후 Pages 화면에서 공개 주소를 확인합니다. 주소 예시: `https://계정명.github.io/warehouse-dashboard/`. 이는 예시이며 실제 URL은 게시 후 결정됩니다.
5. 해당 주소를 열어 창고·랙 조회 및 SKU 상세정보를 테스트합니다.

## 최신 데이터 갱신 (과거 기록 화면 미표시)
- `latest.json`을 최신 데이터로 변환해 같은 이름으로 덮어써 업로드/커밋합니다.
- 이 배포용 ZIP에는 변환 스크립트도 `tools/update_data.py`로 동봉했습니다. 스크립트는 `master/latest.xlsx`를 읽고 `latest.json`을 생성하므로, 갱신 시 작업 PC에서 `master/latest.xlsx`를 교체하고 `python tools/update_data.py`를 실행하세요. `pip install openpyxl`이 필요합니다.
- **중요**: 스크립트가 실행되려면 ZIP을 푼 폴더 안에 `master/latest.xlsx`를 직접 만들어 두어야 합니다. 이 엑셀은 GitHub에 업로드할 필요가 없습니다.
- GitHub에 `latest.json`을 교체 커밋하면 현황판은 최신 내용만 표시하지만, Git 커밋 이력에 과거 데이터가 남을 수 있습니다. GitHub 이력까지 완전히 없애는 방식은 아닙니다.

## 공개 주의
- **로그인/암호 보호가 전혀 없습니다.** URL을 모르는 사람도 검색·접근할 수 있습니다.
- `latest.json` 전체가 공개되며, 재고·상품명·바코드·창고 위치가 포함됩니다.
- 외부 공개 승인을 받은 데이터만 업로드하세요.
- GitHub Pages 배포는 외부 서비스 설정이 필요하며 이 패키지 생성만으로 실제 URL이 발급되지는 않습니다.
