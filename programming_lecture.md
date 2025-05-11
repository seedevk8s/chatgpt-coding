# 프로그래밍 실전경험: 기본코드 작성 실습
## Chat GPT를 활용한 코딩방법소개 및 실전소개

### 목차
1. **소개 (15분)**
   - 특강 소개 및 목표
   - AI 도구의 발전과 코딩에서의 활용

2. **Chat GPT 소개 및 활용법 (25분)**
   - Chat GPT란 무엇인가?
   - 프로그래밍에서 Chat GPT의 장단점
   - 효과적인 프롬프트 작성법
   - 코드 디버깅 및 최적화

3. **실습 1: 기본 코드 작성하기 (30분)**
   - Python 기초 코드 작성
   - 간단한 데이터 분석 프로그램
   - Chat GPT를 활용한 코드 개선

4. **실습 2: 웹 애플리케이션 개발 (30분)**
   - HTML/CSS/JavaScript 기초
   - 간단한 Todo 리스트 웹앱 만들기
   - Chat GPT를 활용한 기능 추가

5. **실습 3: API 연동 및 데이터 시각화 (30분)**
   - REST API 개념 및 활용
   - 공공 데이터 API 연동하기
   - 데이터 시각화 코드 작성

6. **마무리 및 Q&A (20분)**
   - 배운 내용 정리
   - 추가 학습 자료 및 리소스 소개
   - 질의응답

---

## 1. 소개

### 특강 소개 및 목표
- 프로그래밍 기초 지식을 실전에 적용하는 방법 학습
- Chat GPT와 같은 AI 도구를 활용한 효율적인 코딩 방법 습득
- 실습을 통한 실전 경험 획득

### AI 도구의 발전과 코딩에서의 활용
- AI 코딩 도구의 발전 역사
- 현업에서의 AI 도구 활용 사례
- AI 도구의 미래와 개발자의 역할 변화

---

## 2. Chat GPT 소개 및 활용법

### Chat GPT란 무엇인가?
- GPT(Generative Pre-trained Transformer) 모델 개요
- Chat GPT의 작동 원리 및 학습 방식
- 다른 AI 코딩 도구와의 비교 (GitHub Copilot, Amazon CodeWhisperer 등)

### 프로그래밍에서 Chat GPT의 장단점

**장점:**
- 빠른 코드 생성 및 문제 해결
- 다양한 언어 및 프레임워크 지원
- 코드 설명 및 문서화 지원
- 초보자를 위한 학습 도구

**단점:**
- 최신 라이브러리나 프레임워크에 대한 제한된 지식
- 복잡한 시스템 설계의 한계
- 잘못된 정보나 비효율적인 코드 생성 가능성
- 보안 및 데이터 프라이버시 문제

### 효과적인 프롬프트 작성법

**좋은 프롬프트의 특징:**
- 명확하고 구체적인 요구사항 제시
- 원하는 코드의 기능, 입력, 출력 명시
- 사용하려는 언어, 라이브러리, 프레임워크 명시
- 코드 스타일이나 최적화 요구사항 제시

**프롬프트 예시:**
```
Python으로 다음 기능을 하는 함수를 작성해 주세요:
- 기능: 주어진 텍스트 파일에서 가장 자주 등장하는 단어 5개를 찾는 함수
- 입력: 텍스트 파일 경로(문자열)
- 출력: (단어, 빈도수) 튜플의 리스트, 빈도수 기준 내림차순 정렬
- 요구사항: 
  - 대소문자를 구분하지 않고 처리
  - 구두점과 특수문자는 제거
  - 길이가 3 이상인 단어만 대상으로 함
  - 효율적인 데이터 구조 사용
- 사용 라이브러리: collections, re만 사용
```

### 코드 디버깅 및 최적화
- 오류 메시지와 함께 코드를 제공하여 디버깅 요청
- 성능 최적화를 위한 코드 리뷰 요청
- 코드 리팩토링 및 가독성 향상 요청

---

## 3. 실습 1: 기본 코드 작성하기

### Python 기초 코드 작성
이 실습에서는 Python을 사용하여 텍스트 파일에서 단어 빈도를 분석하는 프로그램을 작성합니다.

**목표:**
- 파일 입출력 이해
- 데이터 처리 및 분석 기초 학습
- Chat GPT를 활용한 코드 작성 및 개선

