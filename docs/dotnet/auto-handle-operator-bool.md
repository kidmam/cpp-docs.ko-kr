---
title: auto_handle::operator bool
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- auto_handle.operator bool
- msclr.auto_handle.operator bool
- operator bool
- msclr::auto_handle::operator bool
- auto_handle::operator bool
helpviewer_keywords:
- auto_handle::operator bool
ms.assetid: 2e535e99-cf87-4008-b588-02c587d77453
ms.openlocfilehash: 95a4b324194b2e1adf8cc9596f8e2440379e5a47
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50565947"
---
# <a name="autohandleoperator-bool"></a>auto_handle::operator bool

연산자를 사용 하 여 `auto_handle` 조건식에서입니다.

## <a name="syntax"></a>구문

```
operator bool();
```

## <a name="return-value"></a>반환 값

**true** 래핑된 개체가 잘못 되었습니다. **false** 그렇지 않은 경우.

## <a name="remarks"></a>설명

이 연산자를 실제로 변환 `_detail_class::_safe_bool` 는 보다 안전한 **bool** 정수 계열 형식으로 변환할 수 없기 때문입니다.

## <a name="example"></a>예제

```
// msl_auto_handle_operator_bool.cpp
// compile with: /clr
#include <msclr\auto_handle.h>

using namespace System;
using namespace msclr;

int main() {
   auto_handle<String> s1;
   auto_handle<String> s2 = "hi";
   if ( s1 ) Console::WriteLine( "s1 is valid" );
   if ( !s1 ) Console::WriteLine( "s1 is invalid" );
   if ( s2 ) Console::WriteLine( "s2 is valid" );
   if ( !s2 ) Console::WriteLine( "s2 is invalid" );
   s2.reset();
   if ( s2 ) Console::WriteLine( "s2 is now valid" );
   if ( !s2 ) Console::WriteLine( "s2 is now invalid" );
}
```

```Output
s1 is invalid
s2 is valid
s2 is now invalid
```

## <a name="requirements"></a>요구 사항

**헤더 파일** \<msclr\auto_handle.h >

**Namespace** msclr

## <a name="see-also"></a>참고 항목

[auto_handle 멤버](../dotnet/auto-handle-members.md)<br/>
[auto_handle::operator!](../dotnet/auto-handle-operator-logical-not.md)