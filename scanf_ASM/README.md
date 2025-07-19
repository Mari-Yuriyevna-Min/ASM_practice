#include <stdio.h>
int main()
    {
        int a;
        printf("enter a : \n");
        scanf("%d", &a);
        printf("You entered %d...\n", a);
        return 0;
    }


// ----------


.LC0:  //  0번째 문자열
        .string "enter a : "
.LC1:  //  1번째 문자열
        .string "%d" 
.LC2:  //  2번째 문자열
        .string "you entered %d ... \n"
main:  //  메인 함수
        push    rbp    //  스택에 rbp 넣기
        mov     rbp, rsp    //  rsp로 스택의 시작 부분 설정
        sub     rsp, 16    //  16바이트 할당
        mov     edi, OFFSET FLAT:.LC0    //  0번째 문자열
        call    puts    //  다시 포인터를 스택 쪽으로 옮김
        lea     rax, [rbp-4]    //    4바이트짜리 변수 설정
        mov     rsi, rax    //    변수값이 있는 주소 저장
        mov     edi, OFFSET FLAT:.LC1    //    1번째 문자열
        mov     eax, 0    //   입력되는 변수가 저장되는 eax 칸을 초기화
        call    __isoc99_scanf    //    scanf 함수를 C99 라이브러리에서 가져옴
        mov     eax, DWORD PTR [rbp-4]    //    eax 칸에 4바이트를 받는다.
        mov     esi, eax    //    4바이트 받아놓은 eax 칸 주소 저장
        mov     edi, OFFSET FLAT:.LC2    //    2번째 문자열
        mov     eax, 0    //    eax 칸에 받은 비트를 0번째 비트부터 하나씩 읽기
        call    printf    //    printf 함수로 출력
        mov     eax, 0    //    eax 칸에 받은 비트를 0번째 비트부터
        leave    //    leave 함수
        ret    //    함수 끝