**기본 기능:**
1. 텍스트 파일 읽기
2. 단어 빈도 계산
3. 결과 저장 및 출력

### 단계별 실습:

1. **텍스트 파일 읽기 함수 작성**
```python
def read_file(file_path):
    """
    텍스트 파일을 읽어 문자열로 반환합니다.
    
    Args:
        file_path (str): 읽을 파일의 경로
        
    Returns:
        str: 파일의 내용
    """
    try:
        with open(file_path, 'r', encoding='utf-8') as file:
            return file.read()
    except FileNotFoundError:
        print(f"Error: 파일 '{file_path}'을 찾을 수 없습니다.")
        return ""
    except Exception as e:
        print(f"Error: 파일을 읽는 중 오류가 발생했습니다. {e}")
        return ""
```

2. **단어 빈도 계산 함수 작성**
```python
import re
from collections import Counter

def count_words(text):
    """
    텍스트에서 단어 빈도를 계산합니다.
    
    Args:
        text (str): 분석할 텍스트
        
    Returns:
        list: (단어, 빈도수) 튜플의 리스트, 빈도수 기준 내림차순 정렬
    """
    # 텍스트를 소문자로 변환
    text = text.lower()
    
    # 영문자, 숫자, 한글만 남기고 나머지는 공백으로 대체
    text = re.sub(r'[^\w\s가-힣]', ' ', text)
    
    # 단어 분리
    words = text.split()
    
    # 길이가 3 이상인 단어만 선택
    filtered_words = [word for word in words if len(word) >= 3]
    
    # 단어 빈도 계산
    word_counts = Counter(filtered_words)
    
    # 빈도수 기준 내림차순 정렬
    return word_counts.most_common()
```

3. **결과 저장 및 출력 함수 작성**
```python
def save_results(results, output_file):
    """
    단어 빈도 분석 결과를 파일에 저장합니다.
    
    Args:
        results (list): (단어, 빈도수) 튜플의 리스트
        output_file (str): 저장할 파일 경로
    """
    try:
        with open(output_file, 'w', encoding='utf-8') as file:
            for word, count in results:
                file.write(f"{word}: {count}\n")
        print(f"결과가 '{output_file}'에 저장되었습니다.")
    except Exception as e:
        print(f"Error: 결과를 저장하는 중 오류가 발생했습니다. {e}")

def print_top_words(results, n=5):
    """
    가장 빈도가 높은 n개의 단어를 출력합니다.
    
    Args:
        results (list): (단어, 빈도수) 튜플의 리스트
        n (int): 출력할 단어 수
    """
    print(f"\n가장 많이 등장한 {n}개 단어:")
    for i, (word, count) in enumerate(results[:n], 1):
        print(f"{i}. {word}: {count}회")
```

4. **메인 함수 작성**
```python
def main():
    input_file = input("분석할 텍스트 파일 경로를 입력하세요: ")
    output_file = input("결과를 저장할 파일 경로를 입력하세요: ")
    
    # 파일 읽기
    text = read_file(input_file)
    if not text:
        return
    
    # 단어 빈도 계산
    word_counts = count_words(text)
    
    # 결과 저장
    save_results(word_counts, output_file)
    
    # 상위 단어 출력
    print_top_words(word_counts)

if __name__ == "__main__":
    main()
```

### Chat GPT를 활용한 코드 개선
코드를 작성한 후, Chat GPT에게 다음과 같은 개선 사항을 요청해 봅시다:

1. **성능 최적화 요청 예시**
   ```
   위 코드에서 대용량 파일을 처리할 때 메모리 사용량을 줄일 수 있는 방법이 있을까요?
   ```

2. **기능 추가 요청 예시**
   ```
   특정 단어 목록(예: 불용어)을 제외하고 단어 빈도를 계산하는 기능을 추가해 주세요.
   ```

3. **에러 처리 개선 요청 예시**
   ```
   다양한 인코딩의 파일을 처리할 수 있도록 코드를 개선해 주세요.
   ```

---

## 4. 실습 2: 웹 애플리케이션 개발

### HTML/CSS/JavaScript 기초
이 실습에서는 기본적인 웹 기술을 사용하여 간단한 Todo 리스트 웹 애플리케이션을 개발합니다.

