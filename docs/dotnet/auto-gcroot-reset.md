---
title: auto_gcroot::reset
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- msclr::auto_gcroot::reset
- auto_gcroot::reset
- msclr.auto_gcroot.reset
- auto_gcroot.reset
helpviewer_keywords:
- reset method
ms.assetid: dd58467f-3885-4a15-99fb-ed6dd5d19622
ms.openlocfilehash: d7d8f13a515227aa38fb6d4ba238e54d268697e2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50570705"
---
# <a name="autogcrootreset"></a>auto_gcroot::reset

현재 소유한 개체를 제거 하 고 필요에 따라 새 개체의 소유를 수행 합니다.

## <a name="syntax"></a>구문

```
void reset(
   _element_type _new_ptr = nullptr
);
```

#### <a name="parameters"></a>매개 변수

*_new_ptr*<br/>
(선택 사항) 새 개체입니다.

## <a name="example"></a>예제

```
// msl_auto_gcroot_reset.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

using namespace System;
using namespace msclr;

ref class ClassA {
   String^ m_s;
public:
   ClassA( String^ s ) : m_s( s ) {
      Console::WriteLine( "ClassA constructor: " + m_s );
   }
   ~ClassA() {
      Console::WriteLine( "ClassA destructor: " + m_s );
   }

   void PrintHello() {
      Console::WriteLine( "Hello from {0} A!", m_s );
   }
};

int main()
{
   auto_gcroot<ClassA^> agc1 = gcnew ClassA( "first" );
   agc1->PrintHello();

   ClassA^ ha = gcnew ClassA( "second" );
   agc1.reset( ha ); // release first object, reference second
   agc1->PrintHello();

   agc1.reset(); // release second object, set to nullptr

   Console::WriteLine( "done" );
}
```

```Output
ClassA constructor: first
Hello from first A!
ClassA constructor: second
ClassA destructor: first
Hello from second A!
ClassA destructor: second
done
```

## <a name="requirements"></a>요구 사항

**헤더 파일** \<msclr\auto_gcroot.h >

**Namespace** msclr

## <a name="see-also"></a>참고 항목

[auto_gcroot 멤버](../dotnet/auto-gcroot-members.md)<br/>
[auto_gcroot::release](../dotnet/auto-gcroot-release.md)<br/>
[auto_gcroot::attach](../dotnet/auto-gcroot-attach.md)