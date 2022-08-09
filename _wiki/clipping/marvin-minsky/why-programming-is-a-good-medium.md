---
layout  : wiki
title   : WHY PROGRAMMING IS A GOOD MEDIUM FOR EXPRESSING POORLY UNDERSTOOD AND SLOPPILY­FORMULATED IDEAS by Marvin Minsky
summary : 제대로 이해되지 않고 형식화된 아이디어를 표현할 때 프로그래밍이 좋은 수단인 이유 - 마빈 민스키
date    : 2022-08-06 11:15:12 +0900
updated : 2022-08-10 00:48:57 +0900
tag     : 번역
toc     : true
public  : true
parent  : [[/clipping]]
latex   : true
---
* TOC
{:toc}

- 원문: [WHY PROGRAMMING IS A GOOD MEDIUM FOR EXPRESSING POORLY UNDERSTOOD AND SLOPPILY­FORMULATED IDEAS]( https://web.media.mit.edu/~minsky/papers/Why%20programming%20is--.html )

이 글은 마빈 민스키의 1967년 글을 번역한 것입니다.
의역이 많으므로 원문과 대조해가며 읽기를 권합니다.

## WHY PROGRAMMING IS A GOOD MEDIUM FOR EXPRESSING POORLY UNDERSTOOD AND SLOPPILY­FORMULATED IDEAS

>
This is a slightly revised version of a chapter published in _Design and Planning II -- Computers in Design and Communication_, (Martin Krampen and Peter Seitz, eds.), Visual Committee Books, Hastings House Publishers, New York, 1967.

이 글은 1967년에 출간된 Design and Planning II -- Computers in Design and Communication 의 한 챕터를 약간 수정한 것입니다.

>
_There is a popular, widespread belief that computers can do only what they are programmed to do.
This false belief is based on a confusion between form and content.
A rigid grammar need not make for precision in describing processes.
The programmer must be very precise in following the computer grammar, but the content he wants to be expressed remains free.
The grammar is rigid because of the programmer who uses it, not because of the computer.
The programmer does not even have to be exact in his own ideas‑he may have a range of acceptable computer answers in mind and may be content if the computer's answers do not step out of this range.
The programmer does not have to fixate the computer with particular processes.
In a range of uncertainty he may ask the computer to generate new procedures, or he may recommend rules of selection and give the computer advice about which choices to make.
Thus, computers do not have to be programmed with extremely clear and precise formulations of what is to be executed, or how to do it._

컴퓨터는 프로그래밍된 작업만 수행할 수 있다는 믿음이 널리 펴져 있습니다.
이 잘못된 믿음은 형식<sub>form</sub>과 내용<sub>content</sub>을 혼동하는 데에서 비롯됐습니다.
아무리 문법이 엄격하다 해도 프로세스를 기술할 때의 정확성까지 보장해주지는 않습니다.
프로그래머는 컴퓨터 문법을 매우 정확하게 따라야 하지만, 의도하는 내용<sub>content</sub>은 얼마든지 자유롭게 표현할 수 있는 셈이죠.

딱딱한 것은 문법이며, 문법이 엄격한 이유는 문법을 사용하는 프로그래머 때문입니다. 컴퓨터 때문이 아닙니다.
프로그래머는 아이디어를 아주 정확하게 가다듬지 않아도 됩니다.
컴퓨터의 응답 범위를 적절히 생각해두고 컴퓨터의 응답이 이 범위를 벗어나지 않으면 만족하는 것이 프로그래머입니다.
프로그래머는 특정 프로세스에 맞춰 컴퓨터를 고정해놓고 사용하지 않아도 됩니다.
문제가 불확실한 영역에 있다면 프로그래머는 컴퓨터에게 새로운 절차<sub>procedures</sub>를 생성하도록 요청하면 그만입니다.
아니면 선택 규칙을 추천해주는 식으로 어떤 선택을 해야 하는지에 대해 컴퓨터에게 알려주는 방법도 있습니다.

즉, 컴퓨터는 무엇을 어떻게 실행해야 하는지에 대해 극도로 명확하고 정확한 공식을 통해 프로그래밍하지 않아도 되는 것입니다.

### =====

>
The argument presented here is not specifically about "design," but about the general question of what we can get computers to help us do.
For a number of reasons, it is customary to underestimate the possibilities.
To begin, I want to warn against the pitfall of accepting the apparently "moderate" positions taken by many people who believe they understand the situation.
Science‑fiction writers, scientists of all descriptions, economic forecasters, psychologists, and even logicians tell us often, and make it a convincing tale, that computers will never really think.
_"We must not fall into anthropomorphic ways of thinking about machines; they do only what their programs say; they can't be original or creative."_
We have all heard these views, and most of us accept them.

여기에서 말하고자 하는 바는 구체적으로 "설계<sub>design</sub>"에 대한 것이 아닙니다.
우리가 컴퓨터를 사용해서 무엇을 할 수 있는가라는 광범위한 질문이 우리의 주제라 할 수 있습니다.

일반적으로 여러가지 이유로 컴퓨터의 가능성은 과소평가되고 있습니다.
그래서 나는 일단 겉보기에 "온건해 보이는" 입장을 받아들이는 것의 함정을 경고하면서 이야기를 시작하고 싶습니다.
상황을 이해한다고 생각하는 많은 사람들이 취하는 입장이죠.
SF 작가라던가, 온갖 분야의 과학자, 경제 예측가, 심리학자, 심지어 논리학자들도 진지한 논조로 컴퓨터가 실제로는 절대로 생각을 못하는 기계라고 이야기하곤 합니다.
*"기계를 의인화하는 사고 방식에 빠지면 안됩니다. 기계는 프로그램된 대로만 작동하며 스스로 독창적일 수 없고, 창의적이지도 않습니다."*
이런 말을 안 들어본 사람은 없겠죠. 대다수의 사람들은 이런 의견을 무비판적으로 받아들입니다.

>
It is easy to understand why a humanist will want to rhapsodize about the obscurity of thought processes, for there is an easy non sequitur between that obscurity and the desired an anthropomorphic uniqueness.
But this isn't the non sequitur important here.
The fallacy under discussion is the widespread superstition that we can't write a computer program to do something unless one has an extremely clear, precise formulation of what is to be done, and exactly how to do it.
This superstition is propagated at least as much by scientists—and even by "computer scientists"—as by humanists.

사고의 프로세스의 난해함에 대해 인문주의자들이 이렇게 강하게 이야기하고 싶어하는 이유를 이해하는 것은 간단합니다.
이런 종류의 의인화는 다른 곳에서 찾아볼 수 없는 독특한 것이므로, 이 주제의 난해함과 구분해서 생각하기가 쉽지 않기 때문입니다.

그러나 이런 것은 이 글에서 중요한 논점이 아닙니다.
우리가 따져보고 있는 문제는, *"수행할 작업과 수행하는 방법에 대해 아주 명확하고 정확한 공식이 없으면 컴퓨터 프로그램을 만들어서 돌릴 수 없다"* 는 엄청 유명한 미신입니다.
이 미신은 과학자들은 물론이고 심지어 "컴퓨터 과학자"들에게도 인문주의자들만큼이나 퍼져 있습니다.

>
What we are told, about the limitations of computers, usually takes this general form:
"A computer cannot create. It can do only exactly what it is told. Unless a process is formulated with perfect precision, you cannot make a computer do it."
Now this is perfectly true in one sense, and it is absolutely false in another.
Before explaining why, it is interesting to note that ‑ long before computers ‑ the same was said of the Devil: he could only appear to be creative.

우리 귀에 들려오곤 하는 컴퓨터의 한계에 대한 이야기는 보통 이런 식입니다.
*"컴퓨터는 스스로 창조하지 못합니다. 컴퓨터는 그냥 시키는 것만 할 수 있습니다. 완벽한 정밀도로 공식화한 프로세스를 주지 않으면 컴퓨터는 돌아가지 않을 겁니다."*

오늘날의 관점에서 이 말은 어떤 의미에서는 완벽하게 사실이기도 하지만, 한편으로는 절대적으로 거짓이기도 합니다.
왜 그런지 이유를 설명하기 전에 문득... 컴퓨터가 등장하기 한참 전에 악마에 대해서도 똑같은 말이 있었다는 것이 무척 흥미롭게 느껴집니다. 악마는 창조력을 갖고 있는 것처럼 보이지만 실제로는 그렇지 않다는 거요.

>
In the September 1966 issue of Scientific American, I discussed three programs: one is the checkers program of Samuel, which plays at the master level.
Another is the ANALOGY program of Evans, which does rather well on certain intelligence‑test problems of recognizing analogous relations between geometric figures.
The third is the program "STUDENT" of Bobrow, which takes high school algebra "story" problems given in English:
> > Mary is twice as old as Ann was when Mary was as old as Ann is now. If Mary is 24 years old, how old is Ann?
>
and solves some, but not all of them.
In that article I was concerned with problems of going further, to extend such work in the direction of more versatile general intelligence.
But for my purpose here, they can serve as adequate examples even in their present state, for while limited in what they can handle, they already do enough to confound the old comfortable superstitions.

Scientific American 1966년 9월호에서 나는 세 가지 프로그램에 대해 논의한 바 있습니다.
하나는 마스터 수준의 실력을 보이는 Samuel의 체커 프로그램입니다.
다른 하나는 Evans의 ANALOGY 프로그램인데, 기하학적 도형들 사이의 유사성을 인식하는 종류의 지능 테스트 문제를 상당히 잘 풀어냅니다.
그리고 세 번째는 영어로 된 "이야기" 형식의 고등학교 대수 문제를 푸는 Bobrow의 "STUDENT" 프로그램입니다. 이런 식이죠.

**"메리의 나이는 메리가 앤의 현재 나이였을 때의 두 배입니다. 메리가 24세라면, 앤은 현재 몇 살입니까?"**

이 프로그램은 문제를 제법 풀긴 하지만 모든 문제를 잘 풀어내지는 않습니다.
그 글에서 내가 표현하려 한 주제는 다재다능한 일반 지능으로의 발전에 대한 것이었습니다만,
이 프로그램들은 미신을 타파하겠다는 이 글의 목적에도 적합한 예제가 될 수 있을 것 같습니다.
왜냐하면 이 프로그램들이 제한적인 대상을 취급하긴 하지만 오랫동안 받아들여진 미신을 뒤흔들기에는 충분할 것으로 보이기 때문입니다.

>
The old view is that a program is "nothing but" a set of rigid rules for exactly what to do in each situation.
This is indeed a useful point of view for reassuring beginners at programming, or for analyzing the programs written by beginners.
However, for more advanced processes, while "perfectly" true in one sense, it would be as correct to say that "houses are nothing but arrangements of construction materials" or "books are merely long strings of words."
Indeed, a review of my Scientific American article (in Computer Reviews 8, 1, Jan. 1967) asserts that these programs are made of "dictionary lookup routines, sequences of search and comparison functions, and sort-merge type operations."

프로그램에 대한 고리타분한 관점 중 하나는 프로그램이 "아무것도 아니며<sub>nothing but</sub>" 단지 각각의 상황에서 정확히 무엇을 해야 하는지에 대한 엄격한 규칙을 모아놓은 집합이라는 것입니다.
이 관점은 프로그래밍 초보자를 안심하게 해주는 효능을 갖고 있고, 초보자가 작성한 프로그램을 분석할 때에 한해서는 유용하기도 합니다.
그러나 고급 프로세스에 대해 논할 때 이 관점은 특정한 의미에서만 "완전히" 사실일 뿐이며 "집은 건설자재들을 배치해 놓은 것에 불과하다", "책은 단순히 단어들을 길게 늘어놓은 것에 불과하다"라고 말하는 것과 다름이 없습니다.

실제로, Scientific American에 실린 나의 글에 대한 어떤 리뷰에서는 프로그램은 "dictionary lookup 루틴, search 및 comparison 함수들의 sequence, sort-merge 타입 연산"들로 구성된다고 말하는 반론을 읽어볼 수 있습니다.

### LOGIC AND CONSISTENCY

**논리와 일관성**

>
Let me begin by discussing one of the skeptical attitudes that is derived from some statements of good logicians and bad philosophers.
We are told that certain theorems about proving the self‑consistency of logical systems have the consequence:
"It is impossible to mechanize completely the process of discovery and therefore humans will always have the advantage over machines."
I am sure almost every reader has heard of Godel's theorem, and most have heard of this alleged consequence.
But this is not a logical consequence, for it is based on a careless technical oversight.
If applicable at all to the problem‑solving question, Godel's theorem applies strictly only to perfectly self‑consistent logical systems.
People are not this consistent, and there is no reason whatever why we should feel constrained to build our machines along such lines.
Instead we can, and already do, build machines that can tolerate contradictory factual assertions.
To do this, we have to add selection rules for resolving contradictions, priority hierarchies for choosing between incompatible statements, and the like.
A simple example of such a scheme is described in Bertram Raphael's 1964 MIT PhD dissertation.
Here is an example of a dialog with that program:
>
> ```
> →       EVERY BOY IS A PERSON
> (I UNDERSTAND)
> →       A FINGER IS PART OF A HAND
> (I UNDERSTAND)
> →       EACH PERSON HAS TWO HANDS
> THE ABOVE SENTENCE IS AMBIGUOUS •• PLEASE REPHRASE IT)
> →       THERE ARE TWO HANDS ON EACH PERSON
> (I UNDERSTAND)
> →       HOW MANY FINGERS DOES JOHN HAVE?
> (I DON'T KNOW WHETHER FINGER IS PART OF JOHN)
> →       JOHN IS A BOY
> (I UNDERSTAND)
> →       HOW MANY FINGERS DOES JOHN HAVE?
> (HOW MANY FINGERS PER HAND?)
> →       EVERY HAND HAS 5 FINGERS)
> (I UNDERSTAND)
> →       HOW MANY FINGERS DOES JOHN HAVE?
> (THE ANSWER IS 10)
> →       HOW MANY AUTOMOBILES DOES JOHN HAVE?
> THE ABOVE SENTENCE IS AMBIGUOUS. PLEASE RE-PHRASE IT)
> →       WHO IS PRESIDENT OF THE UNITED STATES?)
> (STATEMENT FORM NOT RECOGNIZED)
> →       THE B0Y IS JUST TO THE LEFT OF THE TABLE
> (G02840 IS A TABLE)
> (I UNDERSTAND)
> →       THE LAMP IS JUST TO THE LEFT OF THE TABLE
> (G02841 IS A LAMP)
> (THE ABOVE STATEMENT IS IMPOSSIBLE)
> →       THE TABLE IS TO THE RIGHT OF THE CHAIR
> (G02842 IS A CHAIR)
> (I UNDERSTAND)
> →       WHAT IS THE RELATIVE POSITION OF A PERSON?
> (THE LEFT-TO-RIGHT ORDER IS AS FOLLOWS)
> (CHAIR BOY TABLE))
> ```

좋은 논리학자와 나쁜 철학자의 몇 가지 발언에서 유래된 회의적인 태도 중 하나를 논의하는 것으로 시작해보죠.

논리 시스템의 자기 일관성을 증명하는 것에 대한 어떤 정리는 *"발견 과정을 완전히 기계화하는 것은 불가능하다. 그러므로 인간은 항상 기계보다 우수하다"* 는 결론을 내렸다고 합니다.
나는 이 글을 읽는 독자 대부분이 괴델의 정리를 들어본 적이 있고 이런 주장에 대해서도 들어본 적이 있을 거라고 확신합니다. 이 주장은 기술적으로 부주의하게 간과한 면이 있죠. 그래서 논리적인 결론이라 할 수 없습니다.

만약 problem‑solving 문제에 적용한다 치면 괴델의 정리는 완벽히 자기 모순이 없는 논리 시스템에만 엄격하게 적용할 수 있습니다.
그러나 인간은 그렇게까지 일관성을 갖는 존재가 아니며, 우리가 굳이 그런 까다로운 제약에 따라 기계를 만들어야 할 이유도 없습니다.
그래서 그렇게 모순 없는 것을 만드는 대신에 우리는 모순되는 주장들을 수용하는 것이 가능한 기계를 만들 수 있으며, 이미 실제로 그렇게 하고 있습니다.
이것이 가능하려면 모순들을 해결하기 위한 선택 규칙과 호환되지 않는 선언들에 적용할 우선순위를 규칙 등을 추가해야 합니다.

1964년 Bertram Raphael의 MIT 박사 논문에 이런 설계의 간단한 예가 나와 있습니다.
다음은 그 프로그램의 대화 예제입니다.


```
→       모든 소년은 사람이다
(알겠습니다)
→       손가락은 손의 일부이다
(알겠습니다)
→       사람은 두 개의 손을 갖고 있다
위의 문장은 모호합니다 .. 다시 말해 주십시오)
→       각각의 사람들은 두 개의 손을 갖고 있다
(알겠습니다)
→       JOHN은 손가락을 몇 개 갖고 있는가?
(손가락이 JOHN의 일부인지 아닌지 모르겠습니다)
→       JOHN은 소년이다
(알겠습니다)
→       JOHN은 손가락을 몇 개 갖고 있는가?
(손 하나에는 몇 개의 손가락이 있습니까?)
→       모든 손은 다섯개의 손가락을 갖는다)
(알겠습니다)
→       JOHN은 손가락을 몇 개 갖고 있는가?
(답은 10 입니다)
→       JOHN은 자동차를 몇 대 갖고 있는가?
위의 문장은 모호합니다. 다시 말해 주십시오)
→       미국 대통령은 누구인가?)
(질문 형식을 인식할 수 없음)
→       소년은 테이블 바로 왼쪽에 있다
(G02840은 테이블입니다)
(알겠습니다)
→       램프는 테이블 바로 왼쪽에 있다
(G02841은 램프입니다)
(위의 설명은 불가능합니다)
→       테이블은 의자의 오른쪽에 있다
(G02842는 의자입니다)
(알겠습니다)
→       사람의 상대적인 위치는?
(THE LEFT-TO-RIGHT ORDER IS AS FOLLOWS)
(왼쪽에서 오른쪽 순서에 따르겠습니다)
(의자 소년 테이블))
```

>
Raphael's knowledge‑collecting, question‑answering system shows how it gives higher priority to particular facts when they conflict with general principles.
This "Exception Principle" is, of course, a rather simple‑minded way to resolve contradictions, and it can be only used when there is a clear difference in level of generality between the statements.
When they are on the same level, the program simply rejects the later statement, as seen here:
>
> ```
> →       THERE ARE 5 FINGERS ON EVERY HAND)
> (I UNDERSTAND)
> →       THERE ARE TWO HANDS ON A PERSON
> (I UNDERSTAND)
> →       A BOY IS A PERSON
> (I UNDERSTAND)
> →       TOM IS A BOY
> (I UNDERSTAND)
> →       DICK IS A BOY
> (I UNDERSTAND)
> →       HARRY IS A BOY
> (I UNDERSTAND)
> →       TOM HAS NINE FINGERS
> (THE ABOVE SENTENCE IS AMBIGUOUS •• BUT I ASSUME (HAS) MEANS (HAS AS PARTS))
> (I UNDERSTAND)
> →       DICK HAS ONE HAND
> (THE ABOVE SENTENCE IS AMBIGUOUS •• BUT I ASSUME (HAS) MEANS (HAS AS PARTS))
> (I UNDERSTAND)
> →       HOW MANY FINGERS DOES TOM HAVE?
> (THE ANSWER IS 9)
> →       HON MANY FINGERS DOES DICK HAVE?
> (THE ANSWER IS 5)
> →       HOW MANY FINGERS DOES HARRY HAVE?
> (THE ANSWER IS 10)
> →       HOW MANY FINGERS DOES JOE HAVE?
> (I DON’T KNOW WHETHER FINGER IS PART OF JOE)
> ```

Raphael의 지식 수집, 질문 응답 시스템은 일반 원칙과 특정한 사실들이 모순될 때 어떤 방식으로 우선 순위를 부여하는지를 보여줍니다.
모순을 해결하기 위한 방법들 중에서 이러한 "예외 원칙"은 상당히 단순한 방법입니다.
명령문들 사이에 일반성 레벨에 확실한 차이가 있는 경우에만 사용할 수 있죠.
명령문들이 같은 레벨에 있다면 프로그램은 아래와 같이 단순하게 나중에 입력된 명령을 거부합니다.

```
→       모든 손에는 다섯 개의 손가락이 있다)
(알겠습니다)
→       사람은 두 개의 손을 갖고 있다
(알겠습니다)
→       소년은 사람이다
(알겠습니다)
→       TOM은 소년이다
(알겠습니다)
→       DICK은 소년이다
(알겠습니다)
→       HARRY는 소년이다
(알겠습니다)
→       TOM은 손가락을 아홉개 갖고 있다
(위의 문장은 모호합니다 .. 그러나 (갖는다)의 의미를 (부분으로 갖는다)로 가정합니다)
(알겠습니다)
→       DICK은 손을 하나 갖고 있다
(위의 문장은 모호합니다 .. 그러나 (갖는다)의 의미를 (부분으로 갖는다)로 가정합니다)
(알겠습니다)
→       TOM의 손가락은 몇 개인가?
(답은 9 입니다)
→       DICK의 손가락은 몇 개인가?
(답은 5 입니다)
→       HARRY의 손가락은 몇 개인가?
(답은 10 입니다)
→       JOE의 손가락은 몇 개인가?
(손가락이 JOE의 일부인지 아닌지 모르겠습니다)
```

>
But of course Raphael could have written some other priority rule.
Incidentally, the program's statement, "The above sentence is ambiguous..." concerns the possibility that the word "has" might mean either "has as a part" or "owns. "
Raphael's program usually guesses correctly by a study of whether the entities in question are already known to own things, or to be parts of things, etc.
I will describe this later in more detail.
Raphael's demonstration that such "contextual" decisions can be programmed, illustrates a more general point, or rather, shows a different and healthier attitude toward programs than the "nothing but" approach.
We will therefore try to explain some of these better ways to think about programs.

물론 Raphael은 다른 방식으로 작동하는 우선순위 규칙을 만들 수도 있었겠지만 그러지 않았습니다.
이 프로그램에서 말하는 *"위의 문장은 모호합니다..."* 는 *"갖는다<sub>has</sub>"* 라는 단어가 *"부분으로 갖는다<sub>has as a part</sub>"* 또는 *"소유한다<sub>owns</sub>"* 는 의미를 포함하고 있을 가능성을 표현하고 있습니다.
즉, Raphael의 프로그램은 문제 속 대상이 일반적으로 무언가를 갖고 있거나, 아니면 다른 무언가의 일부로서 존재하는 것으로 추측하고 있습니다.
이것에 대해서는 나중에 설명하도록 하죠.

너무 일반적인 지점을 묘사하거나 "프로그램이 아무것도 아니라는<sub>nothing but</sub>" 접근방식에 비해, 이와 같이 "맥락을 고려한" 결정 과정이 프로그래밍될 수 있다는 Raphael의 예제는 논증에 있어 훨씬 건강한 태도를 보여주는 사례라 할 수 있겠습니다.
지금부터는 이와 같이 프로그램에 대해 고찰하는 더 나은 방법들을 써서 살펴보도록 하겠습니다.

### (1) A PROGRAM AS A SEQUENCE OF INSTRUCTIONS TO BE OBEYED.

**(1) 프로그램은 준수해야 하는 명령들의 시퀀스이다.**

>
The most common and simple‑minded view is that a computer program is a sequence of clear-cut operations to be performed on some data.
Let's take a simple example of a program: suppose that X is a number given as input:

가장 일반적이면서 단순한 관점은 컴퓨터 프로그램이 어떤 데이터에 대해 수행되는 명료한 작업들의 시퀀스라는 것입니다.
이런 프로그램의 간단한 예를 들어보죠. 입력으로 `X`라는 숫자가 주어졌다고 합시다.

```
START: SET R = 1
LOOP:   SET S = X/R
        SET T=R+S
        SET R = T/2
        SET U = R x R
        SET V = X - U
        IF |V| > .001, GO TO LOOP
        ELSE PRINT V
```

>
This program (attributed to Isaac Newton) will compute an approximation to the square root of X.
At each line in the program it is perfectly clear what is the current status of things, and what is to be done next.
Of course, it requires a mathematical analysis, to show that the sequence of situations so developed will eventually lead to an acceptable value of R, and terminate the computation.'
So there is no great harm in thinking of these statements as a sequence of steps.
The "GO TO" instruction might be considered to be a super‑abbreviation for several more copies of the "main loop."
Of course, until the analysis is made, one should think of the program as an expression of a useful but poorly understood idea.

아이작 뉴턴이 만든 이 프로그램은 `X`의 제곱근의 근사값을 계산합니다.
이 프로그램의 각 라인은 현재 상태와 다음에 수행해야 할 작업을 완전히 명확하게 표현하고 있습니다.
물론 이렇게 진행되는 상태의 시퀀스가 허용 가능한 R 값으로 귀결되며 계산 과정이 종료된다는 것을 보여주기 위해서는 수학적 분석이 필요하긴 하지만, 이런 명령문들의 나열이라면 단계적인 시퀀스로 생각해도 별다른 문제는 없습니다.
"GO TO" 명령도 "main loop"의 다양한 변형 중 하나로 간주할 수 있죠.

분석이 필요하다는 문제가 있긴 하지만 이 관점에서는 프로그램은 이해하기는 좀 어려워도 유용한 아이디어를 표현하는 것이라 생각할 수 있습니다.

### (2) A PROGRAM AS A COURT OF LAW

**(2) 프로그램은 법원이나 다름없다**

>
In Raphael's program, it has to be decided whether "has" means "owns" or "has as parts" when a statement of the form "x has y" is encountered:
>
> ```
> →     JOHN IS A PERSON)
> (I UNDERSTAND)
> →     DICK IS A PERSON)
> (I UNDERSTAND)
> →     A CHAIN IS PART OF A BICYCLE
> (I UNDERSTAND)
> →     THE POWER-SAW HAS A CHAIN
> (THE ABOVE SENTENCE IS AMBIGUOUS •• BUT I ASSUME (HAS) MEANS (HAS AS PARTS))
> (I UNDERSTAND)
> →     JOHN OWNS A CHAIN
> (I UNDERSTAND)
> →     DICK HAS A CHAIR
> (THE ABOVE SENTENCE IS AMBIGUOUS •• BUT I ASSUME (HAS) MEANS (HAS AS PARTS))
> →     THE CUCKOO-CLOCK HAS A CHAIN
> (THE ABOVE SENTENCE IS AMBIGUOUS •• PLEASE REPHRASE IT)
> ```

Raphael의 프로그램은 "x가 y를 갖는다"라는 형태의 명령에 대해 "갖는다<sub>has</sub>"가 "소유한다<sub>own</sub>"를 의미하는지, "부분으로 갖는다<sub>has as parts</sub>"를 의미하는지 결정해야 합니다.

```
→     JOHN은 사람이다)
(알겠습니다)
→     DICK은 사람이다)
(알겠습니다)
→     체인은 자전거의 일부이다
(알겠습니다)
→     전기톱은 체인을 갖고 있다
(위의 문장은 모호합니다 .. 그러나 (갖는다)의 의미를 (부분으로 갖는다)로 가정합니다)
(알겠습니다)
→     JOHN은 체인을 소유한다
(알겠습니다)
→     DICK은 의자를 갖고 있다
(위의 문장은 모호합니다 .. 그러나 (갖는다)의 의미를 (부분으로 갖는다)로 가정합니다)
→     뻐꾸기 시계는 체인을 갖고 있다
위의 문장은 모호합니다 .. 다시 말해 주십시오)
```

>
The problem, when recognized, is transmitted to a part of the program that is able to review all that has happened before.
This sub‑program makes its decision on the following basis:
- _(1) Is y already known to be part of some other thing? Or is y a member of some set whose members are known to be parts of something?_
- _(2) Is y known to be owned by something, or is it a member of some set whose members are known to be owned by something?_
- _(3) If exactly one of (1) or (2) is true, make the choice in the corresponding direction. If neither holds, give up and ask for more information. If both are true, then consider the further possibilities at (4) below. (Thus the program uses evidence about how previously acquired information has been incorporated into its "model" of the world.)_
- _(4) If we get to this point, then y is known already to be involved in being part of something and in being owned and we need a finer test._

인식된 문제는 이전에 발생한 모든 것을 검토하는 서브 프로그램으로 전달됩니다.
이 서브 프로그램은 다음 규칙에 따라 결정을 내립니다.

- (1) `y`는 다른 것의 일부로 알려져 있는 것인가? 아니면 `y`는 다른 무언가의 일부로 구성된 집합의 원소인가?
- (2) `y`는 어떤 것의 소유물로 알려져 있는가? 아니면 무언가의 소유물로 이루어진 어떤 집합의 원소인가?
- (3) 만약 (1) 이나 (2) 중 하나만 참이라면 해당 방향으로 선택한다.
    - 만약 둘 다 거짓이라면, 처리를 포기하고 더 많은 정보를 얻기 위해 질문을 한다.
    - 만약 둘 다 참이라면, 아래의 (4)를 통해 다른 가능성을 고려한다. (이렇게 하여 프로그램은 앞에서 획득한 정보가 세계의 "모델"에 어떻게 통합되었는지에 대한 증거로 사용합니다.)
- (4) 여기까지 왔다면, `y`는 이미 알려진 무언가의 일부이며 소유된 상태라는 것을 알게 되므로 더 정밀한 테스트가 필요하다.

>
Let $$U_1$$ and $$U_2$$ be the "something" or the "some set" that we know exists, respectively, in the answers to questions (1) and (2).
These depend on‑ y.
We now ask: is x a member of, or a subject of $$U_1$$ or $$U_2$$?
If neither, we give up.
If one, we choose the corresponding result‑"part of" or "owns."
If both, we again give up and ask for more information. As Raphael says:

질문 (1)과 질문 (2)의 답변에 사용되는 우리가 알고 있는 "무언가" 내지 "어떤 집합"이 $$U_1$$과 $$U_2$$ 라고 생각해 봅시다.
이것들은 `y`에 따라 달라지겠죠.
그래서 **`x`는 $$U_1$$ 또는 $$U_2$$ 의 원소인가?** 라고 질문하게 됩니다.
만약 둘 다 아니라면 처리를 포기합니다.
만약 둘 중 하나라면 해당하는 결과, 즉 "일부" 또는 "소유"를 선택하게 됩니다.
만약 둘 다라면 우리는 추가 정보를 얻기 위해 질문을 하게 됩니다.

이에 대해 Raphael은 다음과 같이 말합니다.

>
_"These criteria are simple, yet they are sufficient to enable the program to make quite reasonable decisions about the intended purpose in various sentences of the ambiguous word "has."
Of course, the program can be fooled into making mistakes, e.g., in case the sentence, "Dick has a chain," had been presented before the sentence, "John owns a chain," in the above dialogue.
However, a human being exposed to a new word in a similar situation would make a similar error.
The point here is that it is feasible to automatically resolve ambiguities in sentence meaning by referring to the descriptions of the words in the sentence‑descriptions which can automatically be created through proper prior exposure to unambiguous sentences."_

"이 기준은 심플하긴 하지만 다양한 문장에서 모호하게 사용되는 "갖는다<sub>has</sub>"라는 단어가 사용된 의도를 판별하는 데에 충분히 합리적인 결정을 내릴 수 있게 해줍니다.
물론, 프로그램은 속아서 실수를 저지를 수도 있습니다.
예를 들어 위의 예제에서 "John은 체인을 소유한다" 앞에 "Dick은 체인을 갖는다"는 문장이 먼저 제시되는 상황 같은 거죠.
그러나 인간도 비슷한 상황일 때 새로운 단어를 접하게 되면 비슷한 오류를 저지르게 됩니다.
여기에서 핵심은 명확한 문장을 적절히 미리 노출시킬 수 있다면, 단어에 대한 설명을 자동으로 생성 가능할 것이고, 이런 설명을 참조하여 문장 의미의 모호함을 자동으로 해결할 수 있다는 것입니다."