**목표:**
- 웹 개발 기초 이해
- HTML, CSS, JavaScript 활용
- Chat GPT를 통한 웹 개발 지원 받기

### 단계별 실습:

1. **HTML 구조 작성**
```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>할 일 관리 앱</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="container">
        <h1>할 일 관리 앱</h1>
        
        <div class="input-container">
            <input type="text" id="taskInput" placeholder="할 일을 입력하세요...">
            <button id="addBtn">추가</button>
        </div>
        
        <div class="task-filters">
            <button class="filter-btn active" data-filter="all">전체</button>
            <button class="filter-btn" data-filter="active">진행 중</button>
            <button class="filter-btn" data-filter="completed">완료</button>
        </div>
        
        <ul id="taskList"></ul>
        
        <div class="task-stats">
            <span id="taskCount">0 항목 남음</span>
            <button id="clearCompleted">완료 항목 삭제</button>
        </div>
    </div>
    
    <script src="script.js"></script>
</body>
</html>
```

2. **CSS 스타일 작성**
```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Arial', sans-serif;
}

body {
    background-color: #f5f5f5;
    color: #333;
    display: flex;
    justify-content: center;
    padding: 50px 20px;
}

.container {
    width: 100%;
    max-width: 500px;
    background-color: white;
    border-radius: 8px;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
    padding: 20px;
}

h1 {
    text-align: center;
    margin-bottom: 20px;
    color: #2c3e50;
}

.input-container {
    display: flex;
    margin-bottom: 20px;
}

#taskInput {
    flex: 1;
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 4px 0 0 4px;
    font-size: 16px;
}

#addBtn {
    padding: 10px 15px;
    background-color: #3498db;
    color: white;
    border: none;
    border-radius: 0 4px 4px 0;
    cursor: pointer;
    font-size: 16px;
}

#addBtn:hover {
    background-color: #2980b9;
}

.task-filters {
    display: flex;
    margin-bottom: 15px;
    justify-content: center;
}

.filter-btn {
    padding: 8px 12px;
    margin: 0 5px;
    background-color: white;
    border: 1px solid #ddd;
    border-radius: 4px;
    cursor: pointer;
}

.filter-btn.active {
    background-color: #3498db;
    color: white;
    border-color: #3498db;
}

#taskList {
    list-style-type: none;
    margin-bottom: 20px;
}

.task-item {
    padding: 10px;
    border-bottom: 1px solid #eee;
    display: flex;
    align-items: center;
}

.task-checkbox {
    margin-right: 10px;
}

.task-text {
    flex: 1;
}

.completed {
    text-decoration: line-through;
    color: #888;
}

.delete-btn {
    color: #e74c3c;
    background: none;
    border: none;
    cursor: pointer;
    font-size: 18px;
}

.task-stats {
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-size: 14px;
    color: #777;
}

#clearCompleted {
    background: none;
    border: none;
    color: #3498db;
    cursor: pointer;
}

#clearCompleted:hover {
    text-decoration: underline;
}
```

