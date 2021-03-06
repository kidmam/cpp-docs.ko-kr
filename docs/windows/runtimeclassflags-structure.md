---
title: RuntimeClassFlags 구조체
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClassFlags
- implements/Microsoft::WRL::RuntimeClassFlags::value
helpviewer_keywords:
- Microsoft::WRL::RuntimeClassFlags structure
- Microsoft::WRL::RuntimeClassFlags::value constant
ms.assetid: 7098d605-bd14-4d51-82f4-3def8296a938
ms.openlocfilehash: 74ae72dc87d45abba04d15303ed2ec92b18f8c28
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668535"
---
# <a name="runtimeclassflags-structure"></a>RuntimeClassFlags 구조체

인스턴스에 대 한 형식이 포함 된 [RuntimeClass](../windows/runtimeclass-class.md)합니다.

## <a name="syntax"></a>구문

```cpp
template <unsigned int flags>
struct RuntimeClassFlags;
```

### <a name="parameters"></a>매개 변수

*flags*<br/>
A [RuntimeClassType 열거형](../windows/runtimeclasstype-enumeration.md) 값입니다.

## <a name="members"></a>멤버

### <a name="public-constants"></a>공용 상수

|이름|설명|
|----------|-----------------|
|[RuntimeClassFlags::value 상수](#value-constant)|포함 된 [RuntimeClassType 열거형](../windows/runtimeclasstype-enumeration.md) 값입니다.|

## <a name="inheritance-hierarchy"></a>상속 계층

`RuntimeClassFlags`

## <a name="requirements"></a>요구 사항

**헤더:** implements.h

**네임스페이스:** Microsoft::WRL

## <a name="value-constant"></a>Runtimeclassflags:: Value 상수

포함 된 필드를 [RuntimeClassType 열거형](../windows/runtimeclasstype-enumeration.md) 값입니다.

```cpp
static const unsigned int value = flags;
```
