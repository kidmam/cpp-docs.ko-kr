---
title: 컴파일러 오류 C2731
ms.date: 11/04/2016
f1_keywords:
- C2731
helpviewer_keywords:
- C2731
ms.assetid: 9b563999-febd-4582-9147-f355083c091e
ms.openlocfilehash: 2bb00f972f4c12a00255a9820a768d01691f9940
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50655036"
---
# <a name="compiler-error-c2731"></a>컴파일러 오류 C2731

'identifier': 함수를 오버 로드할 수 없습니다

함수 `main`, `WinMain`를 `DllMain`, 및 `LibMain` 오버 로드할 수 없습니다.

다음 샘플에서는 C2731 오류가 생성 됩니다.

```
// C2731.cpp
extern "C" void WinMain(int, char *, char *);
void WinMain(int, short, char *, char*);   // C2731
```