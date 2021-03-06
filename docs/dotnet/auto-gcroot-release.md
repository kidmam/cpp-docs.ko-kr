---
title: auto_gcroot::release
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- msclr::auto_gcroot::release
- auto_gcroot::release
- auto_gcroot.release
- msclr.auto_gcroot.release
helpviewer_keywords:
- release method
ms.assetid: 40b253f0-154e-4d79-80a4-ff13199c3ff0
ms.openlocfilehash: f895595f3f3a4ef3dcfba82e4f48a30bc11b6310
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50437988"
---
# <a name="autogcrootrelease"></a>auto_gcroot::release

개체를 해제 `auto_gcroot` 관리 합니다.

## <a name="syntax"></a>구문

```
_element_type release();
```

## <a name="return-value"></a>반환 값

출시 된 개체입니다.

## <a name="example"></a>예제

```
// msl_auto_gcroot_release.cpp
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
   ClassA^ a;

   // create a new scope:
   {
      auto_gcroot<ClassA^> agc1 = gcnew ClassA( "first" );
      auto_gcroot<ClassA^> agc2 = gcnew ClassA( "second" );
      a = agc1.release();
   }
   // agc1 and agc2 go out of scope here

   a->PrintHello();

   Console::WriteLine( "done" );
}
```

```Output
ClassA constructor: first
ClassA constructor: second
ClassA destructor: second
Hello from first A!
done
```

## <a name="requirements"></a>요구 사항

**헤더 파일** \<msclr\auto_gcroot.h >

**Namespace** msclr

## <a name="see-also"></a>참고 항목

[auto_gcroot 멤버](../dotnet/auto-gcroot-members.md)<br/>
[auto_gcroot::~auto_gcroot](../dotnet/auto-gcroot-tilde-auto-gcroot.md)