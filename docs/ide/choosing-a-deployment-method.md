---
title: 배포 방법 선택
ms.date: 11/04/2016
helpviewer_keywords:
- redistributing DLLs
- manifests [C++]
- DLLs [C++], redistributing
- side-by-side assemblies [C++]
- dynamic linking [C++]
- application deployment [C++], methods
- deploying applications [C++], methods
- static linking [C++]
- libraries [C++], application deployment issues
ms.assetid: fd8eb956-f4a0-4ffb-b401-328c73e66986
ms.openlocfilehash: eb9b0784dc5a31accc086314e64758b5bd91033f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50607651"
---
# <a name="choosing-a-deployment-method"></a>배포 방법 선택

Visual C++ 응용 프로그램이 독립적이고 복사 명령을 사용하는 경우가 아니면 Windows Installer를 사용하여 배포하는 것이 좋습니다. Windows Installer는 설치, 수리 및 제거를 지원하고 응용 프로그램 파일, 종속성 및 레지스트리 항목의 원자성 업데이트도 지원합니다.

> [!NOTE]
>  Visual Studio에서 Visual C++ 네이티브 응용 프로그램에 대한 [ClickOnce](/visualstudio/deployment/clickonce-security-and-deployment) 배포가 가능하지만, 추가 단계가 필요합니다. 자세한 내용은 [ClickOnce Deployment for Visual C++ Applications](../ide/clickonce-deployment-for-visual-cpp-applications.md)를 참조하세요.

## <a name="visual-c-libraries-are-shared-dlls"></a>공유 DLL로서의 Visual C++ 라이브러리

Visual C++ 라이브러리는 Visual Studio 설치 관리자에 의해 %windir%\system32\ 디렉터리에 설치되기 때문에 종속된 Visual C++ 응용 프로그램을 개발하면 예상대로 실행됩니다. 그러나 Visual Studio가 설치되지 않은 컴퓨터에 응용 프로그램을 배포하려면 라이브러리가 응용 프로그램과 함께 해당 컴퓨터에 설치되어야 합니다.

## <a name="redistributing-visual-c-libraries"></a>Visual C++ 라이브러리 재배포

배포 시 재배포 권한이 있는 모든 버전의 Visual C++ 라이브러리를 재배포할 수 있습니다. 배포 방법은 다음 세 가지가 있습니다.

- 중앙 배포 - 재배포 가능 패키지를 사용하며 %windir%\system32\\에 Visual C++ 라이브러리를 공유 DLL로 설치합니다. (이 폴더에 설치하려면 관리자 권한이 필요합니다.) 대상 컴퓨터에 응용 프로그램을 설치하기 전에 재배포 가능 패키지를 실행하는 스크립트 또는 설치 프로그램을 만들 수 있습니다. 재배포 가능 패키지는 x86, x64 및 ARM 플랫폼(VCRedist_x86.exe, VCRedist_x64.exe 또는 VCRedist_arm.exe)에 사용할 수 있습니다. Visual Studio는 이러한 패키지를 %ProgramFiles(x86)%\Microsoft Visual Studio `version`\VC\Redist\\`locale ID`\\에 포함합니다. [Microsoft 다운로드 센터](http://go.microsoft.com/fwlink/p/?linkid=132793)에서도 이러한 파일을 다운로드할 수 있습니다. (다운로드 센터의 검색 상자를 사용하여 응용 프로그램과 일치하는 "Visual C++ 재배포 가능 패키지 *Visual Studio 버전 및 업데이트*"를 검색합니다. 예를 들어 Visual Studio 2015 업데이트 3을 사용하여 응용 프로그램을 빌드한 경우 "Visual C++ 재배포 가능 패키지 2015 업데이트 3"을 검색합니다.) 재배포 가능 패키지를 사용하는 방법에 대한 자세한 내용은 [연습: Visual C++ 재배포 가능 패키지를 사용하여 Visual C++ 응용 프로그램 배포](../ide/deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md)를 참조하세요.

- 중앙 배포 - 병합 모듈을 사용하며 각 모듈이 %windir%\system32\\에 특정 Visual C++ 라이브러리를 공유 DLL로 설치합니다. (이 폴더에 설치하려면 관리자 권한이 필요합니다.) 병합 모듈은 응용 프로그램의 .msi 설치 관리자의 일부가 됩니다. Visual C++ 재배포 가능 병합 모듈은 Visual Studio의 \Program Files (x86)\Common Files\Merge Modules\\에 포함됩니다. 자세한 내용은 [병합 모듈을 사용하여 재배포](../ide/redistributing-components-by-using-merge-modules.md)를 참조하세요.

- 로컬 배포 - Visual Studio 설치, 보통 \Program Files (x86)\Microsoft Visual Studio `version`\VC\Redist\\`platform`\\`library`\에서 특정 Visual C++ DLL을 복사하고 대상 컴퓨터의 같은 폴더에 응용 프로그램 실행 파일로 설치합니다. 관리자 권한이 없는 사용자가 설치하려는 경우 또는 네트워크 공유에서 실행할 수 있는 응용 프로그램의 경우 이 배포 메서드를 사용할 수 있습니다.

배포에 재배포 가능 병합 모듈이 사용되거나 관리자 권한이 없는 사용자가 설치를 실행하면 Visual C++ DLL이 설치되지 않고 응용 프로그램이 실행되지 않습니다. 또한 사용자별로 설치할 수 있는 병합 모듈로 빌드된 응용 프로그램 설치 관리자는 시스템의 모든 사용자에게 영향을 주는 공유 위치에 라이브러리를 설치합니다. 로컬 배포를 사용하면 다른 사용자에게 영향을 주지 않거나 관리자 권한 없이도 특정 사용자 애플리케이션의 디렉터리에 필수 Visual C++ DLL을 설치할 수 있습니다. 서비스 효율성 문제가 발생할 수 있으므로 Visual C++ 재배포 가능 DLL을 로컬 배포하지 않는 것이 좋습니다.

Visual C++ 라이브러리를 잘못 배포하면 이러한 라이브러리에 의존하는 응용 프로그램을 실행할 때 런타임 오류가 발생할 수 있습니다. 운영 체제에서 응용 프로그램을 로드할 때 [LoadLibraryEx](http://go.microsoft.com/fwlink/p/?linkid=132792)에 설명된 검색 순서를 사용합니다.

## <a name="dynamic-linking-is-better-than-static-linking"></a>정적 연결보다 나은 동적 연결

Visual C++ 라이브러리를 재배포할 때는 정적 연결을 사용하지 않는 것이 좋습니다. 정적 연결은 응용 프로그램 성능을 상당히 개선하는 경우는 거의 없으면서도 서비스 제공 비용은 거의 항상 높아집니다. 예를 들어 업데이트로 보안이 향상된 라이브러리에 정적으로 연결된 응용 프로그램을 고려하면 응용 프로그램을 다시 컴파일 및 다시 배포하지 않는 한 그 응용 프로그램은 개선되지 않습니다. 대신에 라이브러리를 배포되는 경우에 항상 업데이트할 수 있도록 응용 프로그램을 종속되는 라이브러리에 동적으로 연결하는 것이 좋습니다.

## <a name="see-also"></a>참고 항목

[데스크톱 응용 프로그램 배포](../ide/deploying-native-desktop-applications-visual-cpp.md)<br>
[ClickOnce 보안 및 배포](/visualstudio/deployment/clickonce-security-and-deployment)<br>
[배포 예제](../ide/deployment-examples.md)