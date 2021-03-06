---
title: 추가 시작 고려 사항
ms.date: 11/04/2016
helpviewer_keywords:
- program startup [C++]
- startup code
- initializing before main
ms.assetid: 0e942aa6-8342-447c-b068-8980ed7622bd
ms.openlocfilehash: 16e48f2e4f7544d28a1bea00e1fdf2d1cff397b5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50605580"
---
# <a name="additional-startup-considerations"></a>추가 시작 고려 사항

C++에서 개체 생성 및 소멸 시 실행할 사용자 코드를 포함할 수 있습니다. 어떤 초기화가 발생 하기 전에 알아야 할 것 이므로 `main` 종료 후 어떤 소멸자가 호출 `main`합니다. (개체의 생성과 소멸에 대 한 자세한 내용은 [생성자](../cpp/constructors-cpp.md) 하 고 [소멸자](../cpp/destructors-cpp.md).)

다음의 초기화에 들어가기 전에 수행 `main`:

- 기본 초기화는 정적 데이터를 0으로 설정합니다. 명시적 이니셜라이저가 없는 모든 정적 데이터는 런타임 이니셜라이저 및 다른 코드를 실행하기 전에 0으로 설정됩니다. 정적 데이터 멤버는 명시적으로 정의되어야 합니다.

- 변환 단위에서 전역 정적 개체를 초기화합니다. 진입 하기 전에 발생할 수 있습니다이 `main` 또는 함수나 개체의 변환 단위에서 개체를 처음 사용 하기 전에 합니다.

**Microsoft 전용**

Microsoft c + +, 진입 하기 전에 전역 정적 개체 초기화 `main`합니다.

**Microsoft 전용 종료**

전역 정적 개체는 상호 의존적이지만, 변환 단위가 다른 전역 정적 개체에서는 잘못된 동작이 발생할 수 있습니다.

## <a name="see-also"></a>참고자료

[시작 및 종료](../cpp/startup-and-termination-cpp.md)