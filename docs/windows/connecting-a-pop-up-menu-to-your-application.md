---
title: C + + 응용 프로그램에 팝업 메뉴 연결
ms.date: 11/04/2016
helpviewer_keywords:
- pop-up menus [C++], connecting to applications
- context menus [C++], connecting to applications
- menus [C++], pop-up
- shortcut menus [C++], connecting to applications
ms.assetid: 295cbf0e-6416-478e-bc3d-472fb98e0e52
ms.openlocfilehash: 8a0cb64caaa58b464b0d5abb52093350c5e3cfeb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50556496"
---
# <a name="connecting-a-pop-up-menu-to-your-c-application"></a>C + + 응용 프로그램에 팝업 메뉴 연결

### <a name="to-connect-a-pop-up-menu-to-your-application"></a>응용 프로그램에 팝업 메뉴를 연결하려면

1. 예를 들어 WM_CONTEXTMENU에 대 한 메시지 처리기를 추가 합니다. 자세한 내용은 [함수에 메시지 매핑](../mfc/reference/mapping-messages-to-functions.md)합니다.

2. 메시지 처리기에 다음 코드를 추가합니다.

    ```cpp
    CMenu menu;
    VERIFY(menu.LoadMenu(IDR_MENU1));
    CMenu* pPopup = menu.GetSubMenu(0);
    ASSERT(pPopup != NULL);
    pPopup->TrackPopupMenu(TPM_LEFTALIGN | TPM_RIGHTBUTTON, point.x, point.y, AfxGetMainWnd());
    ```

   > [!NOTE]
   > 합니다 [CPoint](../atl-mfc-shared/reference/cpoint-class.md) 전달 된 메시지 처리기는 화면 좌표입니다.

## <a name="requirements"></a>요구 사항

MFC

## <a name="see-also"></a>참고 항목

[팝업 메뉴 만들기](../windows/creating-pop-up-menus.md)<br/>
[메뉴 편집기](../windows/menu-editor.md)