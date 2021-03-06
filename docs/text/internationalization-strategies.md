﻿---
title: 국제화 전략
ms.date: 11/04/2016
helpviewer_keywords:
- globalization [C++], character sets
- language-portable code [C++]
- MBCS [C++], internationalization strategies
- Windows API [C++], international programming strategies
- Win32 [C++], international programming strategies
- Unicode [C++], globalizing applications
- character sets [C++], international programming strategies
- localization [C++], character sets
ms.assetid: b09d9854-0709-4b9a-a00c-b0b8bc4199b1
ms.openlocfilehash: 91f4805152944202b7d3f7f45fce494f7e9d81af
ms.sourcegitcommit: ff3cbe4235b6c316edcc7677f79f70c3e784ad76
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53626684"
---
# <a name="internationalization-strategies"></a>국제화 전략

대상 운영체제 및 시장에 따라 몇 가지 국제화에 대한 고민이 필요합니다.

- 응용 프로그램에서 유니코드를 사용 합니다.

   특수 목적을 위한 일부 프로그램에서는 ANSI 문자를 사용할 수 있겠지만, 유니코드는 16비트로 인코딩되어 모든 문자 집합을 표현 할 수 있는 유니코드를 사용합니다. C 런타임 라이브러리에tj는 유니코드 프로그래밍을 위한 전용 함수, 매크로 및 데이터 형식을 제공합니다. MFC는 유니코드를 완벽하게 지원합니다.

- 응용 프로그램이 MBCS를 사용하면 모든 Win32 플랫폼에서 실행 가능합니다.

   MBCS을 사용하면 문자열에는 싱글 바이트 문자, 더블 바이트 문자 또는 두 문자 집합을 모두 포함할 수 있습니다 C 런타임 라이브러리는 MBCS 프로그래밍을 위한 전용 함수, 매크로 및 데이터 형식을 제공합니다. MFC는 완벽하게 MBCS도 지원합니다.

- 만일 다양한 환경으로의 이식성에 대비해 응용 프로그램의 소스 코드를 작성해야 한다면 `_UNICODE` 또는 `_MBCS` 기호를 이용해 코드를 작성하여 개발할 수 있습니다. 자세한 내용은 [tchar.h의 제네릭 텍스트 매핑](../text/generic-text-mappings-in-tchar-h.md)합니다.

   완전한 이식이 가능한 C 런타임 함수, 매크로 및 데이터 형식을 사용할 수 있습니다. MFC를 사용하면 이러한 전략을 유연하게 적용할 수 있습니다.

이러한 주제의 나머지 부분에서는 MBCS 또는 유니코드로 빌드할 수 있는 완전히 이식 가능한 코드 작성에 중점을 둡니다.

## <a name="see-also"></a>참고 항목

[유니코드 및 MBCS](../text/unicode-and-mbcs.md)<br/>
[로캘 및 코드 페이지](../text/locales-and-code-pages.md)
