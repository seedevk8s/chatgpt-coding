# ChatGPT를 활용한 프로그래밍 실전경험
## JavaScript 기본코드 작성 및 AI 코딩 활용법

---

## 목차
1. 소개 및 강의 개요 (10분)
2. JavaScript 기본 코드 작성 실습 (30분)
3. ChatGPT를 활용한 코딩방법 소개 (20분)
4. 실전 프로젝트: 추억의 탱크 게임 개발 (45분)
5. 질의응답 및 마무리 (15분)

---

## 1. 소개 및 강의 개요

### 강사 소개
- 이름 및 경력
- IT 분야 및 AI 활용 경험

### 오늘의 학습 목표
- JavaScript 기본 코드 작성 능력 향상
- ChatGPT를 활용한 효율적인 코딩 방법 습득
- AI 도구를 활용한 실제 프로젝트 개발 경험

### 왜 ChatGPT와 프로그래밍인가?
- AI 시대의 새로운 개발 패러다임
- 개발 생산성 향상과 학습 곡선 단축
- 비전공자도 코딩에 접근하기 쉬운 환경

---

## 2. JavaScript 기본 코드 작성 실습

### JavaScript 기초
- 변수와 데이터 타입
```javascript
// 변수 선언과 할당
let gameName = "탱크 게임";
const playerLife = 3;
var score = 0; // 최신 JavaScript에서는 let, const 사용 권장
```

### 함수와 조건문
```javascript
// 함수 정의
function movePlayer(direction) {
  if (direction === "left") {
    player.x -= 5;
  } else if (direction === "right") {
    player.x += 5;
  }
}
```

### 배열과 반복문
```javascript
// 배열 생성과 반복
const enemies = ["tank1", "tank2", "tank3"];
for (let i = 0; i < enemies.length; i++) {
  console.log(`적 탱크: ${enemies[i]} 출현!`);
}

// forEach 방식 (현대적 접근법)
enemies.forEach(enemy => {
  console.log(`적 탱크: ${enemy} 출현!`);
});
```

### 객체 활용하기
```javascript
// 게임 객체 생성
const tank = {
  x: 100,
  y: 200,
  speed: 5,
  life: 3,
  fire: function() {
    console.log("발사!");
    // 발사 로직 구현
  }
};
```

### 실습 1: 간단한 게임 로직 구현
- 플레이어 이동 함수 작성하기
- 충돌 감지 함수 만들기
- 점수 계산 로직 구현하기

---

## 3. ChatGPT를 활용한 코딩방법 소개

### ChatGPT란?
- GPT(Generative Pre-trained Transformer) 모델 소개
- 코드 생성 및 디버깅 능력
- 한계점과 활용 시 주의사항

### 효과적인 프롬프트 작성법
- 명확하고 구체적인 요구사항 전달하기
- 단계별 질문과 반복적 개선
- 코드 오류 해결을 위한 질문 방법

### 실습 예시: 간단한 코드 생성하기
```
[프롬프트 예시]
"JavaScript로 키보드 방향키 입력을 감지하여 캔버스에 있는 
탱크를 움직이는 코드를 작성해주세요. 탱크는 객체로 
표현되며 x, y 좌표와 이동 속도를 가지고 있습니다."
```

### ChatGPT 활용 실습
- 본인의 코드에 대한 개선점 찾기
- 특정 기능 구현을 위한 코드 생성
- 오류 디버깅 지원 받기

---

## 4. 실전 프로젝트: 추억의 탱크 게임 개발

### 프로젝트 개요
- HTML5 Canvas를 활용한 2D 탱크 게임
- 주요 기능: 이동, 발사, 충돌 감지, 점수 계산
- 단계별 개발 접근법

### 기본 게임 화면 구성
```javascript
// Canvas 설정
const canvas = document.getElementById('gameCanvas');
const ctx = canvas.getContext('2d');
canvas.width = 800;
canvas.height = 600;

// 게임 요소 초기화
const player = {
  x: canvas.width / 2,
  y: canvas.height - 50,
  width: 40,
  height: 40,
  speed: 5,
  color: 'blue'
};
```

