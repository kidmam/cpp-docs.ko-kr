---
title: 데이터 소스 개체 인터페이스
ms.date: 10/24/2018
helpviewer_keywords:
- data source objects [C++], interfaces
- data source objects [C++]
- interfaces [C++], OLE DB
- interfaces [C++], list of
- OLE DB provider templates [C++], object interfaces
- OLE DB [C++], interfaces
ms.assetid: 929e100c-c08c-4b64-8437-d8d1357226f6
ms.openlocfilehash: aaa9e90996750b0518999803487fcb39729c76f9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519649"
---
# <a name="data-source-object-interfaces"></a>데이터 소스 개체 인터페이스

다음 표에서 데이터 원본 개체에 대 한 OLE DB에서 정의 된 필수 및 선택적 인터페이스를 보여 줍니다.

|인터페이스|필수 여부|OLE DB 템플릿에서 구현 되었습니까?|
|---------------|---------------|--------------------------------------|
|`IDBCreateSession`|필수|예|
|`IDBInitialize`|필수|예|
|`IDBProperties`|필수|예|
|[IPersist](/windows/desktop/api/objidl/nn-objidl-ipersist)|필수|예|
|[IConnectionPointContainer](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpointcontainer)|Optional|아니요|
|`IDBDataSourceAdmin`|Optional|아니요|
|`IDBInfo`|Optional|아니요|
|[IPersistFile](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|Optional|아니요|
|`ISupportErrorInfo`|Optional|아니요|

데이터 원본 개체를 `IDBProperties`, `IDBInitialize`, 및 `IDBCreateSession` 상속을 통해 인터페이스입니다. 상속 하거나 이러한 구현 클래스 중 하나에서 상속 하지 않도록 하 여 추가 기능을 지원 하도록 선택할 수 있습니다. 지원 하려는 경우는 `IDBDataSourceAdmin` 인터페이스에서 상속 해야 합니다 `IDBDataSourceAdminImpl` 클래스입니다.

## <a name="see-also"></a>참고 항목

[OLE DB 공급자 템플릿 구조](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
