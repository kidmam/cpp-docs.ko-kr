---
title: 컴파일러 오류 C2688
ms.date: 11/04/2016
f1_keywords:
- C2688
helpviewer_keywords:
- C2688
ms.assetid: 168c9e9d-8f65-4664-af86-db71d3e6ee46
ms.openlocfilehash: 5355abc603726eb1bacb7a22fa1095bf2d81c538
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50588554"
---
# <a name="compiler-error-c2688"></a>컴파일러 오류 C2688

'C2:: fgrv': 여러 개의 공변 (covariant) 반환 또는 가상 상속 varargs 함수에 대해 지원 되지 않습니다

공변 (covariant) 반환 형식은 함수에 변수 인수가 포함 된 경우 Visual c + +에서 지원 되지 않습니다.

이 오류를 해결 하려면 함수 정의 하거나 변수 인수를 사용 하지 않거나 반환 값은 모든 가상 함수에 대해 동일 하 게 이러한 되도록 합니다.

다음 샘플에서는 C2688 오류가 생성 됩니다.

```
// C2688.cpp
struct G1 {};
struct G2 {};
struct G3 : G1, G2 {};
struct G4 {};
struct G5 {};
struct G6 : G4, G5 {};
struct G7 : G3, G6 {};

struct C1 {
   virtual G4& fgrv(int,...);
};

struct C2 : C1 {
   virtual G7& fgrv(int,...);   // C2688, does not return G4&
};
```