# Java 점심 메뉴 룰렛 프로그램 - 전체 동작 과정 및 설명

## 1. 프로그램 목적
- 점심 메뉴를 빠르고 재미있게 정하기 위해 만들어진 콘솔 기반 Java 프로그램입니다.
- 사용자는 두 지역(정문/청주대 사거리) 중 하나를 선택하고, 해당 지역에서 제공하는 다양한 음식 종류와 식당 중에서 룰렛 방식으로 메뉴와 식당을 무작위로 결정합니다.

## 2. 주요 파일
- `src/Main.java`: 프로그램의 진입점 및 모든 핵심 로직이 구현되어 있는 파일
- `README.md`: 전체 프로그램 설명, 사용 방법, 흐름 등이 기술된 문서

## 3. 전체 동작 과정 및 실행 순서

### (1) 지역 선택
- 프로그램이 시작되면 "정문" 또는 "청주대 사거리" 중 어디에서 식사할지 입력하라는 메시지가 출력됩니다.
- 사용자가 입력한 값이 올바른 경우, 해당 지역에 대한 음식 종류와 식당 목록을 변수에 저장합니다.
- 잘못 입력하면 계속해서 올바른 입력을 요구합니다.

### (2) 음식 종류 룰렛
- 선택된 지역에 따라 미리 정의된 음식 종류 리스트(frontCategories/backCategories) 중 하나가 무작위(Random)로 선택됩니다.
- 예시: "정문"의 경우 ["한국음식", "베트남음식", "프랑스 음식", "일본 음식", "필리핀 음식"] 중 하나가 선택됩니다.
- 선택된 음식 종류가 화면에 출력됩니다.

### (3) 식당 룰렛
- 선택된 음식 종류에 해당하는 식당 목록(2차원 리스트)에서 다시 한 번 무작위로 식당을 추첨합니다.
- 예시: "한국음식"이 선택되면 ["비빔밥", "갈비찜", "떡볶이", "삼계탕"] 중 한 곳이 무작위로 선택됩니다.
- 선택된 식당을 화면에 출력합니다.

### (4) 최종 결과 안내
- 최종적으로 "지역", "음식 종류", "식당 이름"이 모두 결정되어 사용자에게 안내 메시지로 출력됩니다.
- 예시 메시지:
  - 🎯 정문 선택됨!
  - 선택된 음식 종류는 한국음식입니다!🎯
  - 오늘의 점심은 비빔밥에서 어떤가요?😉

### (5) 반복 입력 처리
- 사용자가 지역명을 잘못 입력하면, 올바른 입력을 할 때까지 반복해서 입력을 요구합니다.

### (6) 전체 코드 흐름 예시 (의사코드)
```java
while (true) {
    // 지역 입력 및 검증
    // front/back 변수 할당
}
System.out.println("룰렛을 돌리는 중...");
Thread.sleep(300);
System.out.println("지역 선택됨!");
Thread.sleep(1000);
// 음식 종류 무작위 선택 및 출력
// 음식 종류에 따른 식당 무작위 선택 및 출력
scanner.close();
```

### (7) 사용자 입장에서 본 흐름
1. 프로그램 실행
2. "정문" 또는 "청주대 사거리" 입력 (입력 오류 시 재입력)
3. "룰렛을 돌리는 중..." 애니메이션 출력
4. 랜덤으로 음식 종류 선정 메시지
5. 랜덤으로 식당 선정 메시지
6. 결과 안내 후 종료

## 4. 프로그램의 효과
- 매일 점심 메뉴 고민을 줄여주고, 새로운 음식과 식당을 경험할 수 있게 해줍니다.
- 여러 명이 함께 돌릴 때 재미와 소통의 요소도 제공합니다.

---

## 5. 참고 코드 (src/Main.java 주요 부분 발췌)
```java
Scanner scanner = new Scanner(System.in);
Random random = new Random();

List<String> frontCategories = Arrays.asList("한국음식", "베트남음식", ...);
List<List<String>> frontStores = Arrays.asList(
    Arrays.asList("비빔밥", "갈비찜", ...), ...
);
// backCategories, backStores도 동일하게 선언

while (true) {
    System.out.print("정문 또는 청주 사거리을 선택하세요: ");
    String input = scanner.nextLine().trim();

    if (input.equalsIgnoreCase("정문")) {
        // frontCategories/frontStores 할당
        break;
    } else if (input.equalsIgnoreCase("청주대 사거리")) {
        // backCategories/backStores 할당
        break;
    } else {
        System.out.println("⚠️ 잘못 입력하셨습니다. '정문' 또는 '청주대 사거리'으로 다시 입력해주세요.");
    }
}

System.out.println("룰렛을 돌리는 중...⏱️");
Thread.sleep(300);
System.out.println("지역 선택됨!");

Thread.sleep(1000);
System.out.println("음식 종류를 무작위로 선택합니다...");
Thread.sleep(1000);

int categoryIndex = random.nextInt(selectedCategories.size());
String selectedCategory = selectedCategories.get(categoryIndex);
System.out.println("선택된 음식 종류는 " + selectedCategory + "입니다!");

Thread.sleep(1000);
System.out.println("해당 음식 종류의 가게 중 하나를 선택합니다...");
Thread.sleep(1000);

List<String> storeList = selectedStores.get(categoryIndex);
String selectedStore = storeList.get(random.nextInt(storeList.size()));
System.out.println("오늘의 점심은 " + selectedStore + "에서 어떤가요?😉");

scanner.close();
```
