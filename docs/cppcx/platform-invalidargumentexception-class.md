---
title: Platform::InvalidArgumentException 클래스
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::InvalidArgumentException
- VCCORLIB/Platform::InvalidArgumentException::InvalidArgumentException
helpviewer_keywords:
- Platform::InvalidArgumentException
ms.assetid: 1a8d860b-3bcb-41a9-9346-6610616a0b46
ms.openlocfilehash: 11b1e0e2166bba2dc366520161729a8d84e865d7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643614"
---
# <a name="platforminvalidargumentexception-class"></a>Platform::InvalidArgumentException 클래스

메서드에 제공된 인수 중 하나가 유효하지 않을 때 throw됩니다.

## <a name="syntax"></a>구문

```cpp
public ref class InvalidArgumentException : COMException,    IException,    IPrintable,    IEquatable
```

### <a name="remarks"></a>설명

자세한 내용은 [COMException](../cppcx/platform-comexception-class.md) 클래스를 참조하세요.

### <a name="requirements"></a>요구 사항

**지원 되는 최소 클라이언트:** Windows 8

**지원 되는 최소 서버:** Windows Server 2012

**네임스페이스:** Platform

**메타데이터:** platform.winmd

## <a name="see-also"></a>참고 항목

[Platform::COMException 클래스](../cppcx/platform-comexception-class.md)