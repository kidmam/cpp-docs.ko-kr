---
title: 'TN032: MFC 예외 메커니즘'
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.exceptions
helpviewer_keywords:
- TN032
- MFC, exceptions
- CException class [MFC], using
ms.assetid: 0271f0aa-82cb-47a2-b7ea-e88126fc7e43
ms.openlocfilehash: f3f13bb40151d3b9ef0d57c7e769ca30fa629177
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50633394"
---
# <a name="tn032-mfc-exception-mechanism"></a>TN032: MFC 예외 메커니즘

MFC 매크로 제공 하 고 이전 버전의 Visual c + + 표준 c + + 예외 메커니즘을 지원 하지 않았습니다 **TRY/CATCH/THROW** 대신 사용 되었습니다. 이 버전의 Visual C++에서는 C++ 예외가 완전히 지원됩니다. 이 설명서에서는 스택 기반 개체를 자동으로 정리하는 방법을 포함해서 이전 매크로의 고급 구현 세부 정보를 다룹니다. C++ 예외 스택은 기본적으로 스택 해제가 지원되기 때문에 이 기술 설명은 더 이상 필요하지 않습니다.

가리킵니다 [예외: MFC 매크로 및 c + + 예외 사용](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md) MFC 매크로 및 새 c + + 키워드 사이의 차이점에 대 한 자세한 내용은 합니다.

## <a name="see-also"></a>참고 항목

[번호별 기술 참고 사항](../mfc/technical-notes-by-number.md)<br/>
[범주별 기술 참고 사항](../mfc/technical-notes-by-category.md)

