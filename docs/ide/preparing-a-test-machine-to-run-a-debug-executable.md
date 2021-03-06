---
title: 디버그 실행 파일을 실행하기 위한 테스트 컴퓨터 준비
ms.date: 11/04/2016
helpviewer_keywords:
- debug executable, preparing a test machine to run
ms.assetid: f0400989-cc2e-4dce-9788-6bdbe91c6f5a
ms.openlocfilehash: 95633a9b6b04be7e551934744868e10f60d51fb4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50509107"
---
# <a name="preparing-a-test-machine-to-run-a-debug-executable"></a>디버그 실행 파일을 실행하기 위한 테스트 컴퓨터 준비

Visual C++로 빌드한 응용 프로그램의 디버그 버전을 테스트하기 위해 컴퓨터를 준비하려면 응용 프로그램이 종속된 Visual C++ 라이브러리 DLL의 디버그 버전을 배포해야 합니다. 배포해야 할 DLL을 식별하려면 [Visual C++ 응용 프로그램의 종속성 이해](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)의 단계를 수행합니다. Visual C++ 라이브러리 DLL의 디버그 버전에는 일반적으로 "d"로 끝나는 이름이 부여됩니다. 예를 들어 msvcr100.dll의 디버그 버전 이름은 msvcr100d.dll입니다.

> [!NOTE]
>  응용 프로그램의 디버그 버전은 재배포할 수 없으며 Visual C++ 라이브러리 DLL의 디버그 버전도 재배포할 수 없습니다. 응용 프로그램과 Visual C++ DLL의 디버그 버전은 Visual Studio가 설치되지 않은 컴퓨터에서 응용 프로그램을 디버깅 및 테스트하기 위한 목적으로만 다른 컴퓨터에 배포할 수 있습니다. 자세한 내용은 [Redistributing Visual C++ Files](../ide/redistributing-visual-cpp-files.md)을 참조하세요.

세 가지 방법으로 응용 프로그램의 디버그 버전과 Visual C++ 라이브러리 DLL의 디버그 버전을 함께 배포할 수 있습니다.

- 올바른 라이브러리 버전과 응용 프로그램의 아키텍처에 대한 병합 모듈을 포함한 설치 프로젝트를 사용하고 중앙 배포를 이용하여 특정 Visual C++ DLL 디버그 버전을 %windir%\system32\ 디렉터리에 설치합니다. 병합 모듈은 \Common Files\Merge Modules\\의 Program Files 또는 Program Files (x86) 디렉터리에 있습니다. 병합 모듈의 디버그 버전에는 Microsoft_VC110_DebugCRT_x86.msm과 같이 이름에 Debug가 있습니다. 이 배포의 예는 [연습: 설치 프로젝트를 사용하여 Visual C++ 응용 프로그램 배포](../ide/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md)에 나와 있습니다.

- 응용 프로그램의 설치 디렉터리에 특정 Visual C++ DLL의 디버그 버전을 설치하기 위해서는 Program Files 또는 Program Files (x86) 디렉터리의 \Microsoft Visual Studio \<버전>\VC\redist\Debug_NonRedist\\에 제공된 파일을 이용하여 로컬 배포를 수행합니다.

    > [!NOTE]
    >  다른 컴퓨터에서 Visual C++ 2005 또는 Visual C++ 2008로 빌드한 응용 프로그램을 원격으로 디버깅하려면 Visual C++ 라이브러리 DLL 디버그 버전을 공유 side-by-side 어셈블리로 배포해야 합니다. 설치 프로젝트 또는 Windows Installer를 사용하여 해당 병합 모듈을 설치할 수 있습니다.

- Visual Studio의 **구성 관리자** 대화 상자에 있는 **배포** 옵션을 사용하여 프로젝트 출력물 및 기타 파일을 원격 컴퓨터에 복사합니다.

Visual C++ DLL이 설치되었으면 네트워크 공유를 통해 원격 디버거를 실행할 수 있습니다. 원격 디버깅에 대한 자세한 내용은 [원격 디버깅](/visualstudio/debugger/remote-debugging.md)을 참조하세요.

## <a name="see-also"></a>참고 항목

[Visual C++의 개발](../ide/deployment-in-visual-cpp.md)<br>
[Windows Installer 명령줄 옵션](/windows/desktop/Msi/command-line-options)<br>
[배포 예제](../ide/deployment-examples.md)<br>
[Remote Debugging](/visualstudio/debugger/remote-debugging.md)