3. **JavaScript 기능 구현**
```javascript
// DOM 요소 선택
const taskInput = document.getElementById('taskInput');
const addBtn = document.getElementById('addBtn');
const taskList = document.getElementById('taskList');
const taskCount = document.getElementById('taskCount');
const clearCompletedBtn = document.getElementById('clearCompleted');
const filterBtns = document.querySelectorAll('.filter-btn');

// 할 일 데이터 배열
let tasks = JSON.parse(localStorage.getItem('tasks')) || [];
let currentFilter = 'all';

// 앱 초기화
function init() {
    renderTasks();
    updateTaskCount();
    
    // 이벤트 리스너 등록
    addBtn.addEventListener('click', addTask);
    taskInput.addEventListener('keypress', (e) => {
        if (e.key === 'Enter') addTask();
    });
    clearCompletedBtn.addEventListener('click', clearCompleted);
    
    // 필터 버튼 이벤트 리스너
    filterBtns.forEach(btn => {
        btn.addEventListener('click', () => {
            filterBtns.forEach(b => b.classList.remove('active'));
            btn.classList.add('active');
            currentFilter = btn.getAttribute('data-filter');
            renderTasks();
        });
    });
}

// 할 일 추가 함수
function addTask() {
    const taskText = taskInput.value.trim();
    
    if (taskText === '') return;
    
    const newTask = {
        id: Date.now(),
        text: taskText,
        completed: false
    };
    
    tasks.push(newTask);
    saveTasks();
    renderTasks();
    updateTaskCount();
    
    taskInput.value = '';
    taskInput.focus();
}

// 할 일 삭제 함수
function deleteTask(id) {
    tasks = tasks.filter(task => task.id !== id);
    saveTasks();
    renderTasks();
    updateTaskCount();
}

// 할 일 상태 토글 함수
function toggleTask(id) {
    tasks = tasks.map(task => {
        if (task.id === id) {
            return { ...task, completed: !task.completed };
        }
        return task;
    });
    
    saveTasks();
    renderTasks();
    updateTaskCount();
}

// 완료된 할 일 모두 삭제
function clearCompleted() {
    tasks = tasks.filter(task => !task.completed);
    saveTasks();
    renderTasks();
    updateTaskCount();
}

// 할 일 로컬 스토리지에 저장
function saveTasks() {
    localStorage.setItem('tasks', JSON.stringify(tasks));
}

// 할 일 렌더링 함수
function renderTasks() {
    taskList.innerHTML = '';
    
    let filteredTasks = tasks;
    
    if (currentFilter === 'active') {
        filteredTasks = tasks.filter(task => !task.completed);
    } else if (currentFilter === 'completed') {
        filteredTasks = tasks.filter(task => task.completed);
    }
    
    filteredTasks.forEach(task => {
        const taskItem = document.createElement('li');
        taskItem.className = 'task-item';
        
        const checkbox = document.createElement('input');
        checkbox.type = 'checkbox';
        checkbox.className = 'task-checkbox';
        checkbox.checked = task.completed;
        checkbox.addEventListener('change', () => toggleTask(task.id));
        
        const taskText = document.createElement('span');
        taskText.className = `task-text ${task.completed ? 'completed' : ''}`;
        taskText.textContent = task.text;
        
        const deleteBtn = document.createElement('button');
        deleteBtn.className = 'delete-btn';
        deleteBtn.innerHTML = '&times;';
        deleteBtn.addEventListener('click', () => deleteTask(task.id));
        
        taskItem.appendChild(checkbox);
        taskItem.appendChild(taskText);
        taskItem.appendChild(deleteBtn);
        
        taskList.appendChild(taskItem);
    });
}

// 남은 할 일 수 업데이트
function updateTaskCount() {
    const remainingTasks = tasks.filter(task => !task.completed).length;
    taskCount.textContent = `${remainingTasks} 항목 남음`;
}

// 앱 초기화
init();
```

### Chat GPT를 활용한 기능 추가
이제 Chat GPT를 활용하여 추가 기능을 구현해 봅시다:

1. **드래그 앤 드롭으로 할 일 순서 변경 기능 추가**
   ```
   할 일 목록에서 항목을 드래그 앤 드롭으로 순서를 변경할 수 있는 기능을 추가해 주세요.
   ```

2. **날짜 및 시간 추가 기능**
   ```
   각 할 일에 마감일을 설정할 수 있는 기능을 추가해 주세요.
   ```

3. **카테고리 기능 추가**
   ```
   할 일에 카테고리(예: 업무, 개인, 학습 등)를 추가하고 필터링할 수 있는 기능을 추가해 주세요.
   ```

---

## 5. 실습 3: API 연동 및 데이터 시각화

### REST API 개념 및 활용
이 실습에서는 공공 데이터 API를 연동하고 가져온 데이터를 시각화하는 웹 애플리케이션을 개발합니다.

**목표:**
- REST API 개념 이해 및 활용
- 공공 데이터 API 연동
- 데이터 시각화 라이브러리 사용
- Chat GPT를 통한 API 연동 및 시각화 코드 작성

### 단계별 실습:

