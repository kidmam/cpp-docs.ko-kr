---
title: A.4   nowait 절 사용
ms.date: 11/04/2016
ms.assetid: d3de2111-05ea-4ee3-a66c-57bd988712af
ms.openlocfilehash: 7f839397787c35e88ea325c2db81b15b3a4e7508
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50454927"
---
# <a name="a4---using-the-nowait-clause"></a>A.4   nowait 절 사용

병렬 영역 내부에서는 여러 독립적인 루프의 경우 사용할 수는 `nowait` 절 ([2.4.1 섹션](../../parallel/openmp/2-4-1-for-construct.md) 11 페이지) 끝에 암시적된 장벽을 사용 하지 않으려면는 `for` 다음과 같은 지시문:

```
#pragma omp parallel
{
    #pragma omp for nowait
        for (i=1; i<n; i++)
             b[i] = (a[i] + a[i-1]) / 2.0;
    #pragma omp for nowait
        for (i=0; i<m; i++)
            y[i] = sqrt(z[i]);
}
```