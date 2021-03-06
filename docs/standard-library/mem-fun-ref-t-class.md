---
title: mem_fun_ref_t 클래스
ms.date: 11/04/2016
f1_keywords:
- xfunctional/std::mem_fun_ref_t
helpviewer_keywords:
- mem_fun_ref_t class
ms.assetid: 7dadcac3-8d33-4e4b-a792-81bd53d3df39
ms.openlocfilehash: 752b3aeb4126ba41b7a0741ed9de68db018dd6c4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488038"
---
# <a name="memfunreft-class"></a>mem_fun_ref_t 클래스

허용 하는 어댑터 클래스를 `non_const` 멤버 함수는 인수 없이 참조 인수를 사용 하 여 초기화할 때 단항 함수 개체로 호출할 수 있습니다.

## <a name="syntax"></a>구문

```cpp
template <class Result, class Type>
class mem_fun_ref_t : public unary_function<Type, Result> {
    explicit mem_fun_ref_t(
    Result (Type::* _Pm)());

    Result operator()(Type& left) const;

};
```

### <a name="parameters"></a>매개 변수

*_Pm*<br/>
함수 개체로 변환할 `Type` 클래스의 멤버 함수 포인터입니다.

*left*<br/>
개체는 합니다 *_Pm* 멤버 함수가 호출 됩니다.

## <a name="return-value"></a>반환 값

조정 가능한 단항 함수입니다.

## <a name="remarks"></a>설명

복사본을 저장 하는 템플릿 클래스 *_Pm*, 클래스의 멤버 함수에 대 한 포인터 여야 `Type`, 전용 멤버 개체에 있습니다. 또한 해당 멤버 함수 `operator()`를 ( **left**.* `_Pm`)( )을 반환하는 것으로 정의합니다.

## <a name="example"></a>예제

`mem_fun_ref_t`의 생성자는 일반적으로 직접 사용되지 않습니다. 도우미 함수 `mem_fun_ref`은 멤버 함수를 적용하는 데 사용됩니다. 멤버 함수 어댑터를 사용하는 방법에 대한 예제는 [mem_fun_ref](../standard-library/functional-functions.md#mem_fun_ref)를 참조하세요.

## <a name="requirements"></a>요구 사항

**헤더:** \<functional>

**네임스페이스:** std

## <a name="see-also"></a>참고자료

[C++ 표준 라이브러리의 스레드 보안](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 표준 라이브러리 참조](../standard-library/cpp-standard-library-reference.md)<br/>
