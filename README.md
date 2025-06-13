import java.util.*;

public class Main {
    public static void main(String[] args) throws InterruptedException {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();

        List<String> frontCategories = Arrays.asList("한국음식", "베트남음식", "프랑스 음식", "일본 음식", "필리핀 음식");
        List<List<String>> frontStores = Arrays.asList(
                Arrays.asList("비빔밥", "갈비찜", "떡볶이", "삼계탕"),
                Arrays.asList("닭구이", "쌀국수", "반미", "반쎄오", "껌땀", "보네"),
                Arrays.asList("마카롱", "마들렌", "밀푀유", "브리또", "바게트", "브리오슈", "오믈렛"),
                Arrays.asList("초밥", "라면", "소바"),
                Arrays.asList("아보도", "시시그"));

        List<String> backCategories = Arrays.asList("한식", "프랑스 양식", "중식", "일식", "필리핀 음식");
        List<List<String>> backStores = Arrays.asList(
                Arrays.asList("닭갈비", "김밥", "불고기", "송편", "된장찌개", "냉면", "화채", "제육볶음", "오징어볶음", "육전"),
                Arrays.asList("봉골레", "투움바", "까르보나라", "알프레도", "아라비아따"),
                Arrays.asList("마라탕", "짜장면"),
                Arrays.asList("텐동", "가라아게", "타코야키"),
                Arrays.asList("불랄로", "레촌"));

        String selectedGate;
        List<String> selectedCategories = null;
        List<List<String>> selectedStores = null;

        while (true) {
            System.out.println("==== 식사 메뉴 룰렛 ====");
            System.out.print("정문 또는 청주 사거리을 선택하세요: ");
            String input = scanner.nextLine().trim();

            if (input.equalsIgnoreCase("정문")) {
                selectedGate = "정문";
                selectedCategories = frontCategories;
                selectedStores = frontStores;
                break;
            } else if (input.equalsIgnoreCase("청주대 사거리")) {
                selectedGate = "청주대사거리";
                selectedCategories = backCategories;
                selectedStores = backStores;
                break;
            } else {
                System.out.println("⚠️ 잘못 입력하셨습니다. '정문' 또는 '청주대 사거리'으로 다시 입력해주세요.\n");
            }
        }

        System.out.println("룰렛을 돌리는 중...⏱\uFE0F");
        Thread.sleep(300);
        System.out.println("🎯 " + selectedGate + " 선택됨!");

        Thread.sleep(1000);
        System.out.println("음식 종류를 무작위로 선택합니다...\uD83C\uDF72");
        Thread.sleep(1000);

        int categoryIndex = random.nextInt(selectedCategories.size());
        String selectedCategory = selectedCategories.get(categoryIndex);
        System.out.println("선택된 음식 종류는 " + selectedCategory + "입니다!🎯");

        Thread.sleep(1000);
        System.out.println("해당 음식 종류의 가게 중 하나를 선택합니다...⏱\uFE0F");
        Thread.sleep(1000);

        List<String> storeList = selectedStores.get(categoryIndex);
        String selectedStore = storeList.get(random.nextInt(storeList.size()));
        System.out.println("오늘의 점심은 " + selectedStore + "에서 어떤가요?\uD83D\uDE09");

        scanner.close();
    }
}
