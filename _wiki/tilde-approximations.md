---
layout  : wiki
title   : 틸다 근사 (Tilde approximations)
summary : 틸다 표기법
date    : 2020-05-31 18:35:05 +0900
updated : 2020-05-31 20:08:26 +0900
tag     : algorithm
resource: 88/EF8C7D-9A37-4CCA-AF05-3226BEB9A5BD
toc     : true
public  : true
parent  : [[algorithm]]
latex   : true
---
* TOC
{:toc}

## 정의

> $$ \sim f(N) $$는 임의의 함수 $$f$$에 대하여 $$N$$이 커질수록 $$ \frac{ \sim f(N) }{f(N)} $$의 값이 $$1$$에 수렴하게 하는 함수를 말한다.
>
> 그리고 $$g(N) \sim f(N)$$은 $$N$$이 커질수록 $$ \frac{ g(N) }{ f(N) } $$의 값이 $$1$$에 수렴하는 경우를 말한다.[^sedgewick-181]

틸다 표기법의 특징은 다음과 같다.

- 수식에 `~`를 사용하여 수식을 읽는 사람에게 틸다 근사가 적용되었음을 알린다.
- 수식에서 영향력이 적은 낮은 자리수의 항을 제거하여 간단하게 만든다.

> 틸다 근사 $$ f(N) \sim g(N) $$의 정규적인 수학적 정의는
>
> $$\lim_{ N \to \infty } { f(N) \over g(N) } = 1 $$
>
> 이다.[^sedgewick-205]

- 틸다 근사는 점근 근사의 한 종류이다. [[big-O-notation]]{big O 근사}도 점근 근사에 해당한다.

## 틸다 근사의 예

틸다 근사를 쉽게 표현하자면 다음과 같다.

$$ f(N) = g(N) + \text{ 최고차항이 아닌 항들 } $$


| 함수 $$f(N)$$                                    | 틸다 근사 $$g(N)$$       | big O            |
|--------------------------------------------------|--------------------------|------------------|
| $$ 5N^6 - 3N^2 + N $$                            | $$ \sim 5N^6 $$          | $$ O( N^6 ) $$   |
| $$ \frac{N^3}{6} - \frac{N^2}{2} + \frac{N}{3}$$ | $$ \sim \frac{N^3}{6} $$ | $$ O( N^3 ) $$   |
| $$ \frac{N^2}{2} - \frac{N}{2} $$                | $$ \sim \frac{N^2}{2} $$ | $$ O( N^2 ) $$   |
| $$ \lg N + 1 $$                                  | $$ \sim \lg N $$         | $$ O( \lg N ) $$ |
| $$ 3 $$                                          | $$ \sim 3 $$             | $$ O(1) $$       |
| $$ N + 1 $$                                      | $$ \sim N $$             | $$ O(N) $$       |

예를 들어 $$ \color{red}{3N^2 + 5N} $$ 은 [[big-O-notation]]으로는 $$O( N^2 )$$ 이지만, 틸다 표현법에서는 $$ \color{blue}{\sim 3N^2} $$ 이다.

`3`을 남겨두지 않으면 $$\lim_{N \to \infty}{ \color{red}{3N^2 + 5N} \over \color{blue}{N^2}}$$가 `1` 이 아니라 `3`이 되기 때문이다.

## big O 표기법에 대한 틸다 표기법의 장점

> Q. (위 질문에 이어서) 점근적인 성능에 있어서 그 상한은 중요하지 않나?
>
> 중요하다. 하지만 구문의 실행 빈도 관점에서의 정확한 값이 반영된 비용모델을 더 선호한다.
왜냐하면 그것이 알고리즘의 성능에 대해 더 많은 정보를 주고,
이 책에서 다루는 알고리즘들은 정확한 실행 빈도를 구해낼 수 있는 수준이기 때문이다.
예를 들어 "ThreeSum은 $$\sim N^3 / 2$$번의 배열 접근을 한다"
그리고 "ThreeSum에서 `cnt++`가 수행되는 최악 조건 횟수는 $$\sim N^3/6$$이다"라고 기술하면
다소 번거롭기는 하지만 "ThreeSum의 실행 시간은 $$O(N^3)$$이다"라고 하는 것보다 **훨씬 더 풍부한 정보를 제공한다**.
[^sedgewick-206]

참고로 위의 인용에서 말하는 ThreeSum의 코드는 다음과 같다.

```java
/**
 * 합계가 0이 되는 트리플을 카운팅하여 리턴한다.
 *
 * @param numbers 입력 숫자 배열
 * @return
 */
public static int count(int[] numbers) {
  int N = numbers.length;
  int cnt = 0;
  for (int i = 0; i < N; i++) {
    for (int j = i + 1; j < N; j++) {
      for (int k = j + 1; k < N; k++) {
        // 이 if 구문은 정확히 N(N-1)(N-2)/6 회 실행된다.
        if (numbers[i] + numbers[j] + numbers[k] == 0) {
          cnt++;
        }
      }
    }
  }
  return cnt;
}
```

## 함께 읽기

- [[big-O-notation]]

## 참고문헌

- 알고리즘 [개정4판] / 로버트 세지윅, 케빈 웨인 저/권오인 역 / 길벗 / 초판발행 2018년 12월 26일

## 주석

[^sedgewick-181]: 알고리즘 [개정4판]. 1.4장. 181쪽.
[^sedgewick-205]: 알고리즘 [개정4판]. 1.4장. 205쪽.
[^sedgewick-206]: 알고리즘 [개정4판]. 1.4장. 206쪽.

