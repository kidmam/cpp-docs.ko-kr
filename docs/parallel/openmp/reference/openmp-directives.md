---
title: OpenMP 지시문
ms.date: 10/22/2018
f1_keywords:
- OpenMP directives
- atomic
- barrier
- critical
- flush
- for
- master
- ordered
- parallel
- section
- SECTIONS
- single
- threadprivate
helpviewer_keywords:
- OpenMP directives
- atomic OpenMP directive
- barrier OpenMP directive
- critical OpenMP directive
- flush OpenMP directive
- for OpenMP directive
- master OpenMP directive
- ordered OpenMP directive
- parallel OpenMP directive
- sections OpenMP directive
- single OpenMP directive
- threadprivate OpenMP directive
ms.assetid: 0562c263-344c-466d-843e-de830d918940
ms.openlocfilehash: a61e74bda4e508bac3c4afd183fa2ab204c629d1
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51333243"
---
# <a name="openmp-directives"></a>OpenMP 지시문

OpenMP API에서 사용 되는 지시문에 대 한 링크를 제공 합니다.

Visual c + +에서는 다음 OpenMP 지시문을 지원합니다.

|지시문|설명|
|---------|-----------|
|[atomic](#atomic)|지정 하는 원자 단위로 업데이트 되는 메모리 위치입니다.|
|[barrier](#barrier)|팀;의 모든 스레드를 동기화합니다. 모든 스레드가 장애물 모든 스레드가 장애물을 실행할 때까지 일시 중지 합니다.|
|[critical](#critical)|한 번에 코드 한 스레드에서 실행만 되는지 지정 합니다.|
|[flush](#flush-openmp)|모든 스레드 모든 공유 개체에 대 한 메모리의 동일한 보기를 지정 합니다.|
|[for](#for-openmp)|수행 된 작업을 하면는 `for` 여러 스레드로 분배 하는 병렬 영역 내부 루프입니다.|
|[master](#master)|마스터 스레드만 프로그램의 섹션을 실행할지를 지정 합니다.|
|[ordered](#ordered-openmp-directives)|해당 코드를 병렬화 된 아래 지정 `for` 순차 루프와 같은 루프를 실행 해야 합니다.|
|[parallel](#parallel)|병렬로 여러 스레드에서 실행 될 코드는 병렬 영역을 정의 합니다.|
|[섹션](#sections-openmp)|모든 스레드 간에 나눌 코드 섹션을 식별 합니다.|
|[single](#single)|코드의 섹션 마스터 스레드 반드시 단일 스레드에서 실행할지를 지정할 수 있습니다.|
|[threadprivate](#threadprivate)|변수는 스레드에 private 임을 지정 합니다.|

## <a name="atomic"></a>원자성

지정 하는 원자 단위로 업데이트 되는 메모리 위치입니다.

```
#pragma omp atomic
   expression
```

### <a name="parameters"></a>매개 변수

*식*<br/>
Lvalue를 둘 이상의 쓰기를 방지 하려면 메모리 위치가 있는 문. 올바른 식 형식에 대 한 자세한 내용은 OpenMP 사양을 참조 하세요.

### <a name="remarks"></a>설명

`atomic` 지시문 없는 OpenMP 절을 지원 합니다.

자세한 내용은 [2.6.4 atomic 생성](../../../parallel/openmp/2-6-4-atomic-construct.md)합니다.

### <a name="example"></a>예제

```
// omp_atomic.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

#define MAX 10

int main() {
   int count = 0;
   #pragma omp parallel num_threads(MAX)
   {
      #pragma omp atomic
      count++;
   }
   printf_s("Number of threads: %d\n", count);
}
```

```Output
Number of threads: 10
```

## <a name="barrier"></a>장벽

팀;의 모든 스레드를 동기화합니다. 모든 스레드가 장애물 모든 스레드가 장애물을 실행할 때까지 일시 중지 합니다.

```
#pragma omp barrier
```

### <a name="remarks"></a>설명

`barrier` 지시문 없는 OpenMP 절을 지원 합니다.

자세한 내용은 [2.6.3 barrier 지시문](../../../parallel/openmp/2-6-3-barrier-directive.md)합니다.

### <a name="example"></a>예제

샘플을 사용 하는 방법에 대 한 `barrier`를 참조 하세요 [마스터](#master)합니다.

## <a name="critical"></a>중요 한

한 번에 하나의 스레드에서 코드는만 실행 됩니다 지정 합니다.

```
#pragma omp critical [(name)]
{
   code_block
}
```

### <a name="parameters"></a>매개 변수

*name*<br/>
(선택 사항) 중요 한 코드를 식별 하는 이름입니다. Note는 이름을 괄호로 묶어야 합니다.

### <a name="remarks"></a>설명

`critical` 지시문 없는 OpenMP 절을 지원 합니다.

자세한 내용은 [중요 한 2.6.2 생성](../../../parallel/openmp/2-6-2-critical-construct.md)합니다.

### <a name="example"></a>예제

```
// omp_critical.cpp
// compile with: /openmp
#include <omp.h>
#include <stdio.h>
#include <stdlib.h>

#define SIZE 10

int main()
{
    int i;
    int max;
    int a[SIZE];

    for (i = 0; i < SIZE; i++)
    {
        a[i] = rand();
        printf_s("%d\n", a[i]);
    }

    max = a[0];
    #pragma omp parallel for num_threads(4)
        for (i = 1; i < SIZE; i++)
        {
            if (a[i] > max)
            {
                #pragma omp critical
                {
                    // compare a[i] and max again because max
                    // could have been changed by another thread after
                    // the comparison outside the critical section
                    if (a[i] > max)
                        max = a[i];
                }
            }
        }

    printf_s("max = %d\n", max);
}
```

```Output
41
18467
6334
26500
19169
15724
11478
29358
26962
24464
max = 29358
```

## <a name="flush-openmp"></a>flush (OpenMP)

모든 스레드 모든 공유 개체에 대 한 메모리의 동일한 보기를 지정 합니다.

```
#pragma omp flush [(var)]
```

### <a name="parameters"></a>매개 변수

*var*<br/>
(선택 사항) 동기화 할 개체를 나타내는 변수의 쉼표로 구분 된 목록입니다. 경우 `var` 지정 하지 않으면 모든 메모리는 플러시됩니다.

### <a name="remarks"></a>설명

`flush` 지시문 없는 OpenMP 절을 지원 합니다.

자세한 내용은 [2.6.5 flush 지시문](../../../parallel/openmp/2-6-5-flush-directive.md)합니다.

### <a name="example"></a>예제

```
// omp_flush.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

void read(int *data) {
   printf_s("read data\n");
   *data = 1;
}

void process(int *data) {
   printf_s("process data\n");
   (*data)++;
}

int main() {
   int data;
   int flag;

   flag = 0;

   #pragma omp parallel sections num_threads(2)
   {
      #pragma omp section
      {
         printf_s("Thread %d: ", omp_get_thread_num( ));
         read(&data);
         #pragma omp flush(data)
         flag = 1;
         #pragma omp flush(flag)
         // Do more work.
      }

      #pragma omp section
      {
         while (!flag) {
            #pragma omp flush(flag)
         }
         #pragma omp flush(data)

         printf_s("Thread %d: ", omp_get_thread_num( ));
         process(&data);
         printf_s("data = %d\n", data);
      }
   }
}
```

```Output
Thread 0: read data
Thread 1: process data
data = 2
```

## <a name="for-openmp"></a>for (OpenMP)

수행 된 작업을 하면는 `for` 여러 스레드로 분배 하는 병렬 영역 내부 루프입니다.

```
#pragma omp [parallel] for [clauses]
   for_statement
```

### <a name="parameters"></a>매개 변수

*절*<br/>
(선택 사항) 0 개 이상의 절입니다. 지 원하는 절의 목록은 설명 섹션을 참조 `for`합니다.

*for_statement*<br/>
`for` 루프입니다. 사용자 코드에서 하는 경우 정의 되지 않은 동작이 발생할는 `for` 루프 인덱스 변수를 변경 합니다.

### <a name="remarks"></a>설명

`for` 지시문 다음 OpenMP 절을 지원 합니다.

- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [nowait](openmp-clauses.md#nowait)
- [ordered](openmp-clauses.md#ordered-openmp-clauses)
- [private](openmp-clauses.md#private-openmp)
- [reduction](openmp-clauses.md#reduction)
- [schedule](openmp-clauses.md#schedule)

하는 경우 `parallel` 도 지정 되어 `clauses` 절에서 사용할 수는 `parallel` 또는 `for` 지시문을 제외한 `nowait`합니다.

자세한 내용은 [2.4.1 for 구문](../../../parallel/openmp/2-4-1-for-construct.md)합니다.

### <a name="example"></a>예제

```
// omp_for.cpp
// compile with: /openmp
#include <stdio.h>
#include <math.h>
#include <omp.h>

#define NUM_THREADS 4
#define NUM_START 1
#define NUM_END 10

int main() {
   int i, nRet = 0, nSum = 0, nStart = NUM_START, nEnd = NUM_END;
   int nThreads = 0, nTmp = nStart + nEnd;
   unsigned uTmp = (unsigned((abs(nStart - nEnd) + 1)) *
                               unsigned(abs(nTmp))) / 2;
   int nSumCalc = uTmp;

   if (nTmp < 0)
      nSumCalc = -nSumCalc;

   omp_set_num_threads(NUM_THREADS);

   #pragma omp parallel default(none) private(i) shared(nSum, nThreads, nStart, nEnd)
   {
      #pragma omp master
      nThreads = omp_get_num_threads();

      #pragma omp for
      for (i=nStart; i<=nEnd; ++i) {
            #pragma omp atomic
            nSum += i;
      }
   }

   if  (nThreads == NUM_THREADS) {
      printf_s("%d OpenMP threads were used.\n", NUM_THREADS);
      nRet = 0;
   }
   else {
      printf_s("Expected %d OpenMP threads, but %d were used.\n",
               NUM_THREADS, nThreads);
      nRet = 1;
   }

   if (nSum != nSumCalc) {
      printf_s("The sum of %d through %d should be %d, "
               "but %d was reported!\n",
               NUM_START, NUM_END, nSumCalc, nSum);
      nRet = 1;
   }
   else
      printf_s("The sum of %d through %d is %d\n",
               NUM_START, NUM_END, nSum);
}
```

```Output
4 OpenMP threads were used.
The sum of 1 through 10 is 55
```

## <a name="master"></a>마스터

마스터 스레드만 프로그램의 섹션을 실행할지를 지정 합니다.

```
#pragma omp master
{
   code_block
}
```

### <a name="remarks"></a>설명

`master` 지시문 없는 OpenMP 절을 지원 합니다.

합니다 [단일](#single) 지시어를 사용 하면 코드 섹션을 마스터 스레드 반드시 단일 스레드에서 실행할지를 지정 합니다.

자세한 내용은 [2.6.1 master 구문](../../../parallel/openmp/2-6-1-master-construct.md)합니다.

### <a name="example"></a>예제

```
// omp_master.cpp
// compile with: /openmp
#include <omp.h>
#include <stdio.h>

int main( )
{
    int a[5], i;

    #pragma omp parallel
    {
        // Perform some computation.
        #pragma omp for
        for (i = 0; i < 5; i++)
            a[i] = i * i;

        // Print intermediate results.
        #pragma omp master
            for (i = 0; i < 5; i++)
                printf_s("a[%d] = %d\n", i, a[i]);

        // Wait.
        #pragma omp barrier

        // Continue with the computation.
        #pragma omp for
        for (i = 0; i < 5; i++)
            a[i] += i;
    }
}
```

```Output
a[0] = 0
a[1] = 1
a[2] = 4
a[3] = 9
a[4] = 16
```

## <a name="ordered-openmp-directives"></a>ordered (OpenMP 지시문)

해당 코드를 병렬화 된 아래 지정 `for` 순차 루프와 같은 루프를 실행 해야 합니다.

```
#pragma omp ordered
   structured-block
```

### <a name="remarks"></a>설명

합니다 `ordered` 지시문은 동적 범위 내에 있어야 합니다.는 [에 대 한](#for-openmp) 또는 `parallel for` 사용 하 여 생성을 `ordered` 절.

`ordered` 지시문 없는 OpenMP 절을 지원 합니다.

자세한 내용은 [2.6.6 ordered 구문](../../../parallel/openmp/2-6-6-ordered-construct.md)합니다.

### <a name="example"></a>예제

```
// omp_ordered.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

static float a[1000], b[1000], c[1000];

void test(int first, int last)
{
    #pragma omp for schedule(static) ordered
    for (int i = first; i <= last; ++i) {
        // Do something here.
        if (i % 2)
        {
            #pragma omp ordered
            printf_s("test() iteration %d\n", i);
        }
    }
}

void test2(int iter)
{
    #pragma omp ordered
    printf_s("test2() iteration %d\n", iter);
}

int main( )
{
    int i;
    #pragma omp parallel
    {
        test(1, 8);
        #pragma omp for ordered
        for (i = 0 ; i < 5 ; i++)
            test2(i);
    }
}
```

```Output
test() iteration 1
test() iteration 3
test() iteration 5
test() iteration 7
test2() iteration 0
test2() iteration 1
test2() iteration 2
test2() iteration 3
test2() iteration 4
```

## <a name="parallel"></a>병렬

병렬로 여러 스레드에서 실행 될 코드는 병렬 영역을 정의 합니다.

```
#pragma omp parallel [clauses]
{
   code_block
}
```

### <a name="parameters"></a>매개 변수

*절*<br/>
(선택 사항) 0 개 이상의 절입니다.  지 원하는 절의 목록은 설명 섹션을 참조 `parallel`합니다.

### <a name="remarks"></a>설명

`parallel` 지시문 다음 OpenMP 절을 지원 합니다.

- [copyin](openmp-clauses.md#copyin)
- [default](openmp-clauses.md#default-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [if](openmp-clauses.md#if-openmp)
- [num_threads](openmp-clauses.md#num-threads)
- [private](openmp-clauses.md#private-openmp)
- [reduction](openmp-clauses.md#reduction)
- [shared](openmp-clauses.md#shared-openmp)

`parallel` 사용 하 여 사용할 수도 있습니다는 [섹션](#sections-openmp) 하 고 [에 대 한](#for-openmp) 지시문입니다.

자세한 내용은 [2.3 parallel 구문](../../../parallel/openmp/2-3-parallel-construct.md)합니다.

### <a name="example"></a>예제

다음 샘플에는 스레드 수를 설정 하 고 병렬 영역을 정의 하는 방법을 보여 줍니다. 스레드 수가 같은지 기본적으로 컴퓨터의 논리 프로세서의 수입니다. 예를 들어, 하이퍼 스레딩을 사용에 실제 프로세서가 있는 컴퓨터에 있는 경우 됩니다 것 두 개의 논리 프로세서와 두 개의 스레드입니다.

```
// omp_parallel.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main() {
   #pragma omp parallel num_threads(4)
   {
      int i = omp_get_thread_num();
      printf_s("Hello from thread %d\n", i);
   }
}
```

```Output
Hello from thread 0
Hello from thread 1
Hello from thread 2
Hello from thread 3
```

### <a name="comment"></a>주석

출력의 순서는 서로 다른 컴퓨터에서 달라질 수 있는 참고 합니다.

## <a name="sections-openmp"></a>sections (OpenMP)

모든 스레드 간에 나눌 코드 섹션을 식별 합니다.

```
#pragma omp [parallel] sections [clauses]
{
   #pragma omp section
   {
      code_block
   }
}
```

### <a name="parameters"></a>매개 변수

*절*<br/>
(선택 사항) 0 개 이상의 절입니다. 지 원하는 절의 목록은 설명 섹션을 참조 `sections`합니다.

### <a name="remarks"></a>설명

합니다 `sections` 지시문에는 0 개 이상 포함 될 수 있습니다 `section` 지시문입니다.

`sections` 지시문 다음 OpenMP 절을 지원 합니다.

- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [nowait](openmp-clauses.md#nowait)
- [private](openmp-clauses.md#private-openmp)
- [reduction](openmp-clauses.md#reduction)

하는 경우 `parallel` 도 지정 되어 `clauses` 절에서 사용할 수는 `parallel` 또는 `sections` 지시문을 제외한 `nowait`합니다.

자세한 내용은 [2.4.2 sections 구문](../../../parallel/openmp/2-4-2-sections-construct.md)합니다.

### <a name="example"></a>예제

```
// omp_sections.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main() {
    #pragma omp parallel sections num_threads(4)
    {
        printf_s("Hello from thread %d\n", omp_get_thread_num());
        #pragma omp section
        printf_s("Hello from thread %d\n", omp_get_thread_num());
    }
}
```

```Output
Hello from thread 0
Hello from thread 0
```

## <a name="single"></a>단일

코드의 섹션 마스터 스레드 반드시 단일 스레드에서 실행할지를 지정할 수 있습니다.

```
#pragma omp single [clauses]
{
   code_block
}
```

### <a name="parameters"></a>매개 변수

*절*<br/>
(선택 사항) 0 개 이상의 절입니다. 지 원하는 절의 목록은 설명 섹션을 참조 `single`합니다.

### <a name="remarks"></a>설명

`single` 지시문 다음 OpenMP 절을 지원 합니다.

- [copyprivate](openmp-clauses.md#copyprivate)
- [firstprivate](openmp-clauses.md#firstprivate)
- [nowait](openmp-clauses.md#nowait)
- [private](openmp-clauses.md#private-openmp)

합니다 [마스터](#master) 지시어를 사용 하면 코드의 섹션은 마스터 스레드에서만 실행 되도록 지정 합니다.

자세한 내용은 [2.4.3 single 생성](../../../parallel/openmp/2-4-3-single-construct.md)합니다.

### <a name="example"></a>예제

```cpp
// omp_single.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main() {
   #pragma omp parallel num_threads(2)
   {
      #pragma omp single
      // Only a single thread can read the input.
      printf_s("read input\n");

      // Multiple threads in the team compute the results.
      printf_s("compute results\n");

      #pragma omp single
      // Only a single thread can write the output.
      printf_s("write output\n");
    }
}
```

```Output
read input
compute results
compute results
write output
```

## <a name="threadprivate"></a>threadprivate

변수는 스레드에 private 임을 지정 합니다.

```
#pragma omp threadprivate(var)
```

### <a name="parameters"></a>매개 변수

*var*<br/>
스레드를 비공개로 하려는 변수의 쉼표로 구분 된 목록입니다. `var` 전역 또는 네임 스페이스-범위 변수 또는 로컬 정적 변수 여야 합니다.

### <a name="remarks"></a>설명

`threadprivate` 지시문 없는 OpenMP 절을 지원 합니다.

자세한 내용은 [2.7.1 threadprivate 지시문](../../../parallel/openmp/2-7-1-threadprivate-directive.md)합니다.

`threadprivate` 지시문 기반으로 [스레드](../../../cpp/thread.md) 를 사용 하 여 특성을 [__declspec](../../../cpp/declspec.md) 키워드;에 대 한 제한 `__declspec(thread)` 적용할 `threadprivate`합니다.

사용할 수 없습니다 `threadprivate` 를 통해 로드 되는 모든 dll [LoadLibrary](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibrarya)합니다.  이 금지 사항으로 로드 되는 Dll을 포함 [/DELAYLOAD (가져오기 로드 지연)](../../../build/reference/delayload-delay-load-import.md)를 사용 하 여 `LoadLibrary`입니다.

사용할 수 있습니다 `threadprivate` 프로세스를 시작할 때 정적으로 로드 된 dll에서입니다.

때문에 `threadprivate` 더해서 `__declspec(thread)`, `threadprivate` 변수는 모든 스레드를 병렬 영역에 의해 생성 된 스레드 팀의 일부인 스레드 뿐 아니라 프로세스에서 시작에 존재 합니다.  이 구현 세부 정보에 주의 예를 들어 해당 생성자에 대 한 알 수 있습니다는 `threadprivate` 사용자 정의 형식을 예상 하는 다음에 종종 자세한 라고 합니다.

`threadprivate` destructable 형식 변수의 라는 해당 소멸자가 보장 되지 않습니다.  예를 들어:

```
struct MyType
{
    ~MyType();
};

MyType threaded_var;
#pragma omp threadprivate(threaded_var)
int main()
{
    #pragma omp parallel
    {}
}
```

사용자가 병렬 영역을 구성 하는 스레드를 종료 하는 경우에 대 한 제어 하지 않습니다.  프로세스가 종료, 스레드가 프로세스 종료에 대 한 알림이 발송 되지 않습니다 및 소멸자에 대 한 호출 되지 않습니다 하는 경우 해당 스레드에 있으면 `threaded_var` 끝내는 것을 제외 하 고 모든 스레드에서 (여기, 기본 스레드).  코드의 적절 한 소멸은 기대 하지 있도록 `threadprivate` 변수입니다.

### <a name="example"></a>예제

사용 하는 예제에 대 한 `threadprivate`를 참조 하세요 [개인](openmp-clauses.md#private-openmp)합니다.
