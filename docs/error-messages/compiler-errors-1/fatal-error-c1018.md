---
title: 심각한 오류 C1018
ms.date: 11/04/2016
f1_keywords:
- C1018
helpviewer_keywords:
- C1018
ms.assetid: 2ceb8a99-30b2-4b80-bf42-e9f3305b3c52
ms.openlocfilehash: 327bc0d5200fc348611da107257f2086063648fa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532662"
---
# <a name="fatal-error-c1018"></a>심각한 오류 C1018

예기치 않은 #elif입니다.

`#elif` 지시문이 `#if`, `#ifdef`또는 `#ifndef` 구문 외부에 표시됩니다. `#elif` 는 이러한 구문 중 하나 내에서만 사용합니다.

다음 샘플에서는 C1018을 생성합니다.

```
// C1018.cpp
#elif      // C1018
#endif

int main() {}
```

해결 방법:

```
// C1018b.cpp
#if 1
#elif
#endif

int main() {}
```