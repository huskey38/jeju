# 제주 3D 대표경관 지도

제주의 대표경관을 **입체 지도**로 보여 주는 Vite + React 앱입니다. 방문자는 화면을 회전·기울이고 확대하며 관광지를 3차원으로 탐색할 수 있습니다.

## 조작법
- 왼쪽 드래그: 이동
- 오른쪽 드래그(또는 Ctrl+드래그): 회전·기울기
- 마우스 휠: 확대/축소 (터치는 두 손가락)
- 왼쪽 목록 또는 지도 위 핀을 누르면 해당 경관으로 날아가 설명 팝업이 열립니다.

## 구성
- MapLibre GL: 위성사진(Esri) + 고도 데이터(AWS Terrain Tiles)로 입체 지형 생성 (지도 키 불필요)
- `src/data/landmarks.js`: 기본 대표경관 10곳 (한라산, 성산일출봉, 산방산 등)
- `api/landscape.js`: 공공데이터포털 대표경관 API 프록시 (인증키를 브라우저에 노출하지 않음)

## 실행
Node.js 18 이상이 필요합니다.

```powershell
npm install
npm run dev      # http://localhost:5173
npm run build
```

## 공공데이터 API (선택)
1. data.go.kr 에서 해당 데이터셋에 활용신청 후 인증키 확인
2. 로컬: `.env.example` 을 `.env` 로 복사해 `DATA_GO_KR_KEY=발급받은키` 입력 → 개발 서버 재시작
3. Vercel: Settings → Environment Variables 에 `DATA_GO_KR_KEY` 추가(`VITE_` 붙이지 않음, Sensitive 가능) → Redeploy
4. 확인: 배포주소/api/landscape 를 열어 JSON 이 나오는지 봅니다.

키가 없거나 API가 실패하면 기본 대표경관 10곳으로 계속 동작합니다.

## Vercel 배포
저장소를 Import 하고 Root Directory 는 비워 둡니다. (Framework: Vite, Build: `npm run build`, Output: `dist`)

## 출처
위성영상 © Esri, Maxar, Earthstar Geographics · 지형 © Mapzen / AWS Terrain Tiles
