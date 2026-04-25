# Doppler Waveform Simulator — AI Maintainer Guide

상지 동맥 도플러 파형 교육용 시뮬레이터. Raynaud's 진단을 위한 정상·이상 파형 비교.

- Live: https://seltsky.github.io/doppler-waveform/
- 단일 파일 앱 (index.html만 있음, 모든 코드 인라인)

## 사용자 프로파일

- 의사·연구자 (Interventional Radiology + 혈관 검사)
- 한국어, 존댓말, 마크다운 금지(불릿 OK)
- Raynaud's 환자 진단 보조 도구로 사용

## 핵심 컨셉

교육 목적의 인터랙티브 시뮬레이터:

- Interactive: 매개변수 (PSV, EDV, RI 등) 슬라이더로 조정 → 파형 실시간 그림
- Normal vs Raynaud: 정상 vs 비정상 파형 나란히 비교
- Vessel Map: 상지 동맥 해부도 (axillary → brachial → radial/ulnar/interosseous)
- Clinical Scenarios: 사전 정의된 케이스 (cold-induced, severe, mild)
- Exam Protocol: 검사 프로토콜 가이드

## 기술 스택

- 단일 HTML 파일 (CSS·JS 인라인)
- Canvas API로 파형 그리기
- 외부 의존성 없음
- 데이터 저장 없음 (교육용이라 진행 추적 불필요)

## 파일 구조

```
doppler-waveform/
└── index.html       모든 것 (HTML + CSS + JS + Canvas)
```

가장 단순한 앱. 단일 파일 유지 권장.

## 절대 하지 말 것

1. **분리 파일 만들기 금지** — 단일 파일이 의도. 배포·복제·공유 단순함이 가치
2. **외부 라이브러리 추가 금지** — Chart.js·D3 등 도입 X. Canvas vanilla로 충분
3. **물리적으로 부정확한 파형 생성 금지** — 의학 교육 도구라 정확도 우선
4. **데이터 저장 기능 추가 금지** — 교육 도구라 stateless 유지

## 자주 받을 요청

### "새 파형 패턴 추가"
- index.html 안 scenarios 객체에 추가
- 매개변수: peak, end-diastolic, RI, PI, waveform shape

### "다른 혈관 추가 (예: 하지 동맥)"
- 별도 vesselMap 추가 또는 새 모드
- 단순 vs 복잡 판단 — 단순 유지가 우선이면 별도 앱으로 분리도 OK

### "한국어/영어 토글"
- 라벨 객체 추가 + 토글 버튼

### "PDF 보고서 출력"
- 교육 도구 역할 흐려질 위험. 신중

## 의학 정확도

도플러 파형 모양은 임상 가르침의 핵심:
- Normal triphasic: sharp upstroke, brief reverse flow, late forward
- Raynaud (cold induced): blunted upstroke, delayed peak, no reverse
- Severe stenosis: tardus parvus, monophasic
- Calcified: spiked, irregular

매개변수·식 변경 시 사용자(IR 전문의)와 검증 권장.

## 다른 시스템과의 관계

- 이 앱은 독립적 교육 도구. 다른 앱·메모리·launchd 연동 없음
- 연관: 사용자가 Raynaud's 환자 판독 시 참고 (환자별 케이스는 EMR에)

## 텔레그램 응답 톤

- 의학 정확도 + 단순함 동시 추구
- 새 기능 추가 시 "정말 필요한가" 한 번 더 묻기

마지막 업데이트: 2026-04-26
