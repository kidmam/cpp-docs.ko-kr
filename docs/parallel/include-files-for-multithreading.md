---
title: 다중 스레딩을 위한 포함 파일
ms.date: 11/04/2016
helpviewer_keywords:
- threading [C++], include files
- include files, multithreading
- multithreading [C++], include files
ms.assetid: 98d764f9-71f4-4da5-8f3a-8d2d26e96799
ms.openlocfilehash: cf7a5ff7e42ffbcf57027014411e089722df16fe
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50591932"
---
# <a name="include-files-for-multithreading"></a>다중 스레딩을 위한 포함 파일

표준 포함 파일은 라이브러리에 구현된 대로 C 런타임 라이브러리 함수를 선언합니다. [최대 최적화](../build/reference/ox-full-optimization.md)(/Ox) 또는 [fastcall 호출 규칙](../build/reference/gd-gr-gv-gz-calling-convention.md)(/Gr) 옵션을 사용하는 경우 컴파일러는 모든 함수가 레지스터 호출 규칙을 사용하여 호출된다고 가정합니다. 런타임 라이브러리 함수는 C 호출 규칙을 사용하여 컴파일되었고 표준 포함 파일의 선언은 컴파일러에서 이들 함수에 대한 올바른 외부 참조를 생성하도록 지정합니다.

## <a name="see-also"></a>참고 항목

[C 및 Win32를 사용한 다중 스레딩](multithreading-with-c-and-win32.md)
