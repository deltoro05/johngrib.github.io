---
layout  : wiki
title   : Clojure Special Forms
summary : 번역 중인 문서
date    : 2022-05-05 23:15:05 +0900
updated : 2022-05-07 11:36:52 +0900
tag     : clojure 번역
toc     : true
public  : true
parent  : [[/clojure/reference]]
latex   : false
---
* TOC
{:toc}

- 원문: [Special Forms]( https://clojure.org/reference/special_forms )

## Special Forms: Clojure Reference 문서 번역

>
Special forms have evaluation rules that differ from standard Clojure evaluation rules and are understood directly by the Clojure compiler.
>
Headings for the special forms informally describe the special form grammar using regular expression syntax: ? (optional), * (0 or more), and + (1 or more). Non-terminals are denoted by italics.

Special form은 일반적인 Clojure evaluation과는 다른 규칙이 적용되며, Clojure compiler에서 직접 처리합니다.

- 이 문서의 소제목들은 special form의 문법을 개략적으로 보여주며, 정규식의 `?`, `*`, `+`를 사용해서 반복을 표현합니다.

### (`def` symbol doc-string? init?)

>
Creates and interns or locates a global [var]( https://clojure.org/reference/vars ) with the name of _symbol_ and a namespace of the value of the current namespace (`*ns*`).
If _init_ is supplied, it is evaluated, and the root binding of the var is set to the resulting value.
If _init_ is not supplied, the root binding of the var is unaffected.
 `def` always applies to the root binding, even if the var is thread-bound at the point where `def` is called.
 `def` yields the var itself (not its value).
Throws an exception if _symbol_ is already in the namespace and not mapped to an interned var.
Support for _doc-string_ was added in Clojure 1.3.

`symbol` 이름과 "현재 네임스페이스(`*ns*`)"를 사용해서 global var를 생성하고 intern 처리합니다.

- `init`
    - `init`이 주어진다면, `init`을 평가해서 var의 루트 바인딩에 할당합니다.
    - `init`이 없다면, var의 루트 바인딩은 아무런 영향을 받지 않습니다.
        - 역주: init이 없는 def 표현식인 `(def foo)`를 평가하고 나서 `foo`를 평가해 보면 `Unable to resolve symbol: foo in this context`가 발생한다.
- `def`
    - `def`는 언제나 루트 바인딩에 적용됩니다. var가 스레드 바인딩되었을 때 `def`가 호출되어도 마찬가지입니다.
    - `def`는 var 자체를 반환합니다(var의 값이 아니라 var 자체).

만약 `symbol`이 이미 네임스페이스에 존재하고, intern된 var에 매핑되지 않았다면 예외가 던져집니다.

`doc-string`은 Clojure 1.3 부터 지원되었습니다.

>
Any metadata on the _symbol_ will be evaluated, and become metadata on the var itself.
There are several metadata keys that have special interpretation:
>
- `:private`
    - a boolean indicating the access control for the var. If this key is not present, the default access is public (e.g. as if `:private false`).
- `:doc`
    - a string containing short (1-3 line) documentation for the var contents
- `:test`
    - a fn of no args that uses `assert` to check various operations. The var itself will be accessible during evaluation of a literal fn in the metadata map.
- `:tag`
    - a symbol naming a class or a Class object that indicates the Java type of the object in the var, or its return value if the object is a fn.

`symbol`의 모든 메타데이터는 평가를 마친 다음 var 자체의 메타데이터가 됩니다.
이런 메타데이터에는 특별하게 해석되는 다음과 같은 키값들이 있습니다.

- `:private`
    - var에 대한 접근 제어를 나타내는 boolean.
    - 이 키가 없다면 기본값은 `public` 입니다(`:private false`와 같음).
- `:doc`
    - var의 내용에 대한 1~3줄 정도의 짧은 설명 String.
- `:test`
    - `assert`를 사용해 다양한 체크가 가능한 함수.
    - 이 함수는 args가 하나도 없는 `fn` 입니다.
    - 메타데이터 map에서 fn 리터럴을 평가하는 동안 이 함수는 var 자체에 접근 가능합니다.
- `:tag`
    - class 이름에 대한 symbol.
    - 또는 var에 들어있는 객체의 Java 타입을 나타내는 Class 객체.
        - 만약 객체가 fn이라면 해당 fn의 리턴값.

>
In addition the compiler will place the following metadata keys on the var:
>
- `:file` string
- `:line` int
- `:name` simple symbol
- `:ns` namespace in which var is interned
- `:macro` true if var names a macro
- `:arglists` a list of vector(s) of argument forms, as were supplied to defn

다음의 메타데이터는 컴파일러가 var에 추가하는 것입니다.

- `:file` string
- `:line` int
- `:name` 간단한 symbol
- `:ns` var가 intern된 namespace
- `:macro` var가 매크로의 이름을 지정한다면 `true`.
- `:arglists`
    - defn에 지정된 인자들의 form vector.
    - vector의 list가 될 수도 있는데, 함수 오버로딩이 가능하기 때문이다.

>
The var metadata can be used for application-specific purposes as well.
Consider using namespace-qualified keys (e.g. `:myns/foo`) to avoid clashes.

var 메타데이터는 애플리케이션의 목적에 따라 다양하게 사용할 수 있습니다.

키 충돌을 예방하기 위해 네임스페이스에 한정된 키(예: `:myns/foo`)를 사용하는 것도 고려할 수 있습니다.

```clojure
(defn
 ^{:doc "mymax [xs+] gets the maximum value in xs using > "
   :test (fn []
             (assert (= 42  (mymax 2 42 5 4))))
   :user/comment "this is the best fn ever!"}
  mymax
  ([x] x)
  ([x y] (if (> x y) x y))
  ([x y & more]
   (reduce mymax (mymax x y) more)))

user=> (meta #'mymax)
  {:name mymax,
   :user/comment "this is the best fn ever!",
   :doc "mymax [xs+] gets the maximum value in xs using > ",
   :arglists ([x] [x y] [x y & more])
   :file "repl-1",
   :line 126,
   :ns #<Namespace user >,
   :test #<user$fn__289 user$fn__289@20f443 >}
```

>
Many macros expand into `def` (e.g. `defn`, `defmacro`), and thus also convey metadata for the resulting var from the _symbol_ used as the name.
>
Using `def` to modify the root value of a var at other than the top level is usually an indication that you are using the var as a mutable global, and is considered bad style.
Consider either using binding to provide a thread-local value for the var, or putting a [ref](https://clojure.org/reference/refs ) or [agent](https://clojure.org/reference/agents ) in the var and using transactions or actions for mutation.

많은 매크로가 `def`로 펼쳐지는데(예: `defn`, `defmacro`), 이렇게 하면 이름으로 지정한 symbol의 결과인 var에 대한 메타데이터도 함께 전달됩니다.

`def`를 사용해서 var의 루트 값을 변경하는 것은 나쁜 방식입니다.
var를 변경 가능한 전역변수로 사용하는 것이기 때문입니다.
바인딩을 사용해 var에 스레드 로컬 값을 제공하거나, var에 `ref`나 `agent`를 넣고 트랜잭션을 써서 값을 변경하는 방법을 고려해 보세요.

### (`if` test then else?)

>
Evaluates _test_.
If not the singular values `nil` or `false`, evaluates and yields _then_, otherwise, evaluates and yields _else_.
If _else_ is not supplied it defaults to `nil`.
All of the other conditionals in Clojure are based upon the same logic, that is, `nil` and `false` constitute logical falsity, and everything else constitutes logical truth, and those meanings apply throughout.
 `if` performs conditional tests of boolean Java method return values without conversion to Boolean.
Note that `if` does not test for arbitrary values of java.lang.Boolean, only the singular value `false` (Java’s `Boolean.FALSE`), so if you are creating your own boxed Booleans make sure to use `Boolean/valueOf` and not the Boolean constructors.

- test를 평가합니다.
    - test가 `nil` 이나 `false`가 아니라면 then을 평가하고 그 결과를 반환합니다.
    - test가 `nil` 이나 `false` 라면 else를 평가하고 그 결과를 반환합니다.

Clojure에서 `nil`과 `false`는 논리적 거짓을 의미하며, 그 외의 모든 것들은 논리적 참을 의미합니다.
Clojure의 모든 제어문은 이와 같은 논리를 토대로 작동합니다.

`if`는 boolean을 리턴하는 Java 메소드를 이용해 조건 테스트를 수행합니다.
그러나 리턴값을 Boolean으로 변환하지는 않습니다.
주목할만한 점은 `if`가 java.lang.Boolean의 모든 값(`true`, `false`)을 테스트하지 않는다는 것입니다.
`if`는 `false`(Java의 `Boolean.FALSE`)만을 테스트합니다.
따라서 여러분이 자신만의 boxed Boolean을 만들 필요가 있다면 `Boolean/valueOf`를 사용하시기 바랍니다. `Boolean` 생성자를 사용하는 것은 바람직하지 않습니다.

### (`do` expr*)

>
Evaluates the expressions exprs in order and returns the value of the last.
If no expressions are supplied, returns `nil`.

여러 expr 표현식들을 순서대로 평가하고, 마지막 평가 결과값을 리턴합니다.
만약 평가식이 주어지지 않는다면, `nil`을 리턴합니다.

### (`let` [ binding* ] expr*)

>
_binding_ ⇒ _binding-form_ _init-expr_
>
Evaluates the expressions _expr_s in a lexical context in which the symbols in the _binding-form_s are bound to their respective _init-expr_s or parts therein.
The bindings are sequential, so each _binding_ can see the prior bindings.
The _expr_s are contained in an implicit `do`.
If a _binding_ symbol is annotated with a metadata tag, the compiler will try to resolve the tag to a class name and presume that type in subsequent references to the _binding_.
The simplest _binding-form_ is a symbol, which is bound to the entire _init-expr_:

binding-form에서 선언하는 symbol들로 구성된 어휘적 컨텍스트 내에서 expr 표현식들을 평가합니다.
binding-form들은 각자의 init-expr이나 이전 binding-form에 바인딩될 수 있습니다.

바인딩은 순서대로 이루어지며, 각각의 binding은 이전의 binding들을 바라볼 수도 있습니다.

expr 표현식들은 암묵적으로 `do`로 묶이게 됩니다.

만약 binding symbol에 metadata로 tag가 표시되어 있다면 컴파일러는 클래스 이름으로 tag를 붙이려 시도하고, 다음에 binding을 참조할 때 해당 클래스를 사용하게 됩니다.

가장 단순한 binding-form은 symbol이며, 해당 symbol에 init-expr이 바인딩됩니다.

>
> ```clojure
> (let [x 1
>       y x]
>   y)
> -> 1
> ```
>
See [Binding Forms](https://clojure.org/reference/special_forms#binding-forms ) for more information about binding forms.
>
**Locals created with `let` are not variables. Once created their values never change!**

binding form에 대한 자세한 내용은 [Binding Forms](https://clojure.org/reference/special_forms#binding-forms ) 섹션을 참고하세요.

`let`으로 생성한 Local은 변수(variables)가 아닙니다. 한번 생성되면 값은 절대로 변하지 않습니다!

### (`quote` form)

>
Yields the unevaluated _form_.
>
> ```clojure
> user=> '(a b c)
> (a b c)
> ```
>
Note there is no attempt made to call the function `a`. The return value is a list of 3 symbols.

평가되지 않은 form을 그대로 리턴합니다.

위의 예제에서 함수 `a`는 호출되지 않는다는 점에 주목하세요.
예제의 리턴값은 3개 symbol로 구성된 하나의 list입니다.

### (`var` symbol)

>
The _symbol_ must resolve to a var, and the Var object itself _(not its value)_ is returned.
The reader macro `#'x` expands to `(var x)`.

symbol은 반드시 var로서 확인되, Var 객체 자체가 리턴됩니다(var의 값이 아님).

reader 매크로 `#'x`는 `(var x)`로 펼쳐집니다.

### (`fn` name? [params* ] expr*)
### (`fn` name? ([params* ] expr*)+)

>
_params_ ⇒ _positional-param_\* , or _positional-param_\* & _rest-param_  
_positional-param_ ⇒ _binding-form_  
_rest-param_ ⇒ _binding-form_  
_name_ ⇒ _symbol_
>
Defines a function (fn).
Fns are first-class objects that implement the [IFn interface](https://clojure.github.io/clojure/javadoc/clojure/lang/IFn.html ).
The `IFn` interface defines an `invoke()` function that is overloaded with arity ranging from 0-20.
A single fn object can implement one or more invoke methods, and thus be overloaded on arity.
One and only one overload can itself be variadic, by specifying the ampersand followed by a single _rest-param_.
Such a variadic entry point, when called with arguments that exceed the positional params, collects them in a seq which is bound to, or destructured by, the rest param.
If the supplied args do not exceed the positional params, the rest param will be `nil`.

`fn`은 함수를 정의합니다.
fn은 `IFn` 인터페이스를 구현하는 일급 객체이기도 합니다.

`IFn` 인터페이스는 `invoke()` 함수를 정의하는데, `invoke`는 0개에서 20개까지의 인자를 갖도록 오버로딩되어 있습니다.
하나의 fn 객체는 하나 이상의 invoke 메소드를 구현할 수 있으므로, 오버로딩을 사용할 수 있습니다.

하나의 함수만 정의하거나, 하나의 오버로드 함수만 정의하는 경우에만 `&` 뒤에 rest-param 하나를 붙여서 가변 인자를 사용할 수 있습니다.

함수가 호출될 때 위치가 고정된 인자들보다 많은 인자가 주어지면, 이렇게 넘친 인자들은 seq에 수집되며 이 seq는 rest-param에 바인딩되거나 구조분해에 사용됩니다.

만약 제공된 인자들의 수가 위치가 고정된 인자들의 수를 넘지 않는다면, rest param은 `nil`이 됩니다.

>
The first form defines a fn with a single invoke method.
The second defines a fn with one or more overloaded invoke methods.
The arities of the overloads must be distinct.
In either case, the result of the expression is a single fn object.

- 위의 첫번째 form은 하나의 invoke 메소드를 가진 fn을 정의합니다.
- 두 번째 form은 하나 이상의 오버로드된 invoke 메소드를 가진 fn을 정의합니다.

이렇게 오버로딩된 함수들의 arity들은 반드시 서로 달라야 합니다.

두 방법 모두, 평가 결과는 하나의 fn 객체입니다.

>
The expressions _expr_s are compiled in an environment in which the _params_ are bound to the actual arguments.
The _expr_s are enclosed in an implicit `do`.
If a name _symbol_ is provided, it is bound within the function definition to the function object itself, allowing for self-calling, even in anonymous functions.
If a _param_ symbol is annotated with a metadata tag, the compiler will try to resolve the tag to a class name and presume that type in subsequent references to the binding.

expr 표현식들은 실제 인자들이 params에 바인딩된 환경에서 컴파일됩니다.

expr 표현식들은 암묵적으로 `do` 문으로 감싸집니다.
만약 symbol 이름이 주어진다면, 함수 정의에서 함수 객체 자신으로 바인딩됩니다.
그로 인해 자기 자신을 호출하는 것이 가능해집니다.
이는 익명 함수에서도 가능합니다.
만약 param symbol에 tag 메타데이터가 붙는다면 컴파일러는 tag를 클래스 이름으로 인지하여, 다음에 해당 바인딩을 참조할 때 그 타입을 사용할 것입니다.

> ```clojure
> (def mult
>   (fn this
>       ([] 1)
>       ([x] x)
>       ([x y] (* x y))
>       ([x y & more]
>           (apply this (this x y) more))))
> ```
>
Note that named fns such as `mult` are normally defined with `defn`, which expands into something such as the above.
>
A fn (overload) defines a recursion point at the top of the function, with arity equal to the number of _param_s _including the rest param, if present_.
See [`recur`](https://clojure.org/reference/special_forms#recur ).
>
fns implement the Java `Callable`, `Runnable` and `Comparator` interfaces.

`defn` 매크로를 사용해 `mult`라는 이름을 붙인 여러 fn을 정의하면, 위의 코드와 같이 펼쳐지게 됩니다.

오버로딩되는 fn은 함수의 시작점에서 인자들을 나열하여 recursion point를 정의합니다.
자세한 내용은 [`recur`](https://clojure.org/reference/special_forms#recur) 문서를 참고하세요.

fn은 Java의 `Callable`, `Runnable`, `Comparator` 인터페이스를 구현합니다.

>
**_Since 1.1_**
>
Functions support specifying runtime pre- and post-conditions.
>
The syntax for function definitions becomes the following:

1.1 버전부터 함수는 런타임에 대해 사전/사후 조건을 지정할 수 있으며, 다음 문법을 통해 정의할 수 있습니다.

### (`fn` name? [param* ] condition-map? expr*)
### (`fn` name? ([param* ] condition-map? expr*)+)

>
The syntax extension also applies to `defn` and other macros which expand to `fn` forms.
>
Note: If the sole form following the parameter vector is a map, it is treated as the function body, and not the condition map.
>
The _condition-map_ parameter may be used to specify pre- and post-conditions for a function. It is of the following form:

이 신택스 확장은 `defn`처럼 `fn`으로 펼쳐지는 매크로들에 적용됩니다.

참고: 만약 parameter vector 바로 뒤에 map 하나만 있다면, 그 map은 condition map 이 아니라 함수 본문으로 사용됩니다.

condition map parameter는 다음 형식과 같이 함수의 사전/사후 조건을 지정하는 데에 사용할 수 있습니다.

> ```clojure
> {:pre [pre-expr*]
>  :post [post-expr*]}
> ```
>
where either key is optional.
The condition map may also be provided as metadata of the arglist.

여기에서 `:pre`와 `:post` 키는 선택사항입니다.
condition map은 arglist의 메타데이터로 제공될 수도 있습니다.

>
_pre-expr_ and _post-expr_ are boolean expressions that may refer to the parameters of the function.
In addition, `%` may be used in a _post-expr_ to refer to the function’s return value.
If any of the conditions evaluate to `false` and `*assert*` is true, a `java.lang.AssertionError` exception is thrown.

pre-expr 과 post-expr 은 함수의 parameters를 참조할 수 있는 boolean 표현식입니다.
한편, post-expr 에서는 함수의 리턴값을 참조하기 위해 `%`를 사용할 수 있습니다.
만약 pre-expr 이나 post-expr 중 하나라도 `false`로 평가되고 `*assert*`가 true이면, `java.lang.AssertionError` 예외가 던져집니다.

>
Example:
>
> ```clojure
> (defn constrained-sqr [x]
>     {:pre  [(pos? x)]
>      :post [(> % 16), (< % 225)]}
>     (* x x))
> ```
>
See [Binding Forms](https://clojure.org/reference/special_forms#binding-forms ) for more information about binding forms.

binding forms에 대한 더 자세한 내용은 [Binding Forms](https://clojure.org/reference/special_forms#binding-forms ) 문서를 참고하세요.

### (`loop` [binding* ] expr*)

>
`loop` is exactly like `let`, except that it establishes a recursion point at the top of the loop, with arity equal to the number of bindings.
See [`recur`](https://clojure.org/reference/special_forms#recur ).

`loop`는 루프가 시작하는 곳에 같은 수의 바인딩을 갖는 arity가 있는 재귀 포인트를 생성한다는 것을 제외하면 `let`과 똑같습니다.
자세한 내용은 [`recur`](https://clojure.org/reference/special_forms#recur ) 문서를 참고하세요.

### (`recur` expr*)

>
Evaluates the expressions _expr_s in order, then, in parallel, rebinds the bindings of the recursion point to the values of the _expr_s.
If the recursion point was a `fn` method, then it rebinds the params.
If the recursion point was a [`loop`](https://clojure.org/reference/special_forms#loop ), then it rebinds the `loop` bindings.
Execution then jumps back to the recursion point.
The `recur` expression must match the arity of the recursion point exactly.
In particular, if the recursion point was the top of a variadic fn method, there is no gathering of `rest` args - a single seq (or null) should be passed.
`recur` in other than a tail position is an error.

expr 표현식들을 순서대로 평가합니다. 그리고 그와 동시에 expr의 값들을 재귀 포인트에 다시 바인딩합니다.
- 만약 재귀 포인트가 `fn` 메소드라면, params에 리바인딩됩니다.
- 만약 재귀 포인트가 `loop`라면, `loop` 바인딩에 리바인딩됩니다.

그리고 나면 재귀 포인트로 점프해 돌아간 다음 실행을 계속합니다.

`recur` 표현식은 반드시 재귀 포인트의 arity와 정확히 일치해야 합니다.

만약 재귀 포인트가 가변 인자를 갖는 fn 메소드의 최상단이라면, `rest` 인자는 수집되지 않으며 하나의 seq (또는 null)만이 전달됩니다.

`recur`는 마지막 꼬리 위치에 있어야 합니다. 그렇지 않다면 오류입니다.

>
Note that `recur` is the only non-stack-consuming looping construct in Clojure.
There is no tail-call optimization and the use of self-calls for looping of unknown bounds is discouraged.
 `recur` is functional and its use in tail-position is verified by the compiler.

`recur`는 Clojure에서 스택을 사용하지 않는 유일한 루프 구조입니다.
Clojure에는 tail-call 최적화가 없기 때문에, 임의의 범위를 반복적으 로돌리기 위해 자기 자신을 호출하는 것은 권장하지 않습니다.
`recur`은 함수적인 방법이면서 꼬리 위치에서 사용할 때에도 컴파일러의 지원을 받을 수 있습니다.

```clojure
(def factorial
  (fn [n]
    (loop [cnt n acc 1]
       (if (zero? cnt)
            acc
          (recur (dec cnt) (* acc cnt))))))
```

### (`throw` expr)

>
The _expr_ is evaluated and thrown, therefore it should yield an instance of some derivee of `Throwable`.

expr을 평가한 다음 던집니다. 즉, expr은 `Throwable`를 구현하는 인스턴스여야 합니다.

### (`try` expr* catch-clause* finally-clause?)

>
_catch-clause_ → (catch _classname_ _name_ _expr_\*)  
_finally-clause_ → (finally _expr_\*)
>
The _expr_s are evaluated and, if no exceptions occur, the value of the last expression is returned.
If an exception occurs and _catch-clause_s are provided, each is examined in turn and the first for which the thrown exception is an instance of the _classname_ is considered a matching _catch-clause_.
If there is a matching _catch-clause_, its _expr_s are evaluated in a context in which _name_ is bound to the thrown exception, and the value of the last is the return value of the function.
If there is no matching _catch-clause_, the exception propagates out of the function.
Before returning, normally or abnormally, any _finally-clause_ _expr_s will be evaluated for their side effects.

expr을 평가하는 도중에 예외가 발생하지 않았다면 마지막 표현식의 값을 리턴합니다.

catch-clause가 주어졌을 때 예외가 발생했다면, 예외 인스턴스와 매치되는 classname을 가진 첫 번째 catch-clause를 찾습니다.
매치되는 catch-clause를 찾았다면, 던져진 예외에 대해 name이 바인딩된 컨텍스트에서 catch-clause의 expr이 평가되며 이렇게 평가된 마지막 값이 함수의 리턴값이 됩니다.

만약 매치되는 catch-clause가 없다면, 예외는 함수 바깥으로 전파됩니다.

예외가 발생하건 발생하지 않건 간에, 값을 리턴하기 전에는 사이드 이펙트로 finally-clause expr이 평가됩니다.

### (`monitor-enter` expr)
### (`monitor-exit` expr)

## 참고문헌

- [Special Forms]( https://clojure.org/reference/special_forms )

