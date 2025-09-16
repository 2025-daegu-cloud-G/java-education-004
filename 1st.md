## 좋은 포인트 짚으셨어요 👍
import java.net.*; 처럼 * 을 쓰는 것과 import java.net.URL; 처럼 특정 클래스를 지정하는 것의 차이가 있을까요? → 메모리/성능 측면에서는 차이가 없습니다.

## ✅ 왜 차이가 없을까?

import 구문은 컴파일러에게 클래스가 어디에 있는지 알려주는 “컴파일 시점 도우미” 역할만 합니다.

실제 실행 시점(Runtime)에는 JVM이 필요한 클래스만 로딩합니다.

즉, * 를 쓴다고 해서 해당 패키지 안의 모든 클래스가 메모리에 로드되는 건 ❌ 아닙니다.

예시:

import java.util.*;   // List, Map 등 필요할 때만 로딩됨
import java.util.List;

public class Test {
    public static void main(String[] args) {
        List<String> list = new ArrayList<>();
    }
}


➡ * 를 써도 실제로는 List, ArrayList 등 사용한 클래스만 로드됨.

✅ 차이가 있는 부분

가독성 / 유지보수성

* : 코드가 짧아지고 편하지만, 어떤 클래스가 실제로 쓰이는지 명확하지 않음.

특정 클래스 import : 명확하고 IDE에서 자동 정리 가능.

이름 충돌 가능성

서로 다른 패키지에 같은 이름의 클래스가 있을 때 혼동될 수 있음.

예: java.sql.Date vs java.util.Date

이런 경우는 무조건 풀네임(java.util.Date)으로 써야 함.

컴파일 속도

* 사용 시, 컴파일러가 해당 패키지에서 클래스 검색을 조금 더 해야 함.

하지만 현대 IDE/컴파일러에서는 거의 무시해도 될 수준.

✅ 결론

실행 시 성능, 메모리 차이는 전혀 없음.

차이가 나는 건 코드 가독성과 유지보수성.

그래서 실무에서는 명시적 import (import java.net.URL;)을 권장하고,
IDE(Eclipse, IntelliJ 등)에서도 자동으로 “사용하는 클래스만 import”하도록 정리 기능이 있습니다.

👉 정리하면:

import java.net.*; = 편하지만 모호함

import java.net.URL; = 명확하고 실무 권장

JVM 리소스 측면에서는 차이 없음 ✅