---
title: 컴파일러 오류 C3084
ms.date: 11/04/2016
f1_keywords:
- C3084
helpviewer_keywords:
- C3084
ms.assetid: 0362cb70-e24e-476f-a24d-8f5bb97c3afd
ms.openlocfilehash: 7659c17d999a8720ffb0ccdcdb631b27949167b7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50572681"
---
# <a name="compiler-error-c3084"></a>컴파일러 오류 C3084

'function': 종료자/소멸자는 'keyword'가 될 수 없습니다.

종료자 또는 소멸자를 잘못 선언했습니다.

예를 들어 소멸자를 sealed로 표시하면 안 됩니다.  파생 형식이 소멸자에 액세스할 수 없습니다.  자세한 내용은 [명시적으로 재정의](../../windows/explicit-overrides-cpp-component-extensions.md) 하 고 [하는 방법의 소멸자 및 종료자: 클래스 및 구조체 정의 및 사용 (C + + CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).

## <a name="example"></a>예제

다음 샘플에서는 C3084를 생성합니다.

```
// C3084.cpp
// compile with: /clr /c
ref struct R {
protected:
   !R() sealed;   // C3084
   !R() abstract;   // C3084
   !R();
};
```