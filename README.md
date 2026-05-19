# Samwoo PDF Box

삼우에레코 내부용 PDF 문서 관리 SPA. 빌드 없이 `index.html` 하나로 동작합니다.

## 기능

- **PDF 업로드** — 드래그앤드롭 또는 파일 선택, 최대 50MB, 다중 파일 동시 업로드
- **문서 편집 모달** — 업로드 시 제목 수정 + 카테고리 태그 선택 (규정/매뉴얼/견적/기타)
- **퍼지 검색** — Fuse.js 기반 제목·태그 검색 + PDF 본문 텍스트 검색
- **카테고리 필터** — 사이드바에서 카테고리별 문서 필터
- **PDF 미리보기** — 카드 클릭 시 pdf.js Canvas 모달, 페이지 이동, ESC 닫기
- **다크 모드** — 🌙/☀️ 토글, LocalStorage 저장
- **ZIP 내보내기** — 전체 문서 + metadata.json 압축 다운로드
- **영속성** — PDF Blob은 IndexedDB, 메타데이터는 LocalStorage에 저장 (새로고침 후 유지)

## 사용 방법

별도 설치 없이 `index.html`을 브라우저에서 열면 바로 사용 가능합니다.

```bash
# 저장소 클론
git clone https://github.com/blueskyho82/pdfbox.git
cd pdfbox

# index.html을 브라우저에서 열기
```

## 기술 스택

| 역할 | 라이브러리 |
|------|-----------|
| 스타일 | Tailwind CSS CDN |
| PDF 렌더링 | pdf.js 4.2.67 |
| 퍼지 검색 | Fuse.js 7.0.0 |
| ZIP 생성 | JSZip 3.10.1 |
| 저장소 | IndexedDB (Blob) + LocalStorage (메타데이터) |

## 데이터 구조

```json
{
  "id": "uuid",
  "title": "문서 제목",
  "tags": ["규정", "매뉴얼"],
  "fileName": "original.pdf",
  "fileSize": 102400,
  "uploadedAt": "2026-05-19T00:00:00.000Z",
  "pageCount": 12,
  "thumbDataUrl": "data:image/jpeg;base64,..."
}
```

## 브라우저 지원

Chrome / Edge 최신 버전 권장 (IndexedDB + pdf.js ES Module 필요)
