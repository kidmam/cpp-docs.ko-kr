---
title: 링커 도구 오류 LNK1256
ms.date: 11/04/2016
f1_keywords:
- xml
- LNK1256
helpviewer_keywords:
- LNK1256
ms.assetid: 55b64b2b-a56b-436c-a55e-ec9c6dcb050e
ms.openlocfilehash: 9d969d1e5bbae92ed49747f761c1b89d1910d4e1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492870"
---
# <a name="linker-tools-error-lnk1256"></a>링커 도구 오류 LNK1256

ALINK 작업이 실패했습니다: 이유

LNK1256이 발생하는 일반적인 이유는 어셈블리의 버전 번호가 잘못되었기 때문입니다. 어셈블리 버전 번호에는 65535 값을 포함할 수 없습니다. 어셈블리 버전에 대 한 유효한 범위는 0-65534입니다.

ALINK가 명명된 키 컨테이너를 찾을 수 없는 경우에도 LNK1256이 발생할 수 있습니다. 키 컨테이너를 삭제 하 고 다시 추가 강력한 이름 CSP 사용 하 여 [Sn.exe (강력한 이름 도구)](/dotnet/framework/tools/sn-exe-strong-name-tool)합니다.

링커와 Alink.dll 간에 버전이 일치하지 않는 경우에도 LNK1256이 발생할 수 있습니다. 설치된 Visual Studio가 손상되면 버전이 일치하지 않을 수 있습니다. 사용 하 여 **프로그램 및 기능** 을 복구 하거나 Visual Studio를 다시 설치 하려면 Windows 제어판에서.

다음 샘플에서는 LNK1256을 생성합니다.

```
// LNK1256.cpp
// compile with: /clr /LD
// LNK1256 expected
[assembly:System::Reflection::AssemblyVersionAttribute("1.0.65535")];
public class CMyClass {
public:
   int value;
};
```