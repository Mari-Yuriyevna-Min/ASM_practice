[C99]
```C
#include <stdio.h>
int main()
{
    int a=10;
    int b=20;
    int sum = a+b;
    int sub = a-b;
    int mul = a*b;
    int inv = -a;

    printf("%d\n", a);
    printf("%d\n", b);
    printf("%d\n", sum);
    printf("%d\n", sub);
    printf("%d\n", mul);
    printf("%d\n", inv);
    return 0;
}
```
[ASM x86-64]
```ASM
.LC0: 
        .string "%d\n"    //    출력함수
main:    //    메인함수
        push    rbp    //    시작
        mov     rbp, rsp    //    메인함수 시작 포인트 가져오기
        sub     rsp, 32    //    32바이트 공간 만들기
        mov     DWORD PTR [rbp-4], 10    //    int 변수 a, 10(dec)
        mov     DWORD PTR [rbp-8], 20    //    int 변수 b, 20(dec)
        mov     edx, DWORD PTR [rbp-4]    //    변수 a를 edx에 대입
        mov     eax, DWORD PTR [rbp-8]    //    변수 b를 eax에 대입
        add     eax, edx    //    edx와 eax를 더하기 연산 후 eax에 계산값 대입
        mov     DWORD PTR [rbp-12], eax    //    eax의 값 = int 변수 sum
        mov     eax, DWORD PTR [rbp-4]    //     변수 a를 eax에 대입
        sub     eax, DWORD PTR [rbp-8]    //    변수 b를 eax(=a)에서 빼기 연산 후 eax에 계산값 대입
        mov     DWORD PTR [rbp-16], eax    //    eax의 값 = int 변수 sub
        mov     eax, DWORD PTR [rbp-4]    //     변수 a를 eax에 대입
        imul    eax, DWORD PTR [rbp-8]    //    변수 b를 eax(=a)과 곱하기 연산 후 eax에 계산값 대입
        mov     DWORD PTR [rbp-20], eax    //    eax의 값 = int 변수 mul
        mov     eax, DWORD PTR [rbp-4]    //    변수 a를 eax에 대입
        neg     eax    //    eax 값을 음수로 변환
        mov     DWORD PTR [rbp-24], eax    //    eax 음수 값을 int 변수 inv에 대입
        mov     eax, DWORD PTR [rbp-4]    
        mov     esi, eax
        mov     edi, OFFSET FLAT:.LC0
        mov     eax, 0
        call    printf    //    a 값 출력
        mov     eax, DWORD PTR [rbp-8]
        mov     esi, eax
        mov     edi, OFFSET FLAT:.LC0
        mov     eax, 0
        call    printf    //    b 값 출력
        mov     eax, DWORD PTR [rbp-12]
        mov     esi, eax
        mov     edi, OFFSET FLAT:.LC0
        mov     eax, 0
        call    printf    //    sum 값 출력
        mov     eax, DWORD PTR [rbp-16]
        mov     esi, eax
        mov     edi, OFFSET FLAT:.LC0
        mov     eax, 0
        call    printf    //    sub 값 출력
        mov     eax, DWORD PTR [rbp-20]
        mov     esi, eax
        mov     edi, OFFSET FLAT:.LC0
        mov     eax, 0
        call    printf    //    mul 값 출력
        mov     eax, DWORD PTR [rbp-24]
        mov     esi, eax
        mov     edi, OFFSET FLAT:.LC0
        mov     eax, 0
        call    printf    //    inv 값 출력
        mov     eax, 0
        leave    //    main함수 끝
        ret    //    프로그램 끝
