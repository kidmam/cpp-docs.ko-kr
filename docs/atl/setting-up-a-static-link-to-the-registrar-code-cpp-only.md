---
title: 등록자 코드 (c + + 전용)에 대 한 정적 링크 설정
ms.date: 11/04/2016
helpviewer_keywords:
- statically linking to ATL Registrar code
- linking [C++], to ATL Registrar code
ms.assetid: 835f5885-87a6-48fa-91e6-60988ee65538
ms.openlocfilehash: 11600b47abbbd247d099d871fce5e9d5d17d3cf4
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51327891"
---
# <a name="setting-up-a-static-link-to-the-registrar-code-c-only"></a>등록자 코드 (c + + 전용)에 대 한 정적 링크 설정

C + + 클라이언트 등록자 코드에 정적 링크를 만들 수 있습니다. 릴리스 빌드를 약 5 K 추가 기관의 파서를 정적으로 연결 합니다.

정적 연결을 설정 하는 가장 간단한 방법은 사용자가 지정한 가정 [DECLARE_REGISTRY_RESOURCEID](reference/registry-macros.md#declare_registry_resourceid) 개체의 선언입니다. (이 ATL을 사용한 기본 사양은)

## <a name="to-create-a-static-link-using-declareregistryresourceid"></a>DECLARE_REGISTRY_RESOURCEID를 사용 하 여 정적 링크를 만들려면

1. 지정할 [/D](../build/reference/d-preprocessor-definitions.md)  **\_ATL\_정적\_레지스트리** of **/D \_ATL\_DLL**합니다.

1. 다시 컴파일하십시오.

## <a name="see-also"></a>참고 항목

[레지스트리 구성 요소 (등록자)](../atl/atl-registry-component-registrar.md)
