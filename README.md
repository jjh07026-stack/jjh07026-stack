# 정준혁 | Design Verification Engineer 지망

> 테스트가 모두 통과해도, 그 테스트가 만들지 못한 상황에 버그는 숨어 있다고 생각합니다.
> 설계를 직접 만들고, 의심하고, 숫자로 증명하는 검증 엔지니어를 목표로 합니다.

- 전자전기공학부 반도체공학전공 (2027.02 졸업 예정)
- 대한상공회의소 AI 시스템반도체 설계 2기 (2026.09 ~ 2027.03)
- 관심 분야: SystemVerilog · UVM 기반 설계 검증, 디지털 RTL 설계, 온디바이스 AI

## Tech Stack

| 분야 | 기술 |
|---|---|
| HDL · 검증 | Verilog, SystemVerilog, UVM (학습 중) |
| 툴 · 보드 | Vivado, XSim, Cadence Virtuoso, Basys-3 (Artix-7) |
| 임베디드 · AI | Python, Raspberry Pi 5, ESP32, YOLO11 · TFLite, OpenCV |
| 서버 · 기타 | Flask, MySQL, Linux |

## Projects

### 🔍 RTL 설계 · 검증

| 프로젝트 | 내용 | 검증 결과 |
|---|---|---|
| [**UART FIFO Loopback**](https://github.com/jjh07026-stack/uart-fifo-loopback) <br> 개인 · 2026.10 | UART RX/TX + 4-depth FIFO 2단 루프백 설계, sender · receiver · scoreboard 테스트벤치 직접 작성 | 랜덤 16 byte **PASS 16 / FAIL 0** <br> 코드 분석으로 `tx_busy` 1클럭 지연에 의한 데이터 유실 가능성 발견 |
| [**Sensor & UART Control System**](https://github.com/jjh07026-stack/fpga-sensor-uart-system) <br> 4인 · 2026.11 | Watch · Stopwatch · DHT11 · HC-SR04 · UART 명령 제어 통합 <br> **담당: 전체 통합, Control Unit, 전체 검증** | 통합 시나리오 **4 / 4 PASS** <br> 타이밍 · 핸드셰이크 · 예외 처리 문제 **4건 원인 분석 및 해결** |
| [**Digital Watch & Stopwatch**](https://github.com/jjh07026-stack/fpga-watch-stopwatch) <br> 2인 · 2026.10 | FSM 기반 시계 · 스톱워치, 버튼 디바운스, FND 제어 | 시 설정 +10 범위 오류(14 → 24) 재현 및 수정 |

### 🤖 온디바이스 AI · 임베디드

| 프로젝트 | 내용 | 결과 |
|---|---|---|
| [**저전력 온디바이스 AI 영유아 위험 알림**](https://github.com/jjh07026-stack/ondevice-ai-baby-safety) <br> 4인 · 2026.09 | Raspberry Pi 5에서 YOLO11n(TFLite)으로 아기와 위험 물체의 거리를 판단해 휴대폰 알림 <br> **담당: Python 코드 구현** | 4상태 전력 관리로 소비 전력 **−56 %** (4.61 → 2.01 W) |
| [**객체 탐지 기반 실시간 가위바위보**](https://github.com/jjh07026-stack/rps-object-detection-game) <br> 개인 · 2026.09 | 카메라로 두 사람의 손동작을 TFLite 객체 탐지로 인식해 승패 판정, NMS · 좌우 위치 기반 P1/P2 구분 | 3클래스 실시간 판정, 2프레임마다 추론 |
| **공유킥보드 주행구역 판별 및 패널티 부여 시스템** <br> 졸업작품 · 팀장 (3인) · 2025 ~ 2026 | YOLO11 기반 인도 · 도로 실시간 판별 → LED 경고 · 리니어 모터 감속, Flask 서버 · 앱 연동 <br> **담당: 팀 총괄, 서버 · 앱, Python, 하드웨어 보조** | YOLO 4종 동일 조건 비교로 모델 선정 (mAP50 0.905) <br> 14 → 40 FPS 최적화, 헬멧 착용 판정 80회 100 % |

## TODO

**UART FIFO Loopback — `tx_busy` 버그 재현 · 수정 · 재검증**
- [ ] 5 byte 이상 연속 송신 테스트벤치 추가 (FIFO full · overflow 검증)
- [ ] 연속 송신으로 `tx_busy` 1클럭 지연에 의한 데이터 유실 재현
- [ ] `uart_tx` 수정: IDLE에서 `tx_start`를 받는 순간 `tx_busy_next = 1`
- [ ] 수정 후 기존 테스트(FIFO 단독, 1 byte, 랜덤 16 byte) + 연속 송신 테스트 다시 실행해 PASS 확인
- [ ] 수정 전후 파형 캡처와 결과를 [uart-fifo-loopback](https://github.com/jjh07026-stack/uart-fifo-loopback) README에 정리

## Awards

| 연도 | 대회 | 수상 |
|---|---|---|
| 2026 | IT 공학대전 (교내) | **최우수상** |
| 2026 | 창의적 종합설계 경진대회 | 특별상 |
| 2025 | 경상북도형 캡스톤디자인 | 장려상 |

> 세 상 모두 같은 졸업작품을 단계적으로 고도화하며 받은 결과입니다.

## Education & Certificates

- 대한상공회의소 AI 시스템반도체 설계 2기 (2026.09 ~ 2027.03, 수료 예정)
- 반도체 부트캠프 마이크로디그리 수료
- 디지털 설계 실무 과정 (Vivado RTL 설계, Cadence Virtuoso), Vivado SoC 설계 과정 수료
- 한국사능력검정시험
