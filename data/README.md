# 🦅 FGI 공개 데이터 (daifulee/fgi-public-data · data/)

CNN 공포탐욕지수(Fear & Greed Index, FGI) 시계열 전량 보존 + 실시간 현재값. FGI_lane 모의 레인이 자동 갱신한다. 모의 관찰 전용 · 신호 ≠ 자본 · 투자 권유 아님.

| 파일 | 내용 | 갱신 | 불변성 |
|---|---|---|---|
| fgi_history.csv | 2011-01-03~ 일일 마감 FGI 전량 (Date, FGI, source). source=input_csv: 2011~2020-09-18 GitHub 보존본(정수)·2020-09-21~ CNN 일일 마감(소수) / source=cnn_api: 레인 입력에 없는 날짜를 CNN 창에서 보충 | 화~토 KST 10:00 | 추가 전용 — 기존 행 절대 불변 (최초 포착값 보존) |
| fgi_latest.json | CNN 현재 점수·등급·CNN timestamp·전일/1주/1개월/1년 비교값, fetched_utc | 매시(미국 장중) + 일일 | 덮어쓰기 |
| fgi_intraday.csv | 실시간 수집 로그 (fetched_utc, cnn_timestamp, score, rating, 비교값) | 매시(미국 장중) | 추가 전용 (CNN timestamp 동일 시 중복 없음) |
| run_status.json | 일일 실행 상태 — 주문 번호(run_id·입력/레지스트리/엔진 sha256)·단계별 성공/실패/생략·종합 판정·막힌 단계·재개 지점 | 일일 | 덮어쓰기 |
| fgi_cnn_window.csv | CNN API 창 그대로 (최근 ≈1년, 당일 장중 잠정값 포함, CNN 사후 수정값 반영) | 매시 + 일일 | 덮어쓰기 (잠정값 창) |

주의: CNN 은 과거 일자 값을 사후 수정하는 경우가 있다 (예: 2026-11-06 레인 포착 22.08 → 이후 API 24.35). fgi_history.csv 는 레인이 신호에 쓴 최초 포착값을 보존하고, fgi_cnn_window.csv 가 CNN 의 현재 버전을 보여준다. 둘이 다르면 "수정됨"이지 오류가 아니다.
