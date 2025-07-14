# 🚀 비트코인 GPT AI 자동매매 시스템

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Upbit](https://img.shields.io/badge/Exchange-Upbit-orange.svg)](https://upbit.com/)

OpenAI GPT-4를 활용한 KRW-BTC 자동매매 시스템입니다. 기술적 분석과 AI 판단을 결합하여 2시간마다 자동으로 매매 결정을 내립니다.

## 📋 목차
- [🚀 비트코인 GPT AI 자동매매 시스템](#-비트코인-gpt-ai-자동매매-시스템)
  - [📋 목차](#-목차)
  - [✨ 주요 기능](#-주요-기능)
  - [🔧 시스템 구조](#-시스템-구조)
  - [🛠️ 기술 스택](#️-기술-스택)
  - [📊 기술적 분석 지표](#-기술적-분석-지표)
  - [⚙️ 설치 및 설정](#️-설치-및-설정)
    - [로컬 환경 설정](#로컬-환경-설정)
    - [환경 변수 설정 (.env 파일)](#환경-변수-설정-env-파일)
    - [API 키 발급](#api-키-발급)
  - [🖥️ AWS EC2 서버 배포](#️-aws-ec2-서버-배포)
    - [서버 기본 설정](#서버-기본-설정)
    - [프로젝트 배포](#프로젝트-배포)
    - [서버 실행 및 관리](#서버-실행-및-관리)
  - [📱 텔레그램 알림](#-텔레그램-알림)
  - [⚠️ 주의사항](#️-주의사항)
  - [🔒 보안 고려사항](#-보안-고려사항)
  - [📈 성능 최적화](#-성능-최적화)
  - [🤝 기여하기](#-기여하기)
  - [📄 라이선스](#-라이선스)
  - [🛣️ 로드맵](#️-로드맵)

## ✨ 주요 기능

- **AI 기반 의사결정**: GPT-4 Turbo를 활용한 고도화된 매매 판단
- **실시간 기술적 분석**: 30일 일봉, 24시간 시간봉 데이터 분석
- **다양한 기술 지표**: RSI, MACD, 볼린저 밴드, 스토캐스틱 등 10여 가지 지표
- **자동 스케줄링**: 2시간마다 자동 실행
- **텔레그램 알림**: 매매 결과 실시간 알림
- **리스크 관리**: 수수료 및 슬리피지 고려한 매매
- **백그라운드 실행**: 서버 환경에서 24/7 운영 가능

## 🔧 시스템 구조

```
autotrade.py
├── 데이터 수집 (fetch_and_prepare_data)
│   ├── 업비트 OHLCV 데이터 (30일 일봉, 24시간 시간봉)
│   └── 기술적 지표 계산
├── AI 분석 (analyze_data_with_gpt4)
│   ├── GPT-4에 데이터 전송
│   ├── instructions.md 기반 분석
│   └── JSON 형태 매매 결정 반환
├── 매매 실행
│   ├── 매수 (execute_buy)
│   ├── 매도 (execute_sell)
│   └── 포지션 관리
└── 알림 시스템 (send_telegram_message)
    └── 텔레그램 봇을 통한 실시간 알림
```

## 🛠️ 기술 스택

- **Python 3.8+**: 메인 개발 언어
- **OpenAI GPT-4 Turbo**: AI 분석 엔진
- **pyupbit**: 업비트 API 래퍼
- **pandas & pandas_ta**: 데이터 처리 및 기술적 분석
- **schedule**: 자동 스케줄링
- **python-dotenv**: 환경 변수 관리
- **requests**: 텔레그램 API 통신

## 📊 기술적 분석 지표

| 지표 | 설명 | 활용 |
|------|------|------|
| SMA_10 | 10일 단순이동평균 | 단기 트렌드 파악 |
| EMA_10 | 10일 지수이동평균 | 최근 가격 변화에 민감한 트렌드 |
| RSI_14 | 14일 상대강도지수 | 과매수/과매도 구간 판단 |
| MACD | 이동평균 수렴확산 | 모멘텀 변화 감지 |
| Stochastic | 스토캐스틱 오실레이터 | 단기 반전 신호 |
| Bollinger Bands | 볼린저 밴드 | 변동성 및 지지/저항 |

## ⚙️ 설치 및 설정

### 로컬 환경 설정

1. **저장소 클론**
```bash
git clone https://github.com/your-username/AI_Trading_btc.git
cd AI_Trading_btc
```

2. **가상환경 생성 (권장)**
```bash
python -m venv venv
# Windows
venv\Scripts\activate
# Linux/Mac
source venv/bin/activate
```

3. **의존성 설치**
```bash
pip install -r requirements.txt
```

### 환경 변수 설정 (.env 파일)

프로젝트 루트에 `.env` 파일을 생성하고 다음 정보를 입력하세요:

```env
# OpenAI API 키
OPENAI_API_KEY=your_openai_api_key_here

# 업비트 API 키 (KRW 출금 권한 필요)
UPBIT_ACCESS_KEY=your_upbit_access_key_here
UPBIT_SECRET_KEY=your_upbit_secret_key_here

# 텔레그램 봇 설정 (선택사항)
TELEGRAM_BOT_TOKEN=your_telegram_bot_token
TELEGRAM_CHAT_ID=your_telegram_chat_id
```

### API 키 발급

1. **OpenAI API 키**
   - [OpenAI 플랫폼](https://platform.openai.com/)에서 발급
   - GPT-4 API 사용 권한 필요

2. **업비트 API 키**
   - [업비트 API 관리](https://upbit.com/mypage/open_api_management)에서 발급
   - 필요 권한: 자산 조회, 주문 조회, 주문하기, 출금하기
   - IP 주소 제한 설정 권장

3. **텔레그램 봇** (선택사항)
   - [@BotFather](https://t.me/botfather)에서 봇 생성
   - 봇 토큰 및 채팅 ID 확인

## 🖥️ AWS EC2 서버 배포

### 서버 기본 설정

1. **시간대 설정**
```bash
sudo ln -sf /usr/share/zoneinfo/Asia/Seoul /etc/localtime
```

2. **패키지 업데이트**
```bash
sudo apt update && sudo apt upgrade -y
```

3. **Python 및 pip 설치**
```bash
sudo apt install python3-pip python3-venv -y
```

### 프로젝트 배포

1. **저장소 클론**
```bash
git clone https://github.com/your-username/AI_Trading_btc.git
cd AI_Trading_btc
```

2. **가상환경 설정**
```bash
python3 -m venv venv
source venv/bin/activate
```

3. **의존성 설치**
```bash
pip3 install -r requirements.txt
```

4. **환경 변수 설정**
```bash
vim .env
# 또는
nano .env
```

### 서버 실행 및 관리

1. **일반 실행**
```bash
python3 autotrade.py
```

2. **백그라운드 실행**
```bash
nohup python3 -u autotrade.py > output.log 2>&1 &
```

3. **로그 확인**
```bash
# 전체 로그 보기
cat output.log

# 실시간 로그 모니터링
tail -f output.log
```

4. **프로세스 관리**
```bash
# 실행 중인 프로세스 확인
ps aux | grep autotrade.py

# 프로세스 종료
kill -9 [PID]
```

5. **시스템 서비스 등록** (권장)
```bash
sudo vim /etc/systemd/system/autotrader.service
```

```ini
[Unit]
Description=Bitcoin Auto Trading Bot
After=network.target

[Service]
Type=simple
User=ubuntu
WorkingDirectory=/home/ubuntu/AI_Trading_btc
Environment=PATH=/home/ubuntu/AI_Trading_btc/venv/bin
ExecStart=/home/ubuntu/AI_Trading_btc/venv/bin/python autotrade.py
Restart=always
RestartSec=10

[Install]
WantedBy=multi-user.target
```

```bash
sudo systemctl daemon-reload
sudo systemctl enable autotrader
sudo systemctl start autotrader
sudo systemctl status autotrader
```

## 📱 텔레그램 알림

시스템은 다음 상황에서 텔레그램 알림을 발송합니다:

- **매매 결정**: AI 분석 결과 및 결정 사유
- **매수 완료**: 매수 주문 체결 정보
- **매도 완료**: 매도 주문 체결 정보
- **에러 발생**: 시스템 오류 및 예외 상황

알림 예시:
```
🤖 AI 분석 결과
결정: 매수
사유: RSI 30 이하 진입, EMA 상향 돌파 신호 감지

💰 매수 완료
금액: 50,000 KRW
가격: 45,000,000 KRW
수량: 0.00111111 BTC
```

## ⚠️ 주의사항

1. **투자 리스크**: 암호화폐 투자는 높은 리스크를 동반합니다
2. **API 키 보안**: .env 파일을 절대 공개 저장소에 업로드하지 마세요
3. **테스트 필수**: 실제 자금 투입 전 충분한 테스트를 진행하세요
4. **시장 변동성**: AI 분석이 100% 정확하지 않을 수 있습니다
5. **수수료 고려**: 업비트 수수료 0.05%가 자동으로 계산됩니다

## 🔒 보안 고려사항

- **IP 화이트리스트**: 업비트 API에서 IP 제한 설정
- **권한 최소화**: 필요한 최소 권한만 부여
- **정기 키 갱신**: API 키를 정기적으로 갱신
- **로그 모니터링**: 비정상적인 거래 패턴 감시
- **2FA 활성화**: 업비트 계정에 2단계 인증 설정

## 📈 성능 최적화

- **메모리 사용량**: 약 50-100MB
- **CPU 사용률**: 분석 시 순간적으로 증가, 평시 1% 미만
- **네트워크**: API 호출로 인한 최소한의 트래픽
- **실행 주기**: 2시간마다 약 30초간 실행

## 🤝 기여하기

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 라이선스

이 프로젝트는 MIT 라이선스 하에 배포됩니다. 자세한 내용은 `LICENSE` 파일을 참조하세요.

## 🛣️ 로드맵

- [ ] **멀티 거래소 지원**: 빗썸, 바이낸스, 코인베이스 추가
- [ ] **웹 대시보드**: 실시간 모니터링 인터페이스
- [ ] **백테스팅**: 과거 데이터 기반 성능 검증
- [ ] **포트폴리오 관리**: 다중 코인 자동매매
- [ ] **고급 AI 모델**: GPT-4 외 다른 AI 모델 지원
- [ ] **모바일 앱**: 스마트폰 전용 모니터링 앱

---

**⚠️ 면책 조항**: 이 소프트웨어는 교육 목적으로 제공됩니다. 실제 투자에 사용할 경우 발생하는 손실에 대해 개발자는 책임지지 않습니다. 투자는 본인의 판단과 책임 하에 진행하시기 바랍니다.