### 키보드 입력 처리
```javascript
// 키보드 이벤트 처리
const keys = {};

document.addEventListener('keydown', (e) => {
  keys[e.key] = true;
});

document.addEventListener('keyup', (e) => {
  keys[e.key] = false;
});

function handlePlayerMovement() {
  if (keys['ArrowLeft'] && player.x > 0) {
    player.x -= player.speed;
  }
  if (keys['ArrowRight'] && player.x < canvas.width - player.width) {
    player.x += player.speed;
  }
}
```

### 탱크 발사 기능 구현
```javascript
// 총알 배열
const bullets = [];

// 발사 함수
function fireBullet() {
  bullets.push({
    x: player.x + player.width / 2 - 2.5,
    y: player.y,
    width: 5,
    height: 10,
    speed: 7,
    color: 'red'
  });
}

// 스페이스바 입력 감지
document.addEventListener('keydown', (e) => {
  if (e.key === ' ' && !keys[' ']) {
    fireBullet();
  }
  keys[e.key] = true;
});
```

### ChatGPT 활용한 게임 기능 확장
- 적 탱크 생성 및 이동 패턴 구현
- 레벨 시스템 설계
- 사운드 효과 추가

### 실습 2: ChatGPT와 함께 게임 완성하기
- 기존 코드에 적 탱크 추가하기
- 점수 시스템 구현하기
- 게임 오버 및 재시작 기능 추가하기

---

## 5. 질의응답 및 마무리

### 주요 학습 내용 요약
- JavaScript 기본 코드 작성 능력
- ChatGPT를 활용한 코딩 방법
- 실전 프로젝트 경험

### 추가 학습 자원
- 추천 도서 및 온라인 강좌
- 유용한 웹사이트 및 GitHub 저장소
- AI 코딩 도구 모음

### 실전 적용 아이디어
- 다른 유형의 게임으로 확장하기
- 웹 애플리케이션에 게임 기능 통합하기
- 포트폴리오 프로젝트로 활용하기

---

## 부록: 완성된 탱크 게임 코드