1. **HTML 구조 작성**
```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>대한민국 코로나19 현황</title>
    <link rel="stylesheet" href="style.css">
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
</head>
<body>
    <div class="container">
        <h1>대한민국 코로나19 현황</h1>
        
        <div class="date-selector">
            <label for="startDate">시작일:</label>
            <input type="date" id="startDate">
            <label for="endDate">종료일:</label>
            <input type="date" id="endDate">
            <button id="searchBtn">검색</button>
        </div>
        
        <div class="loading" id="loading">데이터 로딩 중...</div>
        
        <div class="dashboard">
            <div class="chart-container">
                <h2>일별 확진자 추이</h2>
                <canvas id="casesChart"></canvas>
            </div>
            
            <div class="stats-container">
                <h2>통계 요약</h2>
                <div id="statsContent"></div>
            </div>
        </div>
    </div>
    
    <script src="script.js"></script>
</body>
</html>
```

2. **CSS 스타일 작성**
```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Arial', sans-serif;
}

body {
    background-color: #f0f2f5;
    color: #333;
    padding: 20px;
}

.container {
    max-width: 1200px;
    margin: 0 auto;
    background-color: white;
    border-radius: 10px;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
    padding: 20px;
}

h1 {
    text-align: center;
    margin-bottom: 20px;
    color: #2c3e50;
}

.date-selector {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 10px;
    margin-bottom: 20px;
    flex-wrap: wrap;
}

.date-selector input {
    padding: 8px;
    border: 1px solid #ddd;
    border-radius: 4px;
}

#searchBtn {
    padding: 8px 15px;
    background-color: #3498db;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
}

#searchBtn:hover {
    background-color: #2980b9;
}

.loading {
    text-align: center;
    margin: 20px 0;
    font-style: italic;
    color: #777;
    display: none;
}

.dashboard {
    display: grid;
    grid-template-columns: 2fr 1fr;
    gap: 20px;
}

@media (max-width: 768px) {
    .dashboard {
        grid-template-columns: 1fr;
    }
}

.chart-container, .stats-container {
    background-color: white;
    border-radius: 8px;
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
    padding: 15px;
}

h2 {
    margin-bottom: 15px;
    color: #34495e;
    font-size: 18px;
}

.stat-card {
    background-color: #f8f9fa;
    border-radius: 6px;
    padding: 15px;
    margin-bottom: 10px;
}

.stat-title {
    color: #7f8c8d;
    font-size: 14px;
    margin-bottom: 5px;
}

.stat-value {
    font-size: 24px;
    font-weight: bold;
    color: #2c3e50;
}

.stat-card.confirmed .stat-value {
    color: #e74c3c;
}

.stat-card.recovered .stat-value {
    color: #2ecc71;
}

.stat-card.deaths .stat-value {
    color: #95a5a6;
}
```

3. **JavaScript API 연동 및 시각화 구현**
```javascript
// DOM 요소 선택
const startDateInput = document.getElementById('startDate');
const endDateInput = document.getElementById('endDate');
const searchBtn = document.getElementById('searchBtn');
const loadingIndicator = document.getElementById('loading');
const statsContent = document.getElementById('statsContent');
let casesChart = null;

// 날짜 기본값 설정 (1개월)
function setDefaultDates() {
    const today = new Date();
    const oneMonthAgo = new Date();
    oneMonthAgo.setMonth(today.getMonth() - 1);
    
    endDateInput.value = formatDate(today);
    startDateInput.value = formatDate(oneMonthAgo);
}

// 날짜 형식 변환 (YYYY-MM-DD)
function formatDate(date) {
    const year = date.getFullYear();
    const month = String(date.getMonth() + 1).padStart(2, '0');
    const day = String(date.getDate()).padStart(2, '0');
    return `${year}-${month}-${day}`;
}

// API에서 코로나 데이터 가져오기
async function fetchCovidData(startDate, endDate) {
    // 실제 API 호출을 대체한 샘플 데이터 생성
    // 실제 구현에서는 fetch()를 사용하여 실제 API에서 데이터를 가져와야 함
    return generateSampleData(startDate, endDate);
}

// 샘플 데이터 생성 (실제 API 연동 시 이 부분을 교체)
function generateSampleData(startDate, endDate) {
    const start = new Date(startDate);
    const end = new Date(endDate);
    const days = Math.ceil((end - start) / (1000 * 60 * 60 * 24)) + 1;
    
    const data = [];
    let prevConfirmed = Math.floor(Math.random() * 1000) + 500;
    
    for (let i = 0; i < days; i++) {
        const date = new Date(start);
        date.setDate(start.getDate() + i);
        
        // 새 확진자 수 (이전 날짜