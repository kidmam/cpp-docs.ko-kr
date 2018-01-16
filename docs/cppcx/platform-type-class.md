---
title: "Platform:: type 클래스 | Microsoft Docs"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- VCCORLIB/Platform::Type::GetTypeCode
- VCCORLIB/Platform::Type::FullName
dev_langs: C++
helpviewer_keywords: Platform::Type Class
ms.assetid: d6b03f1e-b240-49b9-a08e-53a460030475
caps.latest.revision: "7"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c292426b9d04fd5b3d9785224f9b2d48f129f0db
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/21/2017
---
# <a name="platformtype-class"></a>Platform::Type 클래스
특정 형식에 대한 런타임 정보(문자열 이름 및 형식 코드)를 포함합니다. 호출 하 여 가져온 [object:: gettype](../cppcx/platform-object-class.md#gettype) 임의 개체에서 또는 또는 사용 하 여는 [typeid](../windows/typeid-cpp-component-extensions.md) 클래스 또는 구조체 이름에는 연산자입니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
public ref class Platform::Type :      
    Platform::Object, Platform::Details::IEquatable,
    Platform::Details::IPrintable  
```  
  
### <a name="remarks"></a>설명  
 `Type` 클래스는 개체의 런타임 형식을 기반으로 분기하는 `if` 또는 `switch` 문을 사용하여 처리를 지시해야 하는 응용 프로그램에서 유용합니다. 형식 범주를 설명 하는 형식 코드를 사용 하 여 검색 되는 [type:: gettypecode](#gettypecode) 멤버 함수입니다.  
  
## <a name="public-methods"></a>public 메서드  
  
|||  
|-|-|  
|[Type::GetTypeCode 메서드](#gettypecode)|개체의 [Platform::TypeCode 열거형](../cppcx/platform-typecode-enumeration.md) 값을 반환합니다.| 
|[Type::ToString 메서드](#tostring)|해당 메타 데이터에 지정 된 형식의 이름을 반환합니다.| 

 
## <a name="public-properties"></a>public 속성  
  
|||  
|-|-|  
|[Type:: fullname](#fullname)|형식의 정규화된 이름을 나타내며 ::(콜론 두 개) 대신 .(점)을 구분 기호로 사용(예: "MyNamespace.MyClass")하는 [Platform::String 클래스](../cppcx/platform-string-class.md)^을 (점)를 구분 하지 않습니다:: (콜론)-예를 들어 `MyNamespace.MyClass`합니다.|  
  
## <a name="conversion-operators"></a>변환 연산자  
  
|||  
|-|-|  
|[연산자 Type^](../cppcx/operator-subtracttype-hat.md)|`Windows::UI::Xaml::Interop::TypeName` 을 `Platform::Type`으로 변환할 수 있습니다.|  
|[연산자 Windows::UI::Xaml::Interop::TypeName](../cppcx/operator-subtractwindows-ui-xaml-interop-typename.md)|`Platform::Type` 을 `Windows::UI::Xaml::Interop::TypeName`으로 변환할 수 있습니다.|  
  
### <a name="requirements"></a>요구 사항  
 **지원 되는 최소 클라이언트:** Windows 8  
  
 **지원 되는 최소 서버:** Windows Server 2012  
  
 **네임스페이스:** Platform  
  
 **메타데이터:** platform.winmd  

 
## <a name="fullname"></a> Type::FullName 속성
폼에서 현재 형식의 정규화 된 이름을 검색 `Namespace.Type`합니다.  
  
### <a name="syntax"></a>구문  
  
```cpp  
String^ FullName();  
```  
  
### <a name="return-value"></a>반환 값  
 형식의 이름입니다.  
### <a name="example"></a>예  
  
```  
  
//  namespace is TestApp  
MainPage::MainPage()  
{  
    InitializeComponent();  
    Type^ t = this->GetType();  
    auto s = t->FullName; // returns "TestApp.MainPage"  
    auto s2 = t->ToString(); //also returns "TestApp.MainPage"  
}  
```  
  


## <a name="gettypecode"></a> Type::GetTypeCode 메서드
기본 제공 형식의 숫자 형식 범주를 검색합니다.  
  
### <a name="syntax"></a>구문  
  
```cpp  
Platform::TypeCode GetTypeCode();  
```  
  
### <a name="return-value"></a>반환 값  
 Platform::TypeCode 열거형 값의 하나입니다.  
  
### <a name="remarks"></a>설명  
 Gettypecode () 멤버 메서드에 해당 합니다는 `typeid` 속성입니다.

## <a name="tostring"></a>Type::ToString 메서드
검색 한 형식의 이름입니다.  
  
### <a name="syntax"></a>구문  
  
```cpp  
Platform::String^ ToString();  
```  
  
### <a name="return-value"></a>반환 값  
 해당 메타 데이터에 지정 된 형식의 이름입니다.    
  
## <a name="see-also"></a>참고 항목  
 [Platform 네임 스페이스](../cppcx/platform-namespace-c-cx.md)