```javascript
// 전체 게임 코드
const canvas = document.getElementById('gameCanvas');
const ctx = canvas.getContext('2d');
canvas.width = 800;
canvas.height = 600;

// 플레이어 탱크
const player = {
  x: canvas.width / 2 - 20,
  y: canvas.height - 60,
  width: 40,
  height: 40,
  speed: 5,
  color: 'blue'
};

// 키 입력 상태
const keys = {};

// 총알 배열
const bullets = [];

// 적 탱크 배열
const enemies = [];

// 게임 상태
let score = 0;
let gameOver = false;
let level = 1;

// 키보드 이벤트 리스너
document.addEventListener('keydown', (e) => {
  if (e.key === ' ' && !keys[' ']) {
    fireBullet();
  }
  keys[e.key] = true;
});

document.addEventListener('keyup', (e) => {
  keys[e.key] = false;
});

// 총알 발사 함수
function fireBullet() {
  bullets.push({
    x: player.x + player.width / 2 - 2.5,
    y: player.y,
    width: 5,
    height: 10,
    speed: 7,
    color: 'red'
  });
}

// 적 탱크 생성 함수
function createEnemy() {
  const enemy = {
    x: Math.random() * (canvas.width - 30),
    y: 0,
    width: 30,
    height: 30,
    speed: 1 + Math.random() * level,
    color: 'green'
  };
  enemies.push(enemy);
}

// 게임 요소 업데이트
function update() {
  if (gameOver) return;
  
  // 플레이어 이동
  if (keys['ArrowLeft'] && player.x > 0) {
    player.x -= player.speed;
  }
  if (keys['ArrowRight'] && player.x < canvas.width - player.width) {
    player.x += player.speed;
  }
  
  // 총알 이동
  for (let i = 0; i < bullets.length; i++) {
    bullets[i].y -= bullets[i].speed;
    
    // 화면 밖으로 나간 총알 제거
    if (bullets[i].y < 0) {
      bullets.splice(i, 1);
      i--;
    }
  }
  
  // 적 탱크 이동
  for (let i = 0; i < enemies.length; i++) {
    enemies[i].y += enemies[i].speed;
    
    // 화면 아래로 나간 적 제거
    if (enemies[i].y > canvas.height) {
      enemies.splice(i, 1);
      i--;
      gameOver = true;
    }
  }
  
  // 충돌 감지 (총알과 적 탱크)
  for (let i = 0; i < bullets.length; i++) {
    for (let j = 0; j < enemies.length; j++) {
      if (checkCollision(bullets[i], enemies[j])) {
        score += 10;
        bullets.splice(i, 1);
        enemies.splice(j, 1);
        i--;
        break;
      }
    }
  }
  
  // 충돌 감지 (플레이어와 적 탱크)
  for (let i = 0; i < enemies.length; i++) {
    if (checkCollision(player, enemies[i])) {
      gameOver = true;
    }
  }
  
  // 레벨 업
  if (score > level * 100) {
    level++;
  }
  
  // 적 탱크 생성 (확률 기반)
  if (Math.random() < 0.02 + (level * 0.005)) {
    createEnemy();
  }
}

// 충돌 감지 함수
function checkCollision(obj1, obj2) {
  return obj1.x < obj2.x + obj2.width &&
         obj1.x + obj1.width > obj2.x &&
         obj1.y < obj2.y + obj2.height &&
         obj1.y + obj1.height > obj2.y;
}

// 그리기 함수
function draw() {
  // 캔버스 지우기
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  
  // 배경
  ctx.fillStyle = '#f0f0f0';
  ctx.fillRect(0, 0, canvas.width, canvas.height);
  
  // 플레이어 탱크
  ctx.fillStyle = player.color;
  ctx.fillRect(player.x, player.y, player.width, player.height);
  
  // 포신 그리기
  ctx.fillStyle = 'black';
  ctx.fillRect(player.x + player.width/2 - 2, player.y - 10, 4, 10);
  
  // 총알
  for (const bullet of bullets) {
    ctx.fillStyle = bullet.color;
    ctx.fillRect(bullet.x, bullet.y, bullet.width, bullet.height);
  }
  
  // 적 탱크
  for (const enemy of enemies) {
    ctx.fillStyle = enemy.color;
    ctx.fillRect(enemy.x, enemy.y, enemy.width, enemy.height);
    
    // 적 포신 그리기
    ctx.fillStyle = 'black';
    ctx.fillRect(enemy.x + enemy.width/2 - 2, enemy.y + enemy.height, 4, 10);
  }
  
  // 점수 표시
  ctx.fillStyle = 'black';
  ctx.font = '20px Arial';
  ctx.fillText(`점수: ${score} | 레벨: ${level}`, 10, 30);
  
  // 게임 오버 메시지
  if (gameOver) {
    ctx.fillStyle = 'rgba(0, 0, 0, 0.7)';
    ctx.fillRect(0, 0, canvas.width, canvas.height);
    
    ctx.fillStyle = 'white';
    ctx.font = '40px Arial';
    ctx.textAlign = 'center';
    ctx.fillText('게임 오버!', canvas.width/2, canvas.height/2);
    
    ctx.font = '24px Arial';
    ctx.fillText(`최종 점수: ${score}`, canvas.width/2, canvas.height/2 + 50);
    
    ctx.font = '18px Arial';
    ctx.fillText('스페이스바를 눌러 다시 시작', canvas.width/2, canvas.height/2 + 90);
  }
}

// 게임 재시작
function restart() {
  player.x = canvas.width / 2 - 20;
  bullets.length = 0;
  enemies.length = 0;
  score = 0;
  gameOver = false;
  level = 1;
}

// 게임 루프
function gameLoop() {
  if (gameOver && keys[' ']) {
    restart();
  }
  
  update();
  draw();
  requestAnimationFrame(gameLoop);
}

// 게임 시작
gameLoop();
```

## 강의를 마치며

JavaScript와 ChatGPT를 활용한 개발 방법을 배우셨습니다. 이제 여러분은:
- 기본적인 JavaScript 코드를 작성할 수 있습니다
- ChatGPT를 활용하여 코딩 생산성을 높일 수 있습니다
- 간단한 게임을 개발할 수 있는 역량을 갖추게 되었습니다

앞으로도 계속 학습하고 발전하시길 바랍니다!
