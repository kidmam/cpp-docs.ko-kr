---
title: auto_handle::operator=
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- auto_handle::operator=
- msclr.auto_handle.operator=
- msclr::auto_handle::operator=
- auto_handle.operator=
helpviewer_keywords:
- auto_handle::operator=
ms.assetid: 503ca172-e766-4a78-af98-36fd48c931ee
ms.openlocfilehash: 2b65ea2ba5fcdb69a87127abe159dba8fbad64a9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50543717"
---
# <a name="autohandleoperator"></a>auto_handle::operator=

대입 연산자입니다.

## <a name="syntax"></a>구문

```
auto_handle<_element_type> % operator=(
   auto_handle<_element_type> % _right
);
template<typename _other_type>
auto_handle<_element_type> % operator=(
   auto_handle<_other_type> % _right
);
```

#### <a name="parameters"></a>매개 변수

*(_r)*<br/>
합니다 `auto_handle` 현재 할당할 `auto_handle`합니다.

## <a name="return-value"></a>반환 값

현재 `auto_handle`이제 소유 `_right`합니다.

## <a name="example"></a>예제

```
// msl_auto_handle_op_assign.cpp
// compile with: /clr
#include <msclr\auto_handle.h>

using namespace System;
using namespace msclr;

ref class ClassA {
protected:
   String^ m_s;
public:
   ClassA(String^ s) : m_s(s) {
      Console::WriteLine( "in ClassA constructor: " + m_s );
   }
   ~ClassA() {
      Console::WriteLine( "in ClassA destructor: " + m_s );
   }

   virtual void PrintHello() {
      Console::WriteLine( "Hello from {0} A!", m_s );
   }
};

ref class ClassB : ClassA {
public:
   ClassB( String^ s ) : ClassA( s ) {}
   virtual void PrintHello() new {
      Console::WriteLine( "Hello from {0} B!", m_s );
   }
};

int main()
{
   auto_handle<ClassA> a;
   auto_handle<ClassA> a2(gcnew ClassA( "first" ) );
   a = a2; // assign from same type
   a->PrintHello();

   auto_handle<ClassB> b(gcnew ClassB( "second" ) );
   b->PrintHello();
   a = b; // assign from derived type
   a->PrintHello();

   Console::WriteLine("done");
}
```

```Output
in ClassA constructor: first
Hello from first A!
in ClassA constructor: second
Hello from second B!
in ClassA destructor: first
Hello from second A!
done
in ClassA destructor: second
```

## <a name="requirements"></a>요구 사항

**헤더 파일** \<msclr\auto_handle.h >

**Namespace** msclr

## <a name="see-also"></a>참고 항목

[auto_handle 멤버](../dotnet/auto-handle-members.md)