---
title: 다른 언어 (c + +)에 대 한 버전 정보 추가
ms.date: 11/04/2016
f1_keywords:
- vc.editors.version
helpviewer_keywords:
- languages, version information
- New Version Info Block
- blocks, adding
- resources [C++], adding version information
- version information, adding for languages
ms.assetid: 17f6273c-e1cc-441a-a3d8-f564341cbf20
ms.openlocfilehash: 6d79fb575817d5ba743e4efc460154eb03dca4f5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534591"
---
# <a name="adding-version-information-for-another-language-c"></a>다른 언어 (c + +)에 대 한 버전 정보 추가

### <a name="to-add-version-information-for-another-language-new-info-block"></a>다른 언어의 버전 정보(새로운 정보 블록)를 추가하려면

1. [리소스 뷰](../windows/resource-view-window.md)에서 버전 정보 리소스를 두 번 클릭하여 이를 엽니다.

   > [!NOTE]
   > 프로젝트에 .rc 파일이 아직 없는 경우 [새 리소스 스크립트 파일 만들기](../windows/how-to-create-a-resource-script-file.md)를 참조하세요.

2. 버전 정보 테이블 내에서 마우스 오른쪽 단추를 클릭하고 바로 가기 메뉴에서 **새 버전 정보 블록** 을 선택합니다.

   이 명령은 현재 버전 정보 리소스에 추가 정보 블록을 추가하고 [속성 창](/visualstudio/ide/reference/properties-window)에서 해당 속성을 엽니다.

3. **속성** 창에서 새 블록에 적절한 언어 및 문자 집합을 선택합니다.

관리 되는 프로젝트에 리소스를 추가 하는 방법에 대 한 정보를 참조 하세요 [데스크톱 앱의 리소스](/dotnet/framework/resources/index) 에 *.NET Framework Developer's Guide*합니다. 수동으로 관리 되는 프로젝트에 리소스 파일을 추가, 리소스 액세스, 정적 리소스 표시 및 속성에 리소스 문자열 할당에 대 한 내용은 참조 하세요 [데스크톱 앱에 대 한 리소스 파일 만들기](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)합니다. 전역화 및 지역화 관리 되는 앱의 리소스에 대 한 내용은 참조 하세요 [Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)합니다.

## <a name="requirements"></a>요구 사항

Win32

## <a name="see-also"></a>참고 항목

[버전 정보 편집기](../windows/version-information-editor.md)<br/>
[버전 정보(Windows)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)