한국어 Abstract Meaning Representation (AMR) 가이드라인 1.0
=============================
***Korean Abstract Meaning Representation (AMR) Specification 1.0***

+ **Documentized: August 30, 2019**
+ **Released: October 11, 2019**

***최현수, 한지윤, 박혜진, 오태환, 박석원, 김한샘,***
*김미경, 김영상, 노영빈, 류보람, 이보미, 장연지, 정진경, Fei Li*

***Hyonsu Choe\*, Jiyoon Han, Hyejin Park, Taehwan Oh, Seokwon Park, Hanseam Kim*** *|* *Institute of Language and Informatics Studies, Yonsei University* *(Maintained by\*)*

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

  - [*Disclaimer & dependencies*](#disclaimer--dependencies)
- [I. 서론 (Introduction)](#i-%EC%84%9C%EB%A1%A0-introduction)
  - [예시 (Example)](#%EC%98%88%EC%8B%9C-example)
  - [언어로부터의 추상화 (Abstraction away from language)](#%EC%96%B8%EC%96%B4%EB%A1%9C%EB%B6%80%ED%84%B0%EC%9D%98-%EC%B6%94%EC%83%81%ED%99%94-abstraction-away-from-language)
  - [통사적이기보다는 더 논리적인 표상 (More Logical than Syntax)](#%ED%86%B5%EC%82%AC%EC%A0%81%EC%9D%B4%EA%B8%B0%EB%B3%B4%EB%8B%A4%EB%8A%94-%EB%8D%94-%EB%85%BC%EB%A6%AC%EC%A0%81%EC%9D%B8-%ED%91%9C%EC%83%81-more-logical-than-syntax)
  - [초점 (Focus)](#%EC%B4%88%EC%A0%90-focus)
  - [AMR 강령 (AMR slogans)](#amr-%EA%B0%95%EB%A0%B9-amr-slogans)
  - [English AMR 1.2의 한계 (Limitations of AMR 1.2)](#english-amr-12%EC%9D%98-%ED%95%9C%EA%B3%84-limitations-of-amr-12)
    - [한국어 AMR 가이드라인의 한계](#%ED%95%9C%EA%B5%AD%EC%96%B4-amr-%EA%B0%80%EC%9D%B4%EB%93%9C%EB%9D%BC%EC%9D%B8%EC%9D%98-%ED%95%9C%EA%B3%84)
- [II. 개념과 관계 (Concepts and relations)](#ii-%EA%B0%9C%EB%85%90%EA%B3%BC-%EA%B4%80%EA%B3%84-concepts-and-relations)
- [III. 현상 (Phenomena)](#iii-%ED%98%84%EC%83%81-phenomena)
  - [필수역 (Core roles)](#%ED%95%84%EC%88%98%EC%97%AD-core-roles)
  - [양태 (Modality)](#%EC%96%91%ED%83%9C-modality)
  - [부정 (Negation)](#%EB%B6%80%EC%A0%95-negation)
  - [의문문 (Question)](#%EC%9D%98%EB%AC%B8%EB%AC%B8-question)
  - [선택 의문문 (Choice Question)](#%EC%84%A0%ED%83%9D-%EC%9D%98%EB%AC%B8%EB%AC%B8-choice-question)
  - [명령과 감탄 (Imperative and Expressive mode)](#%EB%AA%85%EB%A0%B9%EA%B3%BC-%EA%B0%90%ED%83%84-imperative-and-expressive-mode)
  - [지시사, 복수형, 시제, 상, 인용, 하이픈 (Articles, plurals, tense, aspect, quotes, hyphens)](#%EC%A7%80%EC%8B%9C%EC%82%AC-%EB%B3%B5%EC%88%98%ED%98%95-%EC%8B%9C%EC%A0%9C-%EC%83%81-%EC%9D%B8%EC%9A%A9-%ED%95%98%EC%9D%B4%ED%94%88-articles-plurals-tense-aspect-quotes-hyphens)
  - [높임과 공손성](#%EB%86%92%EC%9E%84%EA%B3%BC-%EA%B3%B5%EC%86%90%EC%84%B1)
  - [암시된 역할 (Implicit roles)](#%EC%95%94%EC%8B%9C%EB%90%9C-%EC%97%AD%ED%95%A0-implicit-roles)
  - [암시된 개념 (Implicit concepts)](#%EC%95%94%EC%8B%9C%EB%90%9C-%EA%B0%9C%EB%85%90-implicit-concepts)
  - [지정사 '-이다'와 계사적 쓰임을 갖는 '있다' (Main verb "be")](#%EC%A7%80%EC%A0%95%EC%82%AC--%EC%9D%B4%EB%8B%A4%EC%99%80-%EA%B3%84%EC%82%AC%EC%A0%81-%EC%93%B0%EC%9E%84%EC%9D%84-%EA%B0%96%EB%8A%94-%EC%9E%88%EB%8B%A4-main-verb-be)
  - [동사 파생이 될 수 있는 서술성 명사 (Nouns that invoke predicates)](#%EB%8F%99%EC%82%AC-%ED%8C%8C%EC%83%9D%EC%9D%B4-%EB%90%A0-%EC%88%98-%EC%9E%88%EB%8A%94-%EC%84%9C%EC%88%A0%EC%84%B1-%EB%AA%85%EC%82%AC-nouns-that-invoke-predicates)
  - [형용사 파생 및 보조 형용사 (Adjectives that invoke predicates)](#%ED%98%95%EC%9A%A9%EC%82%AC-%ED%8C%8C%EC%83%9D-%EB%B0%8F-%EB%B3%B4%EC%A1%B0-%ED%98%95%EC%9A%A9%EC%82%AC-adjectives-that-invoke-predicates)
  - [이중주어문과 이중목적어문](#%EC%9D%B4%EC%A4%91%EC%A3%BC%EC%96%B4%EB%AC%B8%EA%B3%BC-%EC%9D%B4%EC%A4%91%EB%AA%A9%EC%A0%81%EC%96%B4%EB%AC%B8)
  - [압축적 서술과 명사 상당 어구](#%EC%95%95%EC%B6%95%EC%A0%81-%EC%84%9C%EC%88%A0%EA%B3%BC-%EB%AA%85%EC%82%AC-%EC%83%81%EB%8B%B9-%EC%96%B4%EA%B5%AC)
  - [어미, 접사에 의한 부사어 (Adverbs with -ly)](#%EC%96%B4%EB%AF%B8-%EC%A0%91%EC%82%AC%EC%97%90-%EC%9D%98%ED%95%9C-%EB%B6%80%EC%82%AC%EC%96%B4-adverbs-with--ly)
  - [부가역 (Non-core roles)](#%EB%B6%80%EA%B0%80%EC%97%AD-non-core-roles)
    - [`:source`](#source)
    - [`:destination`](#destination)
    - [`:path`](#path)
    - [`:beneficiary`](#beneficiary)
    - [`:accompanier`](#accompanier)
    - [`:topic`](#topic)
    - [`:duration`](#duration)
    - [`:instrument`](#instrument)
    - [`:medium`](#medium)
    - [`:manner`](#manner)
    - [`:purpose`](#purpose)
    - [`:cause`](#cause)
    - [`:concession`](#concession)
    - [`:condition`](#condition)
    - [`:part`](#part)
    - [`:subevent`](#subevent)
    - [`:consist-of`](#consist-of)
    - [`:example`](#example)
    - [`:direction`](#direction)
    - [`:frequency`](#frequency)
    - [`:extent`](#extent)
  - [초점 (Focus)](#%EC%B4%88%EC%A0%90-focus-1)
  - [구체화 (Reification)](#%EA%B5%AC%EC%B2%B4%ED%99%94-reification)
  - [동사구 (Phrasal verbs)](#%EB%8F%99%EC%82%AC%EA%B5%AC-phrasal-verbs)
  - [한국어의 조사와 시간 및 공간 관련 표현 (Prepositions)](#%ED%95%9C%EA%B5%AD%EC%96%B4%EC%9D%98-%EC%A1%B0%EC%82%AC%EC%99%80-%EC%8B%9C%EA%B0%84-%EB%B0%8F-%EA%B3%B5%EA%B0%84-%EA%B4%80%EB%A0%A8-%ED%91%9C%ED%98%84-prepositions)
  - [관계절 (Relative clauses)](#%EA%B4%80%EA%B3%84%EC%A0%88-relative-clauses)
  - [여러번 할당되는 동일 관계 (Multiple relations with the same name)](#%EC%97%AC%EB%9F%AC%EB%B2%88-%ED%95%A0%EB%8B%B9%EB%90%98%EB%8A%94-%EB%8F%99%EC%9D%BC-%EA%B4%80%EA%B3%84-multiple-relations-with-the-same-name)
  - [접속 (Conjunctions)](#%EC%A0%91%EC%86%8D-conjunctions)
  - [양화사와 작용역 (Quantifiers and scope)](#%EC%96%91%ED%99%94%EC%82%AC%EC%99%80-%EC%9E%91%EC%9A%A9%EC%97%AD-quantifiers-and-scope)
  - [정도 (Degree)](#%EC%A0%95%EB%8F%84-degree)
  - [변항과 상호참조 (Variables and co-reference)](#%EB%B3%80%ED%95%AD%EA%B3%BC-%EC%83%81%ED%98%B8%EC%B0%B8%EC%A1%B0-variables-and-co-reference)
  - [소유 (Possession)](#%EC%86%8C%EC%9C%A0-possession)
  - [관련어 (Pertainyms)](#%EA%B4%80%EB%A0%A8%EC%96%B4-pertainyms)
  - [순서 (Ordinals)](#%EC%88%9C%EC%84%9C-ordinals)
  - [부분집합 (Subsets)](#%EB%B6%80%EB%B6%84%EC%A7%91%ED%95%A9-subsets)
  - [개체명과 위키피케이션 (Named Entities and wikification)](#%EA%B0%9C%EC%B2%B4%EB%AA%85%EA%B3%BC-%EC%9C%84%ED%82%A4%ED%94%BC%EC%BC%80%EC%9D%B4%EC%85%98-named-entities-and-wikification)
  - [역할, 직위를 위한 특수 프레임 (Special Frames for Roles)](#%EC%97%AD%ED%95%A0-%EC%A7%81%EC%9C%84%EB%A5%BC-%EC%9C%84%ED%95%9C-%ED%8A%B9%EC%88%98-%ED%94%84%EB%A0%88%EC%9E%84-special-frames-for-roles)
  - [정확한 수 (Exact numbers)](#%EC%A0%95%ED%99%95%ED%95%9C-%EC%88%98-exact-numbers)
  - [대략적인 수 (Approximate numbers)](#%EB%8C%80%EB%9E%B5%EC%A0%81%EC%9D%B8-%EC%88%98-approximate-numbers)
  - [수량 (Quantities)](#%EC%88%98%EB%9F%89-quantities)
  - [수학 연산자 (Mathematical operators)](#%EC%88%98%ED%95%99-%EC%97%B0%EC%82%B0%EC%9E%90-mathematical-operators)
  - [기타 개체: 날짜, 시간, 백분율, 전화번호, 이메일, URL (Other entities: dates, times, percentages, phone, email, URLs)](#%EA%B8%B0%ED%83%80-%EA%B0%9C%EC%B2%B4-%EB%82%A0%EC%A7%9C-%EC%8B%9C%EA%B0%84-%EB%B0%B1%EB%B6%84%EC%9C%A8-%EC%A0%84%ED%99%94%EB%B2%88%ED%98%B8-%EC%9D%B4%EB%A9%94%EC%9D%BC-url-other-entities-dates-times-percentages-phone-email-urls)
  - [추가 정보 (Further information)](#%EC%B6%94%EA%B0%80-%EC%A0%95%EB%B3%B4-further-information)
  - [AMR 기인열전 (AMR Freak Show)](#amr-%EA%B8%B0%EC%9D%B8%EC%97%B4%EC%A0%84-amr-freak-show)
    - [순환성 (cycle)](#%EC%88%9C%ED%99%98%EC%84%B1-cycle)
    - [그래프로 인코딩할 때의 여러 방법들 (Different textual ways to encode a graph)](#%EA%B7%B8%EB%9E%98%ED%94%84%EB%A1%9C-%EC%9D%B8%EC%BD%94%EB%94%A9%ED%95%A0-%EB%95%8C%EC%9D%98-%EC%97%AC%EB%9F%AC-%EB%B0%A9%EB%B2%95%EB%93%A4-different-textual-ways-to-encode-a-graph)
  - [참고 문헌 (References)](#%EC%B0%B8%EA%B3%A0-%EB%AC%B8%ED%97%8C-references)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->


## *Disclaimer & dependencies*
한국어 AMR 가이드라인은 Abstract Meaning Representation (AMR) 1.2.6 Specification ([Banarescu et al. 2019](https://github.com/amrisi/amr-guidelines/blob/master/amr.md), 이하 English AMR)을 기반으로 작성되었습니다.

English AMR의 주석 예시를 바탕으로 한국어의 주석 지침을 확정하는 과정에서 아래의 자료들을 참고하였음을 밝힙니다.

+ AMR Dictionary: https://amr.isi.edu/doc/amr-dict.html
+ List of AMR NE types: https://amr.isi.edu/doc/ne-types.html
+ List of frame arguments in PropBank (AMR version): https://amr.isi.edu/doc/propbank-amr-frames-arg-descr.txt
+ Korean PropBank: https://catalog.ldc.upenn.edu/LDC2006T03


각 챕터의 내용은 English AMR을 한국어의 문법 현상에 적용한 것입니다. 각 챕터의 제목 옆에는 해당 원문의 링크가 포함되어 있으니, 한국어 AMR 주석 지침을 살피기에 앞서 English AMR 및 다른 언어 AMR의 가이드라인 또한 두루 확인하시기 바랍니다.

**본 문서에서 제시하는 한국어 AMR 가이드라인은 어떠한 기관으로부터도 공인된 자료가 아니며, AMR 또는 UMR(Uniform Meaning Representation) 정책에 따라 계속해서 수정될 수 있습니다.**


# I. 서론 ([Introduction](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#part-i-introduction))

AMR은 문장의 "누가 누구에게 무엇을 한다"하는 의미에 집중합니다. 모든 문장들은 **루트를 가지는(rooted), 유향 비순환 그래프(Directed Acyclic Graph; DAG)** 로 표현됩니다. AMR은 관계(relation)를 드러내는 간선(edge)과 개념(concepts)을 나타내는 노드(node)들로 이루어집니다.

AMR은 분석 트리(parse tree)처럼, 모든 노드에 도달 가능한(traversable) 단일 그래프 상에 연관된 단어들을 포괄합니다. 파스 트리와는 다르게 AMR은 **추상적**입니다. 각각의 문장들이 가지는 개념적 의미가 동일하다면, 이들 문장들은 동일한 AMR로 표현될 수 있습니다. (이는 하나의 AMR과 특정한 한 문장 사이의 일대일 관계를 보장하지 않음을 의미합니다. 뜻은 같더라도 말을 어떻게 하는가는 다른 문제이지요.) 또한 의존 구문 분석(dependency parsing)처럼 문장 내의 모든 개별 단어에 대해 주석을 하는 것은 아닙니다. (AMR은 비가역적인 주석입니다.)

AMR은 standard feature structure representation [Shieber 1986, Carpenter 1992]을 활용하여 단순화된 standard neo-Davidsonian semantics [Davidson 1967, Higginbotham 1985]을 구현한 것입니다. 형식적인 면에서 AMR은 unification systems [Kay 1979, Knight 1989, Moore 1989]와 natural language generation [Mann 1982, Elhadad 1995, Knight & Hatzivassiloglou 1995]에 근간을 두고 있습니다. **한국어 AMR에서 서술어의 갈래뜻과 필수 의미역 주석은 Korean PropBank [Palmer et al. 2006]를 바탕으로 합니다.**

한국어와 같은 개별 언어의 문장을 AMR로 표현하는 작업에 있어서, 어떻게 작업해야 한다는 특별한 원칙이나 제약은 없습니다. 한국어 문장을 바탕으로 표현된 AMR은 한국어에만 적합한 것일 수 있습니다. AMR은 언어 간의 호환성을 보장하지 않습니다. (*AMR is not an interlingua.*)


## 예시 ([Example](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#example))

<img width="500" alt="graph" src="https://user-images.githubusercontent.com/20152058/63767149-c515b900-c907-11e9-905a-b0bfea683a22.png">

이 AMR의 의미는 대략 다음과 같습니다: 사건 `생각-01` 주체(`:ARG0`)는 `소년`이 되고 대상(`:ARG1`)은 `좋-02` 사건이 됩니다. (*소년이 '~ 좋아한다'고 생각한다.*) `좋-02` 사건의 주체(`:ARG0`)는 `소녀`가 되고 대상(`:ARG1`)은 앞서 상위에서 언급되었던 `소년`이 됩니다. (*소년이 '소녀가 소년을 좋아한다'고 생각한다.*) 따라서 `소년`의 역할은 (1) `생각-01` 사건의 주체(`:ARG0`)이자 (2) `좋-02` 사건의 대상(`:ARG1`)으로 모두 두 가지입니다. 이런 경우 AMR에서는 같은 개념 노드를 가리키는 두 개의 관계 화살표를 통해 표현할 수 있습니다.

아래는 텍스트 친화적인 AMR입니다.

~~~lisp
(생 / 생각-01
    :ARG0 (소 / 소년)
    :ARG1 (좋 / 좋-02
        :ARG0 (소2 / 소녀)
        :ARG1 소))
~~~

변항(variables) `생`, `소`, `좋`, `소2`는 단일 그래프 내의 노드를 가리킵니다. `(소 / 소년)`을 참조하기 위해 `소`가 2번 나타난 것에 유의하세요.

이 AMR은 아래와 같이 루트(root) 정보를 생략한 논리적 트리플의 결합으로 나타낼 수도 있습니다.

~~~lisp
instance(생, 생각-01) ^        /* '생'은 '생각-01'의 인스턴스 */
instance(소, 소년) ^           /* '소'는 '소년'의 인스턴스 */
instance(좋, 좋-02) ^         /* '좋'은 '좋-02'의 인스턴스 */
instance(소2, 소녀) ^          /* '소2'는 '소녀'의 인스턴스 */
ARG0(생, 소) ^                 /* '생'의 '생각하는 주체'인 '소' */
ARG1(생, 좋) ^                 /* '생'에서 '생각되는 대상'인 '좋' */
ARG0(좋, 소2) ^                /* '좋'에서 '좋아하는 주체'인 '소2' */
ARG1(좋, 소)                   /* '생'에서 '좋아하는 대상'인 '소' */
~~~

## 언어로부터의 추상화 ([Abstraction away from language](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#abstraction-away-from-english))

위의 AMR은 표면형에서 다양한 문장으로 실현될 수 있습니다.


> 소년은 소녀가 자기를 좋아한다고 생각했다.
>
> 소년은 "소녀가 나를 좋아하네."라고 생각했다.
>
> 소년은 소녀를 두고, "걔는 나를 좋아해."라고 생각했다.
>
> …


`좋-02`은 *"좋아한다"*, *"좋아하다"*, *"좋아할 것이다"* 등으로 실현될 수 있을 것입니다. AMR에서 노드는 실제로 쓰인 '단어(Word)'가 아니라 '개념(Concept)'입니다. AMR의 요소(element)를 가리키면서 *"이것은 동사다"*, *"이것은 명사다"* 와 같이 말하지 않습니다. 오히려 *"이것은 객체(object)다."* 또는 *"이것은 사건(event)이다"* 와 같이 말할 수 있습니다.

단일 개체(entity)인 `소년`은 `생각-01`의 `:ARG0`나 `좋-02`의 `:ARG1`과 같이 동시에 여러 역할을 수행할 수 있습니다. AMR은 대용어나 영 대명사(zero-pronouns)에 대해서는 언급하지 않지만, 한국어에서 이러한 방식의 대용은 한 문장에서 어떤 개체가 여러 역할을 수행하는 것을 표현하는 자연스러운 방식입니다.

일반적으로 AMR에서 기능어(function words)는 주석하지 않습니다.

~~~lisp
(조 / 조작-01
    :ARG0 (인 / 인부)
    :ARG1 (기 / 기계))
~~~
> 직원은 기계를 조작했다.
>
> 기계는 직원이 조작했다.


~~~lisp
(죽 / 죽-01
    :time (어 / 어제))
~~~

> 죽은 것은 어제였다.
>
> 죽은 **시점**은 어제.


~~~lisp
(a / and
    :op1 (소 / 소녀)
    :op2 (소2 / 소년))
~~~
> 소년과 소녀
>
> 소년, 소녀 **둘 다**

~~~lisp
(집 / 집
    :poss (그 / 그))
~~~
> 그의 집
>
> 그가 집주인**이**다.


**다만 일부 보조사나 의존 명사는 상황에 따라 주석될 필요가 있습니다.** '도' 또는 '만'과 같은 보조사나, 의존명사 '등'과 같이 특별한 의미 기능이 있는 경우는 상황에 따라 명시적으로 주석하는 것이 바람직합니다.

## 통사적이기보다는 더 논리적인 표상 ([More Logical than Syntax](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#more-logical-than-syntax))

AMR은 더 논리적이고 덜 통사적인 표상(more logical, less syntactic representation)입니다. 예를 들어 "그 아이는 가야 된다."와 "그 아이는 가도 된다."는 문장 구조상 비슷해 보일 수 있지만, 각각의 부정문의 AMR에서 `:polarity -`의 위치는 매우 다르게 나타납니다.

**참고:** 아래 `obligate-01`에 대응하는 양태를 나타내는 한국어 용언 프레임은 특정되지 않았습니다. [양태](#%EC%96%91%ED%83%9C-modality)를 참고하시기 바랍니다.

~~~lisp
(o / obligate-01
    :ARG2 (가 / 가-01
        :ARG0 (아 / 아이))
        :polarity -)
~~~
> 그 아이는 가면 안 된다.
>
> 그 아이는 가지 말아야 한다.

~~~lisp
(허 / 허가-01
    :ARG2 (가 / 가-01
        :ARG0 (아 / 아이))
    :polarity -)
~~~
> 그 아이가 가는 것을 허가할 수 없다.


AMR은 부정되는 것이 무엇인지를 분명히 표시합니다. `허가-01`의 의미가 표면형에서는 "해도 된다"처럼 보조 용언을 동반해서 실현되거나, "허가하다"와 같은 단일 용언, "인가", "승인", "받아들여지다"와 같은 다른 말들을 통해 실현될 수도 있음을 기억하세요.

## 초점 ([Focus](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#focus))

AMR에서 루트(root)는 종속된 모든 내용을 단일한 그래프로 묶는 역할을 합니다. (루트가 없으면 최상위에서 여러 내용들이 열거될 경우 이들을 하나로 묶을 수 없습니다.) 덕분에 AMR은 모든 노드가 탐색 가능한 유향 그래프(Traversable directed graph)가 됩니다. **또한 루트는 문장의 의미 전반에 대한 토대(*a rudimentary representation of overall focus*)를 제공합니다.** 즉, 루트는 초점(Focus)으로 기능합니다.

~~~lisp
(희 / 희-01
    :ARG1 (대 / 대리석))
~~~
> 대리석이 희다.

~~~lisp
(대 / 대리석
    :ARG1-of (희 / 희-01))
~~~
> 흰 대리석

~~~lisp
(알 / 알-01
    :ARG0 (소 / 소년)
    :ARG1 (희 / 희-01
        :ARG1 (대 / 대리석)))
~~~
> 소년은 대리석이 희다는 것을 알았다.

~~~lisp
(알 / 알-01
    :ARG0 (소 / 소년)
    :ARG1 (대 / 대리석
        :ARG1-of (희 / 희-01)))
~~~
> 소년은 흰 대리석을 알았다.


`:domain`의 역관계는 `:domain-of`로 쓰기보다 보통 `:mod`로 줄입니다.

역관계(inverse roles)는 단일 루트 구조를 유지하는 데에 좋은 방법입니다. 가령,

~~~lisp
(읽 / 읽-01
    :ARG0 (아 / 아이)
    :ARG1 (책 / 책
        :mod (그 / 그)
        :ARG1-of (원 / 원하-01
            :ARG0 아))
    :time (전 / 전))
~~~
> 아이가 원하는 그 책은 아이가 전에 읽은 적이 있다.


여기서 초점을 바꾸고 싶다면 어떤 노드든 루트로 "올리고", 다른 노드들이 어떻게 전개될지를 생각하면 됩니다. 예를 들어,`원하-01` 노드를 루트로 올리면, 구조는 다소 달라지겠지만 동일한 내용을 담고 있는 AMR을 얻을 수 있습니다.

~~~lisp
(원 / 원하-01
    :ARG0 (아 / 아이)
    :ARG1 (책 / 책
        :mod (그 / 그)
        :ARG1-of (읽 / 읽-01
            :ARG0 아
            :time (전 / 전))))
~~~  
> 아이가 전에 읽었던 그 책을 원한다.

이것은 초점을 무엇에 두느냐의 문제입니다. '읽는다'는 사건에 초점(`읽-01`)을 둔 첫 번째 AMR과 '원하다'는 사건에 초점(`원하-01`)을 둔 두 번째 AMR의 차이에 유의하세요.

역관계에 대한 또다른 예시(`:instrument-of`)는 아래와 같습니다.

~~~lisp
(개 / 개정-01
    :ARG1 (문 / 문서
        :instrument-of (규 / 규제-01)))
~~~
> 규제 문서가 개정되었다.


## AMR 강령 ([AMR slogans](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#amr-slogans))

아래는 AMR 주석 작업을 더 쉽게 이해할 수 있도록 기본적인 원칙들을 보인 것입니다.

- AMR은 문장의 전반적인 의미를 담기 위해 단일 유향 비순환 그래프로 표상되며, 루트를 기점으로 모든 노드는 도달 가능하게 연결된다.

- AMR은 어떻게 쓰일 수 있는가에 대해 중립적이다.

- 개별 언어의 특성에 따라 AMR의 구성 요소들은 달라질 수 있다. 또한 개별 언어의 어휘에 따라 동일한 개념, 사건의 의미에 대해서 약간 다른 구조적 차이가 발생할 수도 있다. AMR은 언어 간의 호환성을 보장하지 않는다.

- AMR에는 명사, 동사가 없다. (표층에서 나타나는 문법이나 형식보다는 사건과 개념에 의한 심층 구조에 관한 것이다.)

- AMR을 작성할 때 구구조 또는 의존구조 분석은 보통 필요치 않다. 그러나 자연어 문장에서 형태 통사적 중의성이 발생했을 때에는 고려할 수도 있다.

- 하나의 AMR은 하나의 문장에만 대응되는 것이 아니다. 여러 문장이 동일한 AMR로 표현될 수 있고, 하나의 AMR로부터 여러 문장이 생성될 수 있다.

AMR을 작성하는 작업은 마치 외국어 번역과도 같습니다. 구체적인 문장을 바탕으로 AMR을 작성한다고 했을 때, 문장 내의 각 토큰들과 AMR 그래프에 포괄된 각각의 개념들이 일대일로 꼭 대응되거나 엄밀하게 정렬될 수 있는 것은 아닙니다. 그러나 그러한 작업이 (아마도 자동 처리에 의해) 추후에는 가능하리라 생각할 수 있고, 두 언어 간의 문장 토큰들을 서로 정렬하는 작업과 비슷할 수도 있겠습니다.

## English AMR 1.2의 한계 ([Limitations of AMR 1.2](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#limitations-of-amr-12))

English AMR 1.2는 여러모로 개선해야 할 문제들이 아직 많습니다.

- 한 언어의 어휘나 특수성 등, 개별 언어적 상황에 따라 표현 지침이 좌우됩니다.

- 수량사의 범위를 표현할 수 없고, 보편 양화사에 대한 대책도 마련되어 있지 않습니다. (**참고:** DMR@ACL2019에서는 UMR 업데이트에 대응하기 위한 수량사와 작용역 주석 방법이 공개되었습니다.)

- 문장 경계를 넘어가는 공지시(Co-references)에 대한 처리 방법이 없습니다. (**참고:** 2018년 상반기에 공개된 LDC general release에는 일부 AMR 문서를 대상으로 다중 문장 공지시 및 무형대용어 주석 방침이 포함되었으며, `multi-sentence` 주석 scheme은 공식 AMR에 포함되었습니다.)

- 문법적 수(number), 시제(tense), 상(aspect), 인용 부호(quotation marks) 등을 누락시킵니다.

- 명사-명사 관계나, 명사-형용사 관계에 대한 심층적 해석을 제공하지 않습니다. (**참고:** 한국어 AMR에서는 일반적인 복합 명사 또는 명사 상당 어구에 대해 해석적인 주석을 지향합니다.)

- 진도(magnitude), 진앙(epicenter), 사상자(casualties) 등의 역할을 갖는 Earthquake 프레임이나, 엄마(mother), 아빠(father), 아이의 성(baby gender),  착상 후 경과 시간(time since inception) 등의 역할을 갖는 Pregnancy처럼 상세한 프레임을 포함하지는 않습니다. AMR 1.2는 AMR 2.0으로의 개정을 목표로 하고 있습니다.


### 한국어 AMR 가이드라인의 한계

한국어 AMR 가이드라인은 아래와 같은 문제들에 대해서 아직 뚜렷한 지침을 제시하지 못하고 있습니다. 갈 길이 아주 머네요!

- 다수의 우언적 구성에 대해 처리 방법을 명확하게 제시하지 못하고 있습니다. 이를 위해 한국어의 우언적 구성을 분류하고 각각의 우언적 구성들이 어떤 관계 또는 프레임에 대응되는지를 사전식으로 제시할 수 있도록 별도의 챕터를 구성할 계획입니다.


# II. 개념과 관계 ([Concepts and relations](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#part-ii--concepts-and-relations))

개념(Concepts)은 AMR 그래프의 노드가 되는 토큰입니다. AMR은 세계를 놓고 이를 사건이나 객체, 자질 등으로 나누거나 하지는 않습니다. 다만 특정 개념의 인스턴스를 사건으로 참조할 수는 있습니다. 아래의 AMR은 3개의 개념 (`소년`, `책`, `주-01`)을 가집니다.

~~~lisp
(주 / 주-01)
    :ARG0 (소 / 소년)
    :ARG1 (책 / 책
        :poss 소))
~~~
> 소년은 그의 책을 줬다.


여기서 슬래시(`/`)는 ***인스턴스*** 관계임을 나타내는 축약입니다. (예: `소`는 `소년`의 인스턴스) 이러한 관계 표현 방식은 AMR 그래프의 형식을 더 간결하게 나타냅니다. ([서론](#i-%EC%84%9C%EB%A1%A0-introduction)을 확인하세요.)

AMR의 개념은 대개 한국어 어휘 또는 구로 쓰입니다. 필수 논항 관계(core semantic relation)를 가진 개념은 의미별 프레임을 구분하기 위한 번호를 포함할 수 있습니다.

~~~lisp
(생 / 생각-01
    :ARG0 (소 / 소년))
~~~
> 소년은 생각한다.

AMR의 의미 관계는 다음 챕터(III. 현상)에서 예시와 함께 더 자세하게 설명합니다. 여기서는 간략한 설명만 하겠습니다.

필수(core) `:ARGx` 논항 역할에 대한 주석은 Korean PropBank 프레임의 numbered-roleset을 사용합니다.
~~~lisp
:ARGA, :ARG0, :ARG1, :ARG2, :ARG3
~~~

수의 논항 역할(non-core roles):
~~~lisp
:accompanier, :age
:beneficiary
:concession, :condition, :consist-of
:degree, :destination, :direction, :domain, :duration
:example, :extent
:frequency
:instrument
:li, :location
:manner, :medium, :mod, :mode
:name
:ord
:part, :path, :polarity, :polite, :poss, :purpose
:quant
:range
:scale, :source, :subevent
:time, :topic
:unit
:value
:wiki
~~~


`date-entity`에 활용되는 역할:
~~~lisp
:calendar, :century, :day, :dayperiod, :decade, :era, :month, :quarter, :season, :timezone, :weekday, :year, :year2
~~~


접속(Conjunction)이나 위치, 시간 등 특정 표현에 대한 내용을 기술할 때 `:opx`를 활용할 수 있습니다.
~~~lisp
:op1, :op2, :op3, :op4, ...
~~~


`:postp-X` 형태(English AMR의 `:prep-X`에 해당)의 역할은 앞서 제시된 주석을 활용할 수 없을 때 동원해볼 수 있겠지만, 가급적 활용을 지양하는 것이 좋습니다. 아래는 일부 예시이며 `:postp-X` 관계는 한국어 AMR에서 인정될 수 있습니다. (**참고:** 현재 '도'나 '만'과 같은 보조사의 처리는 적당한 논항 역할과 함께 `:mod`를 부여하는 것으로 주석하고 있습니다. `:postp-X`와 같은 역할을 활용한다는 것은 개념적인 표상을 다소 포기하는 방법이 되므로 가급적 활용하지 않는 것이 바람직합니다.)


~~~lisp
:postp-는커녕, :postp-으로-의, ...
~~~
등등.


일부 접속부사들은 위에서 제시된 Non-core roles로 처리하기 어려운 경우도 있을 것입니다. 마찬가지로 가급적 활용을 지양하는 것이 좋겠지만 부득이한 경우가 있기 마련이죠.
~~~lisp
:conj-뿐-아니라, ...
~~~
등등.


위에서 제시된 모든 역할의 역관계(inverse role)는 `:X-of`의 형태로 나타낼 수 있습니다. (**참고:** `:consist-of`의 역관계는 `:consist-of-of`입니다.)
~~~lisp
:ARG0-of, :ARG1-of
:location-of, :consist-of-of
~~~
등등.


# III. 현상 ([Phenomena](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#part-iii--phenomena))

## 필수역 ([Core roles](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#core-roles))

필수역은 Korean PropBank의 의미역을 가져옵니다.

- `주-01`(give)의 `:ARG0`는 주는 주체(agent)를 나타냅니다.

- `주-01`(give)의 `:ARG1`는 주는 대상(thing given)을 나타냅니다.

- `주-01`(give)의 `:ARG2`는 주는 행위의 상대방(given to)을 나타냅니다.

~~~lisp
(주 / 주-01
    :ARG0 (소 / 소년)
    :ARG1 (책 / 책)
    :ARG2 (소2 / 소녀))
~~~
>소년은 소녀에게 책을 줬다.
>
>소년은 소녀에게 책을 주었던 것이다.
>
>소년은 책을 소녀에게 주었다.
>
>...

***Predicate-sensitivity:*** 모든 주어가 늘 `:ARG0`인 것은 아닙니다. 예를 들어 `걱정-01`은 걱정하는 사람이 (놀랍게도!) `:ARG1`입니다.

- `걱정-01`(worry)의 `:ARG0`는 걱정의 대상(topic of worry)를 나타냅니다.

- `걱정-01`(worry)의 `:ARG1`는 걱정하는 주체(worrier)을 나타냅니다.

문장의 주어(subject)와 행위의 행동주(agent), 사건의 대상(theme) 등을 서로 혼동해선 안되며, 함부로 짐작해서도 안됩니다. 문장에서 조사 '-을/를'을 동반하는 목적어가 `:ARG1`일지 `:ARG2`일지는 개별 서술어의 격틀 구조에 달린 것에 불과합니다. 반드시 Korean PropBank 프레임의 roleset을 확인하고 주석하여야 한다는 점을 잊지 마세요!

어떤 의미 프레임(semantic frame)은 한국어에서 다채로운 방식으로 실현될 수 있습니다.

~~~lisp
(알 / 알-01
    :ARGA (경 / 경찰
        :location (현 / 현장))
    :ARG0 (본 / 본부)
    :ARG1 (실 / 실패-01
        :ARG2 (작 / 작전)))
~~~
> 현장 경찰은 작전이 실패했음을 본부에 알렸다.
>
> 현장에 있던 경찰이 본부에 알린 바에 따르면, 작전은 실패했다.
>
> 현장 경찰이 본부에 알림: 작전 실패
>
> 작전이 실패했다는 것을 본부는 현장 경찰에 의해 알고 있다.
>
>...

AMR은 문장에 나타난 "바", "-에서", "-을" 따위를 어떻게 표현할지에 대해 신경쓰지 않습니다.

Korean PropBank의 서술어 프레임과 roleset의 정의가 애매하거나 조금 우스워 보일 수는 있습니다. 예를 들어 `가르치-01`의 `:ARG0`은 'teacher'이고, `:ARG1`은 'subject', `:ARG2`는 'student(s)'이지만 이것이 꼭 말 그대로 '선생님'과 '과목', '학생'만을 논항으로 취해야 하는 것을 의미하는 것은 아닙니다. 가르치는 사람의 직업이 반드시 교사일 필요는 없으며, 가르치는 내용이 반드시 정규 과목이어야 하는 것은 아닙니다. 즉, "그는 딸에게 운전하는 법을 가르쳐 주었다."라는 문장도 `가르치-01`를 활용하여 주석할 수 있습니다.

Korean PropBank에 등재되지 않은 단어(미등재어)가 있다면, AMR은 `-00`을 취하여 주석합니다.
~~~lisp
(가 / 가능-01
    :ARG1 (조 / 조회-00
        :location (지 / 지점
            :ARG1-of (가2 / 가깝-01))
        :ARG1 (사 / 사실
            :mod (신 / 신청-01))))
~~~
> 가까운 지점에서 신청 사실을 조회할 수 있습니다.

## 양태 ([Modality](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#modality))

English AMR에서는 통사적 양태를 `possible-01`(가능), `likely-01`(개연), `obligate-01`(의무), `permit-01`(허락), `recommend-01`(권장) 등의 프레임을 활용하여 표상합니다.

한국어 AMR에서도 (English AMR과 유사한 요령으로) `가능-01`, `허가-01`, `선호-01` 등의 프레임을 활용하여 양태를 표상할 수 있습니다. 그러나 Korean PropBank에는 `obligate-01`나 `likely-01` 등에 직접 대응하는 적절한 한국어 용언 프레임이 없는 상태입니다. 이와 같은 경우에는 **임시적으로** English AMR의 처리 기준을 따라 `obligate-01`, `likely-01` 등을 활용하여 의무 양태를 표상할 수 있습니다.

**참고:** 한국어 AMR에서 양태를 어떻게 다룰 것인가에 대한 기준은 앞으로 계속 개정될 예정입니다. 예를 들어 `possible-01`과 `가능-01`은 roleset의 구조가 유사하여 서로 대응되는 용언 프레임으로 특정된 것이지만, 모든 경우가 그럴 수는 없습니다. 이 챕터에서 보이는 양태 처리 기준은 아직 **임시방편**에 불과합니다. AMR의 기본적인 원칙은 같은 양태 의미를 가진다면 동일한 개념을 활용하여 표상하는 것입니다. **따라서 아래에 보인 몇몇 처리 지침은 추후 더 나은 방법으로 대체될 수 있습니다.**

~~~lisp
(가 / 가능-01
    :ARG1 (걷 / 걷-01
        :ARG0 (로 / 로봇
            :mod (이 / 이))))
~~~
> 이 로봇은 걸을 수 있다.
>
> 이 로봇은 걷는 것이 가능하다.
>
> 이 로봇은 걸을 줄 안다.

~~~lisp
(o / obligate-01
    :ARG2 (가 / 가-01
        :ARG0 (소 / 소년)))
~~~
> 소년은 가야 한다.
>
> 소년이 가는 것은 의무다.

~~~lisp
(허 / 허가-01
    :ARG1 (가 / 가-01
        :ARG0 (소 / 소년)))
~~~
> 그 아이는 가도 된다.
>
> 그 아이는 가는 것이 허가되었다.

~~~lisp
(가 / 가능-01
    :ARG1 (내 / 내리-04
        :ARG1 (비 / 비)))
~~~
> 비가 내릴 모양이다.
>
> 비가 내릴지도 모른다.
>
> 강수 확률이 있다.

~~~lisp
(l / likely-01
    :ARG1 (가 / 가-01
        :ARG0 (소 / 소년)))
~~~
> 소년은 갈 가능성이 높다.
>
> 소년은 가기 마련이다.

~~~lisp
(선 / 선호-01
    :ARG0 (소 / 소년)
    :ARG1 (가 / 가-01
        :ARG0 소))
~~~
> 소년은 가려고 할 것이다.
>
> 소년은 가고 싶어 한다.

## 부정 ([Negation](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#negation))

AMR은 `:polarity` 를 이용하여 논리적인 부정을 표현합니다.

~~~lisp
(가 / 가-01
    :ARG0 (소 / 소년)
    :ARG3 (학 / 학교)
    :polarity -)
~~~
> 소년은 학교에 안 갔다.

한국어의 통사적 부정문은 '부정소(不定素)'라 불리는 요소에 의해 실현되는 문장을 말합니다. 통사적 부정문의 범주에는 들지 않지만, 부정의 의미를 가진 문장 역시 AMR에서는 부정으로 봅니다. 즉 '아니(안)', '못' 외의 부정소에 의한 부정뿐만 아니라 '아니하다(않다)', '못하다', '말다', '아니다' 등 용언에 의해 실현된 문장 역시 `:polarity -`을 활용하여 표상한다는 것입니다.

~~~lisp
(가 / 가능-01
    :ARG1 (가2 / 가-01
        :ARG0 (소 / 소년)
        :ARG3 (학 / 학교))
    :polarity -)
~~~
> 소년은 학교에 갈 수 없다.
>
> 소년이 학교에 가는 것은 불가능하다.
>
> 소년은 학교에 못 간다.

이때 `불가능-01` 등의 프레임을 활용하기 보다는 `가능-01`과 `:polarity -`를 활용하는 것이 더 바람직한 방법입니다.

~~~lisp
(가 / 가능-01
    :ARG1 (가2 / 가-01
        :ARG0 (소 / 소년)
        :ARG3 (학 / 학교)
        :polarity -))
~~~
> 소년이 학교에 가지 않을 수 있다.
>
> 소년이 학교에 안 갈 수 있다.

~~~lisp
(o / obligate-01
    :ARG2 (가 / 가-01
        :ARG0 (소 / 소년))
    :polarity -)
~~~
> 소년은 가지 않아도 된다.

~~~lisp
(o / obligate-01
    :ARG2 (가 / 가-01
        :ARG0 (소 / 소년)
        :polarity -))
~~~
> 소년은 가지 말아야 한다.
>
> 소년은 가선 안 된다.

~~~lisp
(생 / 생각-01
    :ARG0 (소 / 소년)
    :ARG1 (이 / 이기-01
        :ARG0 (팀 / 팀
            :poss 소))
    :polarity -)
~~~
> 소년은 자기네 팀이 이길 것이라고 생각하지 않는다.
>  
> 소년은 자기 팀이 이길 거라 생각 안해. (구어체의 경우 또는 중의적인 경우에 한정)

~~~lisp
(생 / 생각-01
    :ARG0 (소 / 소년)
    :ARG1 (이 / 이기-01
        :ARG0 (팀 / 팀
            :poss 소)
        :polarity -))
~~~
> 소년은 소년의 팀이 못 이길 거라고 생각한다.
>  
> 소년은 자기 팀이 이길 거라 생각 안해. (구어체의 경우 또는 중의적인 경우에 한정)

~~~lisp
(가 / 가지-01
    :ARG0 (나 / 나)
    :ARG1 (돈 / 돈)
    :polarity -)
~~~
> 나는 돈을 가지고 있지 않다.
>
> 나는 가진 돈이 없다.

앞서 `불가능-01`을 직접 활용하지 않고 `가능-01`과 `:polarity -`를 활용하여 부정의 의미를 나타내었습니다. 부정소 외에도 부정접사에 의한 어휘적 부정 역시 `:polarity -`로 부정의 의미를 명시합니다. 물론 이런 방식으로 주석을 하게 되면 반의어 관계에 있는 어휘들 중 어디까지 이 기준을 적용할 것인가를 결정하기 어려울 수 있습니다. 일반적으로 '미(未)-', '무(無)-', '비(非)-', '불(不)-', '몰(沒)-'과 같은 부정의 접두사를 포함한 단어가 쓰인 문장이나 '모르다', '없다' 등의 서술어가 사용된 문장들은 모두 부정으로 봅니다.

~~~lisp
(적 / 적절하-01
    :ARG1 (옷 / 옷차림)
    :polarity -)
~~~
> 옷차림이 적절하지 않다.
>
> 옷차림이 부적절하다.

~~~lisp
(옷 / 옷차림
    :ARG1-of (적 / 적절하-01
        :polarity -))
~~~
> 적절하지 않은 옷차림
>
> 부적절한 옷차림

~~~lisp
(알 / 알-01
    :ARG0 (나 / 나)
    :ARG1 (그 / 그녀)
    :polarity -)
~~~
> 나는 그녀를 잘 알지 못한다.
>
> 나는 그녀를 모른다.

~~~lisp
(완 / 완성-01
    :ARG1 (지 / 지침)
    :polarity -)
~~~
> 지침이 완성되지 않았다.
>
> 지침이 미완성이다.

대개 '미(未)-'에는 '아직'의 의미가 있지만 부정과 관련하여 그 의미를 크게 부각시키지는 않습니다.

~~~lisp
(정 / 정상
    :domain (문 / 문장
        :mod (이 / 이))
    :polarity -)
~~~
> 이 문장은 비정상적이다.
>
> 이 문장은 정상적이지 않다.
>
> 이 문장은 정상이 아니다.
>
> 이 문장은 정상적인 것이 아니다.

## 의문문 ([Question](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#questions))

AMR은 의문을 표상하기 위해 `amr-unknown`을 해당 위치에 놓습니다.

~~~lisp
(찾 / 찾-01
    :ARG0 (소 / 소녀)
    :ARG1 (a / amr_unknown))
~~~
> 소녀가 찾는 것이 무엇인가?
>
> 소녀가 무얼 찾는가?

~~~lisp
(찾 / 찾-01
    :ARG0 (소 / 소녀)
    :ARG1 (소2 / 소년)
    :location (a / amr_unknown))
~~~
> 소녀가 소년을 찾은 곳은 어디인가?
>
> 어디서 소녀가 소년을 찾았나?

~~~lisp
(찾 / 찾-01
    :ARG0 (소 / 소녀)
    :ARG1 (소2 / 소년)
    :manner (a / amr_unknown))
~~~
> 소녀가 소년을 어떻게 찾았나?

~~~lisp
(찾 / 찾-01
    :ARG0 (소 / 소녀)
    :ARG1 (장 / 장난감
        :poss (a / amr_unknown)))
~~~
> 소녀가 찾은 장난감이 누구의 것인가?
>
> 소녀는 누구의 장난감을 찾았나?

~~~lisp
(달 / 달리-01
    :ARG0 (소 / 소녀)
    :manner (빠 / 빠르-01
        :degree (a / amr_unknown)))
~~~
> 소녀가 얼마나 빨리 달리니?

~~~lisp
(보 / 보-01
    :ARG0 (소 / 소녀)
    :ARG1 (a / amr_unknown
        :ARG1-of (붉 / 붉-01)))
~~~
> 소녀가 본 붉은 것이 무엇인가?

~~~lisp
(주 / 주도-01
    :ARG0 (그 / 그녀)
    :ARG1 (a / amr_unknown
        :ARG1-of (조 / 조사-01)))
~~~
> 그녀는 무엇에 대한 조사를 주도하고 있니?

또한 AMR에서는 판정 의문문(yes-no question)을 처리하기 위해 `amr-unknown`를 활용합니다. 이때 `amr-unknown`은 `:polarity` 관계와 결합하며, 본질적으로 '이 전제의 진리값이 무엇인가'에 대한 표상이 됩니다.

~~~lisp
(찾 / 찾-01
    :ARG0 (소 / 소녀)
    :ARG1 (소2 / 소년)
    :polarity (a / amr-unknown))
~~~
> 소녀가 소년을 찾았습니까?

~~~lisp
(찾 / 찾-01
    :ARG1 (소 / 소년)
    :polarity (a / amr-unknown))
~~~
> 소년을 찾았습니까?


'누구'와 같은 대명사가 의문사로 쓰인 것이 아닌 경우는 구분되어야 합니다. '누구'와 같은 개념(흔히 대명사)이 관계화된 경우는 `amr_unknown`가 아닌 역관계를 활용하여 표현하는 것에 유의하세요.

~~~lisp
(알 / 알-01
    :ARG0 (나 / 나)
    :ARG1 (사 / 사람
        :ARG1-of (보 / 보-01
            :ARG0 (너 / 너))))
~~~
> 나는 네가 본 사람이 누구인지 안다.
>
> 나는 네가 본 사람을 안다.

AMR은 의문문은 아니지만 '~ㄴ지 아닌지'와 같은 의문이 내포된 문장에 대해서도 역관계를 활용합니다. 이때에는 앞서 보인 바와 같이 관계절을 표상할 때에는 `amr_unknown`을 사용하지 않지요. 이 경우에는 어떤 사건이 발생했는지 아닌지에 대해 표상하기 위해 `truth-value`를 활용합니다.

~~~lisp
(알 / 알-01
    :polarity -
    :ARG0 (소 / 소년)
    :ARG1 (t / truth-value
        :polarity-of (오 / 오-01
            :ARG0 (소2 / 소녀))))
~~~
> 소년은 소녀가 왔는지 아닌지를 모른다.

아래와 비교해 보세요.

~~~lisp
(알 / 알-01
    :polarity -
    :ARG0 (소 / 소년)
    :ARG1 (오 / 오-01
        :ARG0 (소2 / 소녀)))
~~~
> 소년은 소녀가 왔다는 것을 모른다.
>
> 소년은 소녀가 왔다는 것을 알지 못한다.

## 선택 의문문 ([Choice Question](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#choice-questions))

선택 의문문은 판정(yes-no) 의문문과 비슷해 보일 수 있지만, 가능한 응답의 집합을 제공합니다. 선택 의문문은 `amr-choice`(주로 `or`의 자리)를 활용하여 표상하며, 숫자를 붙여 쓰는 `:op` 논항을 활용할 수 있습니다.

~~~lisp
(원 / 원하-01
    :ARG1 (a / amr-choice
        :op1 (차 / 차)
        :op2 (커 / 커피)))
~~~
> 차와 커피 중에서 어떤 것을 원하세요?

~~~lisp
(권 / 권유-01
    :ARG1 (a / amr-choice
        :op1 (머 / 머무르-01
            :ARG1 (나 / 나))
        :op2 (가 / 가-01
            :ARG0 나)
    :ARG2 나))
~~~
> 제가 머물러야 하나요 아니면 가야 하나요?


## 명령과 감탄 ([Imperative and Expressive mode](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#imperative-and-expressive-mode))

`:mode imperative`는 명령문을 표상할 때 활용됩니다. AMR에서는 느낌표가 붙거나 하여 강세가 있는 명령문(Exclamatory imperatives) 역시 단순히 명령문으로 처리합니다.

~~~lisp
(가 / 가-01
    :mode imperative
    :ARG0 (너 / 너))
~~~
> 가라.
>
> 가라고!

~~~lisp
(가 / 가-01
    :mode imperative
    :ARG0 (우 / 우리))
~~~
> 가자.
>
> 갑시다!

`아, 어머, 우와, 오예` 등 감정을 표현할 뿐 특정한 사건이나 대상, 속성 등을 가리키는 것이 아닌 감탄사에는 `:mode expression`을 활용합니다. 단순히 강조가 목적인 볼드체나 이탤릭체, 느낌표 '!', 따옴표 등을 이용한 강조에는 `:mode expression`을 **사용하지 않는다는** 것에 유의하세요. '어', '음'과 같은 간투사 혹은 말더듬(disfluency markers)도 AMR에서는 나타내지 않습니다.

~~~lisp
(우 / 우와 :mode expression)
~~~
> 우와!

~~~lisp
(응 / 응 :mode expression)
~~~
> 응!!!

`응` 또는 `그래`와 같이 앞선 질문에 대헤 일반적으로 기대되는 정보를 전달하고자 쓰인 보통의 대답들은 `:mode`를 동반하지 않는다는 것을 유의하세요. 그러나 응원하는 팀이 중요한 시점에서 득점을 했다거나 하는 상황에서 자축하는 의미로 쓰인 `그렇지!!!` 같은 것은 `:mode expression`를 동반해야 합니다.

~~~lisp
(그 / 그렇-01 :mode expression)
~~~
> 그렇지!!!
>
> 그래!!!


## 지시사, 복수형, 시제, 상, 인용, 하이픈 ([Articles, plurals, tense, aspect, quotes, hyphens](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#articles-plurals-tense-aspect-quotes-hyphens))

AMR은 (명시적인 `:time` 관계 외에) 시제나 상, 복수(흔히 접미사 '-들'), 인용 부호(") 등을 표상하지 않습니다. 

~~~lisp
(가 / 가-01  
    :ARG0 (소 / 소년))
~~~
> 소년이 갔다.
>
> 소년이 갔었다.
>
> 소년이 간다.

~~~lisp
(예 / 예정-01
    :ARG1 (가 / 가-01  
        :ARG0 (소 / 소년)))
~~~
> 소년이 갈 예정이다.
>
> 소년이 갈 것이다.

일반적으로 복수는 표상하지 않습니다. 

~~~lisp
(좋 / 좋-01
    :ARG1 (아 / 아이))
~~~
> 좋은 아이들이네요.

접미사 '-들'이 붙어 **한 단어가 된 말**은 그대로 씁니다. (사전 등재어 기준으로 판단하세요.)

~~~lisp
(보 / 보-01
    :ARG0 (그 / 그)
    :ARG1 (그2 / 그들))
~~~
> 그는 그들을 보았다.

지시관형사는 표상합니다.

~~~lisp
(소 / 소년
    :mod (저 / 저))
~~~
> 저 소년
>
> 저 소년들

~~~lisp
(소 / 소년
    :mod (이 / 이))
~~~
> 이 소년
>
> 이 소년들

English AMR에서 관사(article) 'a' 또는 'an'이 누락되는 것처럼, 한국어의 수관형사는 누락됩니다.

~~~lisp
(가 / 가-01  
    :ARG0 (소 / 소년))
~~~
> 한 소년이 가고 있다.

~~~lisp
...
    :location (마 / 마을
        :mod (근 / 근방
            :op1 (이 / 이)))
...
~~~
> 이 근방의 한 마을에서는 ...

그러나 단위 명사를 동반하는 수관형사 또는 수사는 `:quant`로 표상해야 합니다.

~~~lisp
(소 / 소년
    :quant 1
    :unit (명 / 명))
~~~
> 소년 한 명

~~~lisp
(소 / 소년 :quant 1)
~~~
> 소년 하나

지시대명사는 문장 내에 선행사가 없다면 표상합니다.

~~~lisp
(모 / 모자  
    :domain (이 / 이것))
~~~
> 이것은 모자이다.

~~~lisp
(다 / 다람쥐
    :domain (녀 / 녀석
        :mod (이 / 이)))
~~~
> 이 녀석은 다람쥐입니다.

과거, 현재, 미래 등의 시제(tense)나 진행, 완료 등의 상(aspect)은 나타내지 않습니다. 따라서 아래의 문장들은 하나의 AMR이 됩니다.

~~~lisp
(작 / 작동
    :ARG1 (기 / 기계))
~~~
> 기계가 작동 중이다.
>
> 기계가 작동하고 있다.
>
> 기계가 작동한다.
>
> 기계가 작동했다.
>
> 기계가 작동했었다.

하이픈이 포함된 단어를 분절하여 처리해도 무방한 경우에는 그렇게 합니다. 

~~~lisp
(이 / 이어가-01
    :ARG1 (협 / 협력-01
        :ARG0 (u / university :wiki "연세대학교" :name (이 / 이름 :op1 "연세대"))
        :ARG1 (u2 / university :wiki "고려대학교" :name (이2 / 이름 :op1 "고려대")))
~~~
> 연세대-고려대 협력 이어간다.

**참고:** 한국어에서는 하이픈(-)을 자주 쓰지 않습니다. 특히 국립국어원에서는 하이픈이 들어간 외국어 단어를 외래어로 수용할 때 하이픈을 무시하고 붙여쓰도록 정해 놓았습니다.(예: Stratford-upon-Avon → 스트랫퍼드어폰에이번) 이런 경우에는 하이픈을 그대로 표기하면 잘못된 외래어 표기가 되지요.

그러나 구성소들의 의미를 개별적으로 처리할 수 없다면 하이픈을 포함한 개념을 씁니다.

~~~lisp
(코 / 코시-슈바르츠-부등식)
~~~
> 코시-슈바르츠 부등식

AMR에서 쓰이는 "-"는 실제 표면형의 하이픈과는 전혀 별개의 것일 수 있음에 유의하세요. 예를 들어 관용구 같은 것은 "-"를 활용해야 할 때도 있습니다.

~~~lisp
(보 / 보-01
    :mod (보2 / 보자-보자-하니까)
    :domain (나 / 나)
    :ARG1 (보3 / 보자기))
~~~
> 보자 보자 하니까 내가 보자기로 보이나!

어떠한 경우에도 AMR의 일급 개념(first-concept)으로 하이픈 그 자체("-")를 쓰는 일은 없습니다.

위에서 봐왔던 요령들은 가운뎃점(·)의 경우에도 마찬가지겠죠. (복합명사나 명사 연쇄 등 명사 복합체의 경우도 마찬가지입니다.)
~~~lisp
(w / world-region
    :wiki "아시아_태평양" 
    :name (이 / 이름 :op1 "아시아·태평양지역"))
~~~
> 아시아·태평양지역

## 높임과 공손성

한국어 AMR에서 높임과 낮춤은 구분하지 않습니다. 사물 존대나 압존법 역시 고려되지 않습니다.

~~~lisp
(묻 / 묻-01
    :mode imperative
    :ARG1 (t / truth-value
        :polarity-of (먹 / 먹-01
            :ARG0 (할 / 할머니)
            :ARG1 (밥 / 밥)))
    :ARG2 할
    :mod (우 / 우선)
    :condition (돌아오 / 돌아오-01
        :ARG0 할))
~~~
> 할머님께서 돌아 오시면, 우선 진지는 드셨는가부터 할머님께 여쭤 보세요.

위 AMR에서 '진지'는 `밥`으로, '할머님'은 `할머니`로, '돌아 오시다'는 단순히 `돌아오-01`로, '드시다'는 `먹-01`로, '여쭙다'는 `묻-01`로 처리한 것을 볼 수 있습니다.

단순한 존칭으로 쓰인 '-님'이나 '-분' 등은 AMR에 포함시키지 않습니다. 그러나 "사모님", "선생님" 같이 한 단어로 굳어진 존칭어는 그대로 쓸 수 있습니다.

~~~lisp
(들 / 들어오-01
    :mode imperative
    :ARG0 (환 / 환자
        :ord (다 / 다음)))
~~~
> 다음 환자분 들어 오세요.

~~~lisp
(오 / 오-01
    :ARG0 (선 / 선생님))
~~~
> 선생님 오신다!

높임이 늘 어떤 대상을 높일 의도로만 쓰이는 것은 아닙니다. 반말이 아니라고해서 `:polite +`를 주석할 수는 없죠.

~~~lisp
(보 / 보내-01
    :ARG1 (수 / 수표)
    :ARG2 (사 / 사무실
        :poss (나 / 나))
    :manner (합 / 합의-01
        :polarity -
        :ARG0 나))
~~~
> 저랑 합의도 없이 제 사무실에다 수표를 보내셨습디다?

공손성은 `:polite +`로 주석합니다. 대개 '-어 주다'와 같은 표현을 쓸 때가 해당됩니다. 그러나 어떤 종결 어미가 쓰이는가에 따라 느껴지는 공손성의 정도가 달라질 수 있습니다.

~~~lisp
(가 / 가져오-01
    :mode imperative
    :ARG1 (책 / 책
        :ARG1-of (읽 / 읽-01)))
~~~
> 읽을 책을 가져오세요.

~~~lisp
(가 / 가져오-01
    :mode imperative
    :polite +
    :ARG1 (책 / 책
        :ARG1-of (읽 / 읽-01)))
~~~
> 읽을 책을 가져와 주실래요?

~~~lisp
(가 / 가져오-01
    :mode imperative
    :ARG1 (책 / 책
        :ARG1-of (읽 / 읽-01)))
~~~
> 읽을 책을 가져와 줘.

~~~lisp
(가 / 가져오-01
    :mode imperative
    :polite +
    :ARG1 (책 / 책
        :ARG1-of (읽 / 읽-01)))
~~~
> 읽을 책을 가져와 줄 수 있을까?


## 암시된 역할 ([Implicit roles](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#implicit-roles))

역할(role)은 막상 한국어로 옮겼을 때 생략된 상태일 수 있습니다. AMR은 현실에서 발생 가능한 사건과 관련하여 실제 언급이 없는 경우에도 그러한 역할들을 포함합니다. (더 해석적인 선택이죠.)
~~~lisp
(기 / 기소-01
    :ARG1 (그 / 그)
    :ARG2 (a / and
        :op1 (주 / 주폭)
        :op2 (저 / 저항-01
            :ARG0 그
            :ARG1 (체 / 체포-01
                :ARG1 그))))
~~~
> 그는 주폭과 체포 저항으로 기소되었다.

여기서 변항(variable) `그`가 여러번 나타나는 것을 볼 수 있습니다. 이 문장에서는 `그`가 다른 사람이 아닌 '그 자신'의 체포에 저항한 것이 자명하므로, `체포-01`의 `ARG1`은 `그`가 됩니다. 그렇지만 기소한 주체와 구속한 주체가 동일한지에 대해서는 확신할 수 없기 때문에 그런 것까지는 표현하지 않았습니다.


## 암시된 개념 ([Implicit concepts](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#implicit-concepts))

텍스트로부터 AMR을 만들때, 암시된 역할은 포함하지만 일반적으로 암시된 개념을 포함하지 않습니다. 아래 `일으키-01`을 보세요:

~~~lisp
(흥 / 흥미롭-01             NOT: (일 / 일으키-01
    :ARG1 (구 / 구성))               :ARG0 (구 / 구성)
                                    :ARG1 (흥 / 흥미))
~~~
> 구성이 흥미롭다.

단, 개체명 타입(named entity types)은 예외입니다. 아래 [개체명과 위키피케이션](#%EA%B0%9C%EC%B2%B4%EB%AA%85%EA%B3%BC-%EC%9C%84%ED%82%A4%ED%94%BC%EC%BC%80%EC%9D%B4%EC%85%98-named-entities-and-wikification) 챕터에서 다룹니다.


## 지정사 '-이다'와 계사적 쓰임을 갖는 '있다' ([Main verb "be"](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#main-verb-be))

이 챕터는 English AMR 주석 지침의 [Main verb "be"](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#main-verb-be)의 내용을 한국어의 상황에 맞게 옮겨온 것으로, [Choe et al. 2019](https://www.aclweb.org/anthology/W19-3314)의 내용을 재구성한 것입니다. 

한국어의 지정사 '-이다'는 서술격 조사로 분류되지만 서술성을 갖고 활용을 합니다. 하지만 지정사 '-이다'는 계사(copula)로서 고정된, 혹은 독자적인 의미 프레임을 갖지 않습니다. 지정사문(또는 계사문)의 개념 구조는 '-이다'가 담당하지 않습니다. 따라서 '-이-' 자체가 노드가 되는 경우는 없습니다.

문장의 의미를 해석적으로 표상하는 것은 계사문에서도 마찬가지입니다. 아래 문장에서는 서술성 명사에 '-이-'가 붙어 서술어가 되었지만, 통사적인 현상을 그대로 드러내는 것은 AMR이 할 일이 아닙니다.

~~~lisp
(담 / 담당-01
    :ARG0 (나 / 나)
    :ARG1 (부 / 부분
        :mod (그 / 그)))
~~~
> 그 부분이 내 담당**이**다.
>
> 내가 그 부분을 담당하고 **있**다.
>
> 나는 그 부분을 담당한다.

위 문장에서 "그 부분"을 `:domain`으로 처리하지 않은 것에 유의하세요. 다음의 예들도 확인합시다.

~~~lisp
(남 / 남자
    :age 32
    :time (올 / 올해))
~~~
> 남자는 올해로 서른 둘**이**다.

~~~lisp
(걱 / 걱정-01
    :ARG0 (고 / 고양이
        :ARG0-of (나 / 나가-01
            :ARG2 (집 / 집))))
~~~
> 집 나간 고양이가 걱정**이**다.
>
> 집 나간 고양이가 걱정된다.

~~~lisp
(프 / 프린터
    :location (사 / 사무실)
    :quant 3)
~~~
> 사무실에 프린터가 세 대(**이**)다.
>
> 세 대의 프린터가 사무실에 있다.

위에서 보는 바와 같이 계사적인 쓰임을 갖는 존재사 '있다'는 `있-01`과 같은 프레임을 활용하지 않고 단순하게 나타낸다는 점에 유의하세요.

~~~lisp
(다 / 다람쥐)
~~~
> 다람쥐
>
> 다람쥐다.
>
> 다람쥐가 있다.
> 
> 다람쥐가 있다람쥐!

아래와 비교해 봅시다.

~~~lisp
(다 / 다람쥐
    :location (저 / 저기))
~~~
> 저기에 다람쥐가 있다.

Korean Propbank에 적절한 용언 프레임이 없다면 `-00`을 붙이고 해석을 시도하세요. 이때 비슷한 의미를 가진 유의어의 roleset을 참고하여 `:ARGX` 역할을 주석하는 것은 괜찮습니다. 그러나 마땅치 않은 경우에는 `:domain`을 활용하는 것이 일반적인 접근입니다.

~~~lisp
(아 / 아니꼽-00                 OR: (아 / 아니꼽-00
    :ARG1 (눈 / 눈빛))                :domain (눈 / 눈빛))
~~~
> 눈빛이 아니꼽군.

**참고**: English AMR에서는 보어로 쓰인 형용사의 처리와 관련하여 적절한 프레임이 OntoNotes에 등재되지 않은 경우 `-00`없이 개념 노드로 씁니다. (예: `small`) 그러나 한국어의 형용사는 동사와 함께 용언 범주를 이루고 스스로 서술어로 쓰이기 때문에, 한국어 지침에서는 `-00`을 붙입니다. (추후에 주석자들이 `-00`으로 처리한 것을 모으면 확장된 용언 프레임을 추가로 등재하는 데에 도움이 될 것입니다.)

'무엇이 무엇이다'의 구성 역시 `:domain`을 활용합니다.

~~~lisp
(변 / 변호사
    :domain (남 / 남자
        :mod (그 / 그)))
~~~
> 그 남자는 변호사다.

~~~lisp
(남 / 남자
    :mod (그 / 그)
    :mod (변 / 변호사))
~~~
> 변호사인 그 남자

어떤 단어들은 품사통용어입니다. 부사도 명사처럼 쓰일 때가 있죠. 용언이 아니라면 `-00`은 붙이지 않습니다.

~~~lisp
(별 / 별로
    :domain (성 / 성격))
~~~
> 성격이 별로야.

계사 '-이-'는 용언이 아니지만 그 부정은 어휘화된(lexicalized) '아니-'입니다. '아니-'는 형용사로 엄연한 용언이지요. 하지만 `아니-01`을 활용하지 않고 `:polarity`를 씁니다. [부정](#%EB%B6%80%EC%A0%95-negation)에서 '있다'-'없다', '알다'-'모르다'를 어떻게 처리했는지를 떠올려 보세요.

~~~lisp
(변 / 변호사
    :polarity -
    :domain (남 / 남자
        :mod (그 / 그)))
~~~
> 그 남자는 변호사가 아니다.

~~~lisp
(다 / 다람쥐
    :polarity -
    :location (저 / 저기))
~~~
> 저기엔 다람쥐가 없다.

[양화사와 작용역](#%EC%96%91%ED%99%94%EC%82%AC%EC%99%80-%EC%9E%91%EC%9A%A9%EC%97%AD-quantifiers-and-scope)에서 다시 언급하겠지만, 부정의 작용역을 어떻게 줄 것인가가 혼란스러울 수 있습니다. '다람쥐가 있긴 있지만 저기에 없는 것'이라면 `:polarity`는 `저기`에 놓여야 하는 것이 아닐까 하는 고민이 들 수도 있지요. ('저기가 아닌 곳에 다람쥐가 있다?') 

**참고**: 작용역을 적절하게 다루는 방법은 최근에서야 DMR@ACL2019에서 제안된 바가 있고, 곧 세부 요령이 업데이트 될 것입니다.

'~ 것이다' 구성의 분열문(cleft sentence) 역시 '것'을 따로 표상하지는 않습니다.

~~~lisp
(이 / 이야기-01
    :manner (정 / 정직-01)
    :domain (선 / 선택-01
        :mod (최 / 최선)))
~~~
> 최선의 선택은 정직하게 얘기하는 것이다.

~~~lisp
(문 / 문제
    :domain (녹 / 녹-01
        :ARG1 (빙 / 빙하)))
~~~
> 빙하가 녹는 것은 문제다.

~~~lisp
(문 / 문제
    :polarity -
    :domain (녹 / 녹-01
        :ARG1 (빙 / 빙하)))
~~~
> 빙하가 녹는 것은 문제가 아니다.

'아니-'와 관련해서 때로는 문제가 생길 수 있습니다. "X는 Y가 아니다"의 구성에서 Y에 분열문이 오는 경우 부적절한 표상이 될 위험이 있습니다. 예를 들어 *"문제는 빙하가 녹는 것이 아니다."* 라는 문장을 표상하려고 아래와 같은 AMR을 작성했다고 합시다.

~~~lisp
INAPPROPRIATE:
(녹 / 녹-01
    :polarity -
    :ARG1 (빙 / 빙하) 
    :domain (문 / 문제))
~~~
> 문제는 빙하가 녹는 것이 아니다. (...?)

위 표상은 오히려 ***"문제는 빙하가 녹지 않는 것이다."*** 에 가깝습니다. 

이런 경우에는 `have-mod-91`과 `:polarity`를 조합하여 주석합니다. (이 작업이 복잡하게 느껴진다면 왼쪽과 같이 `아니-01`를 활용해도 좋습니다. 물론 이 경우에는 후처리가 필요할 것입니다. 그러나 `:polarity`를 명시한다는 점에서 `have-mod-91`는 AMR Policy에 가까운 방법이 될 수 있습니다.)

~~~lisp
(h / have-mod-91            OR: (아 / 아니-01
    :polarity -                      :ARG1 (문 / 문제)
    :ARG1 (문 / 문제)                 :ARG2 (녹 / 녹-01
    :ARG2 (녹 / 녹-01                     :ARG1 (빙 / 빙하)))
        :ARG1 (빙 / 빙하)))
~~~
> 문제는 빙하가 녹는 것이 아니다.


## 동사 파생이 될 수 있는 서술성 명사 ([Nouns that invoke predicates](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#nouns-that-invoke-predicates))

이 챕터는 [Nouns that invoke predicates](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#nouns-that-invoke-predicates)의 내용을 바탕으로 한국어의 상황에 맞게 재구성한 것입니다. 여기서는 특히 서술성 명사를 어떻게 처리할 것인가를 자세히 다룹니다.

AMR의 원칙은 실제 단어의 품사를 따지기 보다 Korean PropBank의 용언 프레임을 최대한으로 활용하는 것입니다. AMR은 동사가 아닌 개념을 표상하는 것이므로, "연기"와 "연기하다"는 같은 AMR로 표상됩니다. AMR은 주석 일관성을 위해서 갈래뜻이 붙은(sense-tagged) KPB 용언 프레임을 활용합니다.

~~~lisp
(연 / 연기-01
    :ARG0 (g / government-organization :name (이 / 이름 :op1 "국방부"))
    :ARG1 (발 / 발표-01
        :ARG0 g)
    :manner (거 / 거듭하-00))
~~~
> 국방부 발표 거듭 연기

~~~lisp
(표 / 표출-01
    :ARG0 (소 / 소년)
    :ARG1 (불 / 불만-01
        :ARG1 소))
~~~
> 소년은 자기의 불만을 표출했다.
>
> 소년의 불만 표출
>
> 소년 자신의 불만 표출

이렇게 `표출-01`를 활용함으로써 의미론적 프레임을 일관되게 드러낼 수 있게 됩니다.

정리하자면, **서술성 명사인 경우에는 단순한 명사로 취급하지 않는 것이 중요합니다.** 

~~~lisp
(파 / 파괴
   …)
~~~
이렇게 하면 안됩니다.

"파괴"가 미등재어일 때에는 차라리,

~~~lisp
(파 / 파괴-00
   …)
~~~
이렇게 하는 것이 좋습니다.

[Korean PropBank](https://catalog.ldc.upenn.edu/LDC2006T03)는 2006년에 공개된 자원으로, 모두 2,749개의 용언 프레임만을 담고 있습니다. 주석을 할 때에 꽤 많은 경우가 미등재어일 것입니다. 미등재어를 처리할 때에는 아래와 같이 처리하는 것이 좋습니다.

동사 파생 접미사 '-하다', '-되다', '-시키다', '-받다', '-당하다' 등에 의해 동사 파생이 가능한 명사류는 어근(root)이 되는 명사를 토대로 미등재어 처리를 합니다.

~~~lisp
(조 / 조회-00
    :mode imperative
    :location (지 / 지점
        :ARG1-of (가 / 가깝-01)))
~~~
> 가까운 지점에서 조회하세요.

~~~lisp
(고 / 고통-00
    :ARG1 (아 / 아이))
~~~
> 아이들은 고통당하고 있다.
>
> 아이들이 고통받고 있다.

'-화(化)'에 의해 명사 파생된 명사가 다시 동사 파생 될 수 있는 경우에는 "~화"까지 어간(stem)으로 보고 미등재어 처리합니다. (KPB 등재어인 `구체화-01`, `정당화-01` 등과 같은 요령으로 취급하기 위함입니다. '슬럼화'와 같은 경우도 "슬럼화하다", "슬럼화되다" 모두 가능하다는 점을 상기해 보세요.)

~~~lisp
(슬 / 슬럼화-00
    :ARG1 (지 / 지역))
~~~
> 지역이 슬럼화되었다.

일부 명사 전성된 단어들은 (예: 죽음) 사건 전체를 가리키기도 하며, 또 어떤 명사들은 개념과 결부된 역할(role)을 상기시키기도 합니다.

~~~lisp
(죽 / 죽-01)
~~~
> 죽음

~~~lisp
(안 / 안건
    :ARG1-of (요 / 요청-01))
~~~
> 요청안
>
> 요청된 안건
>
> 요청 안건

명사로서의 쓰임이 용언으로 쓰일 때보다 더 빈도가 높더라도, AMR을 작성하기 전 KPB 용언 프레임을 꼭 한번씩 검색해 보세요. `공통-01` 같은 경우가 또 있을지 모릅니다.

~~~lisp
(의 / 의견
    :ARG1-of (공 / 공통-01))
~~~
> 공통 의견
>
> 공통된 의견
>
> 공통인 의견

역관계는 '-자(者)', '-인(人)', '-사(社)' 명사들에도 많이 쓰입니다. 아래와 같이 역관계를 활용하는 요령은 단순히 `:mod`나 `:poss` 등을 활용하는 것보다 KPB 용언 프레임의 활용성을 극대화시키는 효과가 있습니다.

~~~lisp
(사 / 사람
    :ARG0-of (제 / 제안-01))
~~~
> 제안자

~~~lisp
(사 / 사람
    :ARG0-of (신 / 신청-01
        :ARG1 (민 / 민원)))
~~~
> 민원 신청인

~~~lisp
(사 / 사람
    :ARG0-of (투 / 투자-01))
~~~
> 투자자

~~~lisp
(회 / 회사
    :ARG0-of (제 / 제조-01
        :ARG1 (자 / 자동차)))
~~~
> 자동차 제조사

**참고**: 모든 경우에 함축된 개념을 되살려야 하는 것은 아닙니다. '근무자'는 `사람`과 `근무-01`로 일반화하는 것이 좋습니다. 그러나 '직원'은 `직원`으로 씁니다. English AMR에서 'teacher'는 '-er'류 명사로 보고 `(p / person :ARG0-of (t / teach-01))`로 쓰지만 한국어 AMR에서는 단순히 `교사`를 씁니다.

실제 통용되는 뜻이 다른 경우에는 분석하지 않고 그대로 씁니다. 예를 들어 "현금사냥꾼"은 정말로 사냥을 업으로 하는 사람이 아니겠지요.

~~~lisp
(현 / 현금사냥꾼)           NOT: (사 / 사람
                                    :ARG0-of (사 / 사냥-00
                                            :ARG1 (현 / 현금)))
~~~

'-자(者)' 명사들의 의미를 분절적으로 표상하기 쉽더라도, 언제나 역관계를 활용하는 것이 최선인 것은 아닙니다. 예를 들어서 "그는 성실한 근무자다."와 같은 문장은 단순히 '그는 성실하게 근무한다'는 의미입니다. `사람`등을 굳이 루트로 둘 필요가 없다면 AMR을 쉽게 쓰세요.

~~~lisp
(근 / 근무-01                   NOT: (그 / 그
    :ARG0 (그 / 그)                     :ARG0-of (근 / 근무-01
    :manner (성 / 성실-01))                     :manner (성 / 성실-01)))
~~~
> 그는 성실한 근무자다.
>
> 그는 성실하게 근무한다.

## 형용사 파생 및 보조 형용사 ([Adjectives that invoke predicates](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#adjectives-that-invoke-predicates))

"군인답다", "자유롭다", "어른스럽다", "행복하다", "감쪽같다", "맛있다"와 같이, '-답다', '-롭다', '-스럽다', '-하다', '-같다', '-있다' 등에 의한 형용사 파생이 가능한 명사들도 [동사 파생이 될 수 있는 서술성 명사](#%EB%8F%99%EC%82%AC-%ED%8C%8C%EC%83%9D%EC%9D%B4-%EB%90%A0-%EC%88%98-%EC%9E%88%EB%8A%94-%EC%84%9C%EC%88%A0%EC%84%B1-%EB%AA%85%EC%82%AC-nouns-that-invoke-predicates) 챕터에서 설명한 바와 같이 다룹니다.

~~~lisp
(중 / 중요-01
    :ARG1 (행 / 행복-01
        :ARG1 (가 / 가정)))
~~~
> 가정의 행복이 중요하다.
>
> 가정이 행복한 것이 중요하다.

~~~lisp
(살 / 살-01
    :manner (자 / 자유롭-01))
~~~
> 자유롭게 살고 있습니다.

~~~lisp
(좋 / 좋-02
    :ARG0 (나 / 나)
    :ARG1 (사 / 사람
        :ARG1-of (어 / 어른스럽-00)))
~~~
> 저는 어른스러운 사람이 좋아요.
>
> 저는 어른스러운 사람을 좋아해요.

~~~lisp
(행 / 행동-01
    :mode imperative
    :manner (군 / 군인답-00))
~~~
> 군인답게 행동해라.

~~~lisp
(음 / 음식
    :ARG1-of (맛 / 맛있-00))
~~~
> 맛있는 음식

"불안감", "자신감", "기대감", "책임감"과 같이 일부 '-감(感)'이 붙는 명사들은 적당한 용언 프레임이 있는 경우가 흔합니다.

~~~lisp
(불 / 불안-01
    :mod (조 / 조금)
    :ARG1 (나 / 나))
~~~
> 나는 조금 불안감이 있다.
>
> 나는 조금 불안하다.

~~~lisp
(책 / 책임지-01
    :ARG1 (그 / 그)
    :ARG2 (일 / 일하-01
        :ARG0 그))
~~~
> 그는 자기 일에 책임감이 있다
>
> 그는 자기 일에 책임을 진다.
>
> 그는 자기 일을 책임지고 한다.

이런 방식을 쓰면 다소 기능적인 역할만을 하는 '하다', '있다', 등의 기본 동사를 사용하지 않고도 간단하게 AMR을 작성할 수 있습니다. 예를 들어 "책임지고 한다"를 표상하기 위해 `하-01`를 루트로 놓고 시작할 필요가 없는 것이죠.

형용사 프레임에서 `ARG1`은 보통 그 형용사의 의미를 띄는 대상을 가리킵니다. 일부 심리형용사에서 어떠한 감정을 불러 일으키는 역할(causer)이 따로 있다면 `ARG0`이 있을 수 있으며, 그러한 행동주가 없는(not agentive) 경우에는 대개 `ARG1`, `ARG2`의 순서로 roleset이 결정됩니다.

"까매지다", "슬퍼지다", "자유로워지다"와 같이 '-아/어지다'가 붙은 말은 어떻게 해야 할까요? 어떤 것이 현재 까맣다는 것이 반드시 까맣게 된 것이라고 보기는 어렵습니다. (그래서 `까맣-01`만 단독으로 쓸 수는 없겠죠.) KPB에 직접 활용할 수 있는 프레임이 없다면 `-00`을 붙여 미등재어 처리를 하거나, `되-01`을 활용하는 방법이 적당해 보입니다.

~~~lisp
(되 / 되-01
    :ARG1 (얼 / 얼굴)
    :ARG2 (까 / 까맣-01))
~~~
> 얼굴이 까매졌다.

어떤 명사들은 보조형용사 '직하다', '만하다'와 함께 쓰이기도 합니다. 이런 단어들은 단순하게 `예상-01`이나 `가능-01`, `권유-01` 등을 활용하여 처리합니다.

~~~lisp
(예 / 예상-01
    :ARG1 (도 / 도착-01
        :ARG1 (그 / 그)
        :time (이 / 이제)))
~~~
> 이제는 그가 도착했음 직하다.

~~~lisp
(가 / 가능-01
    :ARG1 (신 / 신뢰-01
        :ARG1 (그 / 그)))
~~~
> 그는 신뢰할 만한 사람이다.

~~~lisp
(권 / 권유-01
    :ARG1 (먹 / 먹-01
        :ARG1 (음 / 음식
            :mod (그 / 그))))
~~~
> 그 음식은 먹어볼 만하다.


## 이중주어문과 이중목적어문

이 챕터는 한국어 문장에서 주격이나 목적격이 중출(case-stacking)하는 구문들을 처리하는 방법을 다룹니다. ([Choe et al. 2019](https://www.aclweb.org/anthology/W19-3314)) 

한 서술어에 대해 주격 조사 '-이/가'(또는 보조사 '-은/는')이 두 번 이상 드러나는 문장을 이중주어문이라 하며, '-을/를'이 두 번 이상 드러나는 문장을 이중목적어문이라고 합니다. AMR에서는 대부분의 경우 어느 하나의 중출 성분을 부가역으로 처리할 수 있습니다.

~~~lisp
(덥 / 덥-01
    :ARG1 (날 / 날씨)
    :time (어 / 어제))
~~~
> 어제가 날씨가 더웠다.

~~~lisp
(좋 / 좋-02
    :ARG0 (나 / 나)
    :ARG1 (그 / 그))
~~~
> 나는 그가 좋다.

위 문장들은 마치 주어가 2개인 것처럼 보이지만, 그 의미를 생각하면 적당한 관계를 할당하는 것이 어렵지 않습니다. 이런 요령은 이중목적어문에서도 마찬가지로 적용됩니다.

~~~lisp
(자 / 자르-01
    :ARG0 (그 / 그녀)
    :ARG1 (발 / 발톱
        :part-of (고 / 고양이)))
~~~
> 그녀는 고양이를 발톱을 잘라 주었다.

~~~lisp
(주 / 주-01
    :ARG0 (할 / 할머니) 
    :ARG1 (구 / 구두
        :ARG1-of (아 / 아끼-01
            :ARG0 할)
    :ARG2 (나 / 나))
~~~
> 할머니는 아끼시던 구두를 나를 주셨다.

간혹 개념 간의 관계를 뚜렷하게 정하지 못할 때도 있습니다. 그럴 때에는 `:domain`을 활용합니다. `:domain`은 주로 가장 바깥의 주어나 목적어에 할당됩니다. `:poss`나 `:part-of`를 써도 될지 확신이 없다면 좋은 대안이 됩니다. 

~~~lisp
(좋 / 좋-01
    :ARG1 (향 / 향)
    :domain (와 / 와인))
~~~
> 와인은 향이 좋다.

~~~lisp
(뽑 / 뽑-01
    :ARG1 (꽝 / 꽝)
    :domain (제 / 제비))
~~~
> 제비를 꽝을 뽑았다.

보조사 '-은/는'과 주격 조사 '-이/가'는 분포가 상당히 비슷합니다. "와인이 향이 좋다"는 어떻게 표상해야 할까요?

우선 "와인"이 특정한 대상을 가리키는 경우라면 (예: 발화자의 눈 앞에 있는 와인 한 잔) 아래와 같이 표상하는 것이 바람직합니다. 

~~~lisp
(좋 / 좋-01
    :ARG1 (향 / 향
        :poss (와 / 와인
            :mod (이 / 이))))
~~~
> 이 와인이 향이 좋다.
>
> 이 와인의 향이 좋다

~~~lisp
(좋 / 좋-01
    :ARG1 (향 / 향
        :poss (와 / 와인)))
~~~
> (특정할 수 있는 어떤) 와인이 향이 좋다.
>
> (와인을 한 모금 마신 후) 와인의 향이 좋군요.

그러나 "와인은 (일반적으로) 향이 좋다."와 같은 의미라면 '와인이 어떠하다' + '향이 좋다'로 봅니다. (서술절 내포문)

~~~lisp
(좋 / 좋-01
    :ARG1 (향 / 향)
    :domain (와 / 와인))
~~~
> 와인이 향이 좋아. (다른건 안 좋아.)

이러한 해석에 대해서 `:topic`을 활용하지 않는다는 것에 유의하세요. `:topic`의 쓰임새는 제한적입니다.

"나는 짜장면!"이라는 문장에 대해서 '나는 짜장면을 먹겠다'의 의미라면 `(먹 / 먹-01 :ARG0 (나 / 나))`로 합니다. 그러나 문장의 의미를 특정하기 어려운 경우, 즉 '나'와 '짜장면' 사이의 관계를 특정할 수 없는 경우에는 `:domain`을 씁니다.

~~~lisp
(짜 / 짜장면
    :domain (나 / 나))
~~~
> 나는 짜장면!

## 압축적 서술과 명사 상당 어구

AMR 1.2는 명사-명사 관계나, 명사-형용사 관계에 대해 심층적인 해석을 제공하지 않습니다. 대개의 경우 `:mod`로 처리한다는 의미입니다.

~~~lisp
(인 / 인출
    :mod (자 / 자동
        :mod (현 / 현금)))
~~~
> 현금 자동 인출

그러나 언어 표현의 구조보다 '의미'를 표상한다는 목적을 생각했을 때, 아래와 같이 표상하는 것이 더 바람직한 AMR일 것입니다. (`인출-00`처럼 미등재어 처리를 해서라도 말이죠.)

~~~lisp
(인 / 인출-00
    :manner (자 / 자동)
    :ARG1 (현 / 현금))
~~~
> 현금 자동 인출
>
> 현금을 자동으로 인출

비록 정확하게 헤아리기 어려운 경우더라도, 어떤 말이 환기하는 개념을 '대강이나마' 짐작할 수 있을 것입니다. 아래 AMR에서 `(창 / 창조)`가 아닌 `(창 / 창조-01)`를 쓴 이유는 (그렇게 하지 않는 경우보다) '더 깊은 해석'이기 때문입니다.

~~~lisp
(경 / 경제
    :manner (창 / 창조-01))
~~~
> 창조 경제

신문 텍스트에 자주 나오는 복합 명사, 명사 연속 구성, 임시적인 합성 명사 등을 모두 `:mod`로 처리한다면 (주석 작업은 한결 쉽겠지만) AMR의 취지에 맞는 방법이라고 볼 수는 없습니다. 한국어 AMR에서는 압축적인 서술 또는 명사 상당 어구에 대해 (가능하다면) 해석적인 주석을 지향합니다.

~~~lisp
(a / and
    :op1 (발 / 발견-01
        :ARG1 (정 / 정황
            :mod (도 / 도피-00
                :ARG0 (인 / 인물
                    :ARG1-of (주 / 주요-01)))))
    :op2 (가 / 가속화-01
        :ARG1 (수 / 수사-01)))
~~~
> 주요인물 해외도피 정황 발견... 수사 가속화

~~~lisp
(지 / 지원-01
    :ARG1 (여 / 여성
        :ARG0-of (단 / 단절-01
            :ARG1 (경 / 경력))))
~~~
> 경력 단절 여성들에 대한 지원


## 어미, 접사에 의한 부사어 ([Adverbs with -ly](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#adverbs-with--ly))

부사어는 어간을 기준(stemming)으로 형용사 프레임을 활용하여 처리합니다.

~~~lisp
(관 / 관측-01
    :ARG1 (이 / 이동-01
        :ARG0 (군 / 군대)
        :manner (빠 / 빠르-01)))
~~~
> 군대가 빠르게 이동하는 것이 관측되었다.
>
> 군대의 빠른 이동을 관측하였다.
>
> 군대가 빨리 이동하고 있음이 관측되었다.


## 부가역 ([Non-core roles](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#non-core-roles))

지침 앞부분에서 `:time`이나 `:location`과 같은 역할들을 볼 수 있었습니다. AMR에는 다양한 부가역(non-core roles)들이 있습니다.

### [`:source`](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#source)
### [`:destination`](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#destination)

~~~lisp
(운 / 운전-01
    :ARG0 (그 / 그)
    :direction (서 / 서쪽)
    :source (c / city :wiki "창원" :name (아 / 이름 :op1 "창원"))
    :destination (c2 / city :wiki "목포" :name (이2 / 이름 :op1 "목포")))
~~~
> 그는 창원에서 목포를 향해 서쪽으로 운전했다.

### [`:path`](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#path)

~~~lisp
(운 / 운전-01
    :ARG0 (나 / 나)
    :destination (c / city :wiki "서울" :name (이 / 이름 :op1 "서울"))
    :path (r / road :wiki "경부고속도로" :name (이2 / 이름 :op1 "경부고속도로")))
~~~
> 나는 경부고속도로를 타고 서울로 운전했다.

~~~lisp
(운 / 운전-01
    :ARG0 (나 / 나)
    :path (터 / 터널))
~~~
> 나는 터널을 따라 운전했다.

### [`:beneficiary`](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#beneficiary)
### [`:accompanier`](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#accompanier)

~~~lisp
(부 / 부르-01
    :ARG0 (군 / 군인)
    :ARG1 (군 / 군가)
    :beneficiary (소 / 소녀)
    :time (가 / 가-01
        :ARG0 군
        :accompanier 소
        :destination (마 / 마을)))
~~~
> 군인은 소녀와 함께 마을로 가는 동안 소녀에게 군가를 불러 주었다.

### [`:topic`](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#topic)

주로 '무엇에 대해', '무엇에 관하여'와 같은 표현이나 과목명, 주제 등에 활용되는 역할입니다.

~~~lisp
(정 / 정보 :polarity -
    :topic (사 / 사건
        :mod (그 / 그)))
~~~
> 그 사건에 대해서 정보가 없다.

~~~lisp
(p / person :wiki "최현배" :name (이 / 이름 :op1 "최현배")
    :ARG0-of (h / have-org-role-91
        :ARG1 (u / university :wiki "연세대학교" :name (이2 / 이름 :op1 "연세대학교"))
        :ARG2 (교 / 교수
            :topic (국 / 국어국문학))))
~~~
> 연세대학교 국어국문학과 교수 최현배

### [`:duration`](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#duration)

~~~lisp
(일 / 일하-01
    :ARG0 (그 / 그)
    :duration (t / temporal-quantity
        :quant 2
        :unit (시 / 시간)))
~~~
> 그는 두 시간 동안 일했다.

### [`:instrument`](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#instrument)

`:instrument`는 일반적으로 도구, 장치, 무기 또는 손가락이나 주먹과 같은 신체 부위 등, 동작에 사용되는 물리적 대상물(physical object)을 다룹니다. 

어떤 것이 어떻게, 어떤 방식으로 이루어지는지 설명하고자 한다면 보다 일반적인 `:manner`를 사용해야 합니다.

~~~lisp
(먹 / 먹-01
    :ARG0 (나 / 나)
    :ARG1 (파 / 파스타)
    :instrument (포 / 포크))
~~~
> 나는 포크로 파스타를 먹었다.

~~~lisp
(감 / 감행-01
    :ARG0 (c / country :wiki "이라크" :name (이 / 이름 :op1 "이라크"))
    :ARG1 (공 / 공격-01
        :instrument (미 / 미사일)))
~~~
> 이라크가 미사일 공격을 감행했다.

### [`:medium`](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#medium)

`:medium`은 사용 언어뿐만 아니라 신문, TV 채널, 웹 서비스, YouTube, Facebook, 연설 등, 커뮤니케이션 수단에 활용됩니다.

~~~lisp
(이 / 이야기-01
    :ARG0 (그 / 그녀)
    :ARG2 (그2 / 그)
    :medium (l / language :wiki "영어" :name (이2 / 이름 :op1 "영어")))
~~~
> 그녀는 그에게 영어로 이야기했다.

~~~lisp
(발 / 발표-01
    :ARG0 (p / person :wiki "박지성" :name (이 / 이름 :op1 "박지성"))
    :ARG1 (출 / 출산-01
        :ARG1 (사 / 사람
            :ARG0-of (h / have-rel-role-91 
                :ARG1 p
                :ARG2 (딸 / 딸))))
    :medium (p2 / product :wiki "트위터" :name (이2 / 이름 :op1 "트위터")))
~~~
> 박지성이 트위터를 통해 딸의 출산을 발표했다.

### [`:manner`](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#manner)

`:manner`는 '그 일이 어떻게 이루어질 수 있었는가'에 대한 설명이 됩니다. `:instrument` 또는 `:medium`에 해당하지 않으면 `:manner`로 처리하면 됩니다.

~~~lisp
(노 / 노래-00
    :ARG0 (소 / 소년)
    :manner (아 / 아름답-01
        :degree (무 / 무척))

~~~
> 소년은 무척 아름답게 노래했다.

~~~lisp
(장 / 장식-01
    :ARG0 (그 / 그)
    :ARG1 (방 / 방)
    :manner (창 / 창의-00))
~~~
> 그는 방을 창의적으로 장식했다.

`:manner`는 어떤 일을 하기 위한 방법이나 행위가 되기도 하며, 때로는 수단을 나타내기도 합니다.

~~~lisp
(제 / 제안-01
    :ARG0 (사 / 사람
        :ARG0-of (h / have-org-role-91
            :ARG2 (시 / 시장)))
    :ARG1 (줄 / 줄-01
        :ARG1 (범 / 범죄)
        :manner (고 / 고용-01
            :ARG2 (사2 / 사람
                :ARG0-of (h2 / have-org-role-91
                    :ARG1 (경 / 경찰관))
                :mod (많 / 많-01)))))
~~~
> 시장은 많은 경찰관을 고용하여 범죄를 줄일 것을 제안했다.

`:manner`는 운송 수단에도 적용됩니다.

~~~lisp
(가 / 가-01
    :ARG0 (p / person :wiki - :name (이 / 이름 :op1 "현수"))
    :ARG4 (c / country :wiki "피렌체" :name (이2 / 이름 :op1 "피렌체"))
    :manner (기 / 기차))
~~~
> 현수는 기차를 타고 피렌체로 갔다.

### [`:purpose`](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#purpose)

~~~lisp
(가 / 가-01
    :ARG0 (그 / 그)
    :ARG3 (가2 / 가게)
    :purpose (사 / 사-01
        :ARG0 그
        :ARG1 (목 / 목재
            :purpose (담 / 담장
                :mod (새 / 새)))))
~~~
> 그는 새 담장을 위한 목재를 사려고 가게에 갔다.

### [`:cause`](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#cause)

~~~lisp
(속 / 속삭-00
    :ARG0 (소 / 소년)
    :manner (부 / 부드럽-00)
    :purpose (달 / 달래-01
        :ARG1 (소2 / 소녀))
    :cause (걱 / 걱정-01
        :ARG0 소2
        :ARG1 소))
~~~
> 소년은 소녀가 걱정됐기 때문에, 소녀를 달래고자 부드럽게 속삭였다.

참고: `:cause`와 `:cause-of`는 `cause-01`로 구체화(reification)됩니다. 간단히 `:cause`를 사용해도 됩니다.

### [`:concession`](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#concession)

~~~lisp
(계 / 계속-01
    :ARG1 (경 / 경기)
    :concession (내 / 내리-04
        :ARG1 (비 / 비)))
~~~
> 비가 내림에도 불구하고 경기는 계속되었다.
> 
> 비가 내렸지만 경기는 계속됐다.

~~~lisp
(두 / 두렵-01
    :ARG0 (그 / 그)
    :ARG1 (부 / 부하)
    :concession (수 / 수감-01
        :ARG1 그))
~~~
> 그가 수감되었음에도 부하들은 그를 두려워했다.

### [`:condition`](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#condition)

~~~lisp
(노 / 노래-00
    :ARG0 (소 / 소년)
    :condition (주 / 주-01
        :ARG1 (돈 / 돈)
        :ARG2 소))
~~~
> 소년은 돈을 받으면 노래할 것이다.
>
> 소년은 노래할 것이다. 돈만 준다면.
>
> 소년은 돈을 받아야 노래를 한다.

~~~lisp
(노 / 노래-00
    :ARG0 (소 / 소년)
    :polarity -
    :condition (주 / 주-01
        :ARG1 (돈 / 돈)
        :ARG2 소))
~~~
> 만약 돈을 주면 소년은 노래하지 않을 것이다.
>
> 소년에게 돈만 주지 않는다면 소년은 노래할 것이다.

AMR에서 `X :cause Y`는 X의 원인이 Y라는 것을 의미합니다. 따라서 `Y :cause-of X`는 Y가 X의 원인이라는 것을 의미하죠. (`:cause` 또는 `:cause-of` 대신 `cause-01` 개념을 사용할 수 있습니다. [구체화](#%EA%B5%AC%EC%B2%B4%ED%99%94-reification) 챕터를 참고하세요.)

~~~lisp
(타 / 타격-01
    :ARG0 (어 / 어뢰)
    :cause-of (파 / 파손-01
        :ARG1 (선 / 선박)))
~~~
> 어뢰에 타격되어 선박이 파손되었다.
>
> 어뢰 타격에 의한 선박 파손

`:purpose`로부터 `:cause`를 따로 떼어서 생각하는 것이 어려울 수 있습니다. "그녀가 아프다고 해서 가고 있다."(원인), "그녀에게 소식을 전하려고 가고 있다."(의도)를 생각해 보세요.

때때로 연번이 부여된 `:ARGx` 필수역(numbered core roles)은 `:location`, `:beneficiary` 등과 같은 부가역과 일치할 수 있습니다. 이러한 경우에는 `:ARGx` 필수역을 사용합니다. 

예를 들면 오른쪽과 같이 주석하지 않습니다.

~~~lisp
(주 / 주-01                     NOT: (주 / 주-01
    :ARG0 (소 / 소년)                     :ARG0 (소 / 소년)
    :ARG1 (초 / 초콜릿)                    :ARG1 (초 / 초콜릿)
    :ARG2 (소2 / 소녀))                   :beneficiary (소2 / 소녀))
~~~
> 소년은 소녀에게 초콜릿을 주었다.

때로는 생성 사건(creation events)과 관련된 AMR에서 `:location`, `:time` 등이 수식해야 하는 것이 무엇인지 명확하지 않을 때가 있습니다. 이런 경우에는 생성물보다는 사건을 수식하는 것으로 봅니다.

~~~lisp
(짓 / 짓-01                           NOT: (짓 / 짓-01
    :ARG0 (그 / 그들)                           :ARG0 (그 / 그들)
    :ARG1 (다 / 다리)                           :ARG1 (다 / 다리 :location ...))
    :location (s / state 
        :wiki "메릴랜드주" 
        :name (이 / 이름 :op1 "메릴랜드주"))
    :time (d / date-entity :month 12))
~~~
> 메릴랜드주의 다리는 그들이 12월에 지은 것이다.
>
> 그들은 12월에 메릴랜드주에 다리를 지었다.

그 밖에 다른 부가역도 있습니다.

### [`:part`](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#part)

~~~lisp
(엔 / 엔진
    :part-of (자 / 자동차))
~~~
> 자동차의 엔진
>
> 자동차 엔진

~~~lisp
(부 / 부서
    :part-of (회 / 회사)
~~~
> 회사의 부서
>
> 회사 부서

회사의 CEO와 같은 구성원에게는 `:part`를 사용하지 않습니다.

~~~lisp
(남 / 남부
    :part-of (c / country :wiki "프랑스" :name (이 / 이름 :op1 "프랑스")))
~~~
> 프랑스의 남부
>
> 프랑스 남부

### [`:subevent`](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#subevent)

~~~lisp
(우 / 우승-00
    :ARG0 (소 / 소년)
    :ARG1 (계 / 계주
        :subevent-of (g / game :wiki "올림픽" :name (이 / 이름 :op1 "올림픽"))))
~~~
> 소년은 올림픽 계주에서 우승했다.

### [`:consist-of`](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#consist-of)

~~~lisp
(반 / 반지
    :consist-of (금 / 금))
~~~
> 금으로 된 반지
>
> 금반지

~~~lisp
(팀 / 팀
    :consist-of (원 / 원숭이)
~~~
> 원숭이로 이루어진 팀
>
> 원숭이 팀

### [`:example`](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#example-1)

~~~lisp
(기 / 기업
    :example (a / and
        :op1 (c / company :name (이 / 이름 :op1 "구글"))
        :op2 (c2 / company :name (이2 / 이름 :op1 "IBM"))))
~~~
> 구글과 IBM 같은 기업들

의존 명사 '등'은 '구글'이나 'IBM' 외에도 해당하는 것이 더 있음을 암시하므로 `:opN` 관계를 사용합니다.

~~~lisp
(기 / 기업
    :mod (i / IT)
    :example (등 / 등
        :op1 (c / company :name (이 / 이름 :op1 "구글"))
        :op2 (c2 / company :name (이2 / 이름 :op1 "IBM"))))
~~~
> 구글이나 IBM 등의 IT 기업들

### [`:direction`](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#direction)

~~~lisp
(운 / 운전-01
    :ARG0 (그 / 그)
    :direction (서 / 서쪽))
~~~
> 그는 서쪽으로 운전했다.

### [`:frequency`](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#frequency)

`:frequency`는 어떤 일이 얼마나 자주 발생했는지를 설명합니다.

~~~lisp
(만 / 만나-01
    :frequency 3
    :ARG0 (우 / 우리))
~~~
> 우리는 세 번 만났다.

특수 프레임 `rate-entity-91`은 "3,000 마일당" 또는 "갤런(gallon)당 $3"와 같이 거듭되는 사건이나 빈도를 가지는 개체를 표상하는 데 사용됩니다.

~~~lisp
(r / rate-entity-91
    :ARG1 2
    :ARG2 (t / temporal-quantity
        :quant 1
        :unit (년 / 년)))
~~~
> 매년 두 번씩
>
> 1년에 두 번

~~~lisp
(하 / 하-01
    :ARG0 (우 / 우리)
    :ARG1 (바 / 바둑)
    :frequency (r / rate-entity-91
        :ARG4 (d / date-entity
            :weekday (수 / 수요일)
            :dayperiod (오 / 오후))))
~~~
> 우리는 매주 수요일 오후에 바둑을 한다.

`rate-entity-91`의 필수역(core roles):

- `rate-entity-91`의 `:ARG1`은 수량입니다. (기본값: 1)
- `rate-entity-91`의 `:ARG2`는 일정 기준이 되는 수량(reference quantity)입니다. ("per quantity")
- `rate-entity-91`의 `:ARG3`은 반복 사건 간의 일정한 간격입니다. ("2달마다" - `:ARG2`보다 좀 더 구체적)
- `rate-entity-91`의 `:ARG4`는 반복적 사건이 일어나는 모든 개체입니다.

### [`:extent`](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#extent)

~~~lisp
(잇 / 잇-01
    :ARG0 (길 / 길)
    :extent (끝 / 끝없이))
~~~
> 길이 끝없이 이어진다.
>
> 길이 끝없이 이어져 있다.


## 초점 ([Focus](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#focus-1))

역관계(inverse relations)는 초점을 주기에 좋습니다. ([서론](#i-%EC%84%9C%EB%A1%A0-introduction)을 보세요.)

~~~lisp
(노 / 노래-00
    :ARG0 (소 / 소년
        :ARG0-of (오 / 오-01
            :ARG2 (학 / 학교))))
~~~
> 학교에서 온 소년이 노래했다.

~~~lisp
(소 / 소년
    :ARG0-of (노 / 노래-00)
    :ARG0-of (오 / 오-01
        :ARG2 (학 / 학교)))
~~~
> 학교에서 온 노래하는 소년
>
> 학교에서 온 노래하는 소년이 있다.

그러나 한국어에서 아래와 같은 관계절 구성은 자연스럽지 않습니다.

~~~lisp
???:
(학 / 학교
    :ARG2-of (오 / 오-01
        :ARG0 (소 / 소년
            :ARG0-of (노 / 노래-01))))
~~~
> 노래하는 소년이 온 학교 (노래하는 사람이 있던 곳은 학교라는 의미로)

이런 경우는 있을 수 있겠네요.

~~~lisp
(학 / 학교
    :source (소 / 소년
        :ARG0-of (노 / 노래-01)))
~~~
> 노래하는 소년의 학교

**참고**: 한국어의 동사 '오다'와 '가다'를 생각했을 때, "노래하는 소년이 온 학교"라는 표현의 '학교'는 '오다' 동사의 목적지(`:destination`)로 여겨질 수 있습니다. (화자의 위치가 '학교'인 경우 '노래하는 소년'을 언급할 때 목적지가 '학교'로 해석될 수 있습니다.) 이러한 현상 때문에 개별 어휘의 개념 구조를 따라 엄밀하게 표상하는 것이 중요합니다. (Predicate-sensitivity를 준수하세요.) 위의 예제에서는 `:ARG3-of`(end point)가 아닌 `:ARG2-of`(start point)로 주석하였습니다.

초점은 AMR의 최상위 노드(루트)에만 적용됩니다. 일단 루트가 결정되고 난 후에는 더 이상 초점에 대해 고려하지 않아도 됩니다. 다른 모든 나머지 개념들은 초점이 된 개념과의 의미론적 관계에 의해 자연히 따라 붙을 것입니다. 예를 들어 `(학 / 학교)`를 루트로 결정하면, `:ARG2-of`(`:source-of`)는 `노래-01`가 아닌 `오-01`로 결정되어야 합니다.

## 구체화 ([Reification](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#reification))

간혹 AMR에서의 관계들을 일급 개념(first-class concept)으로 다루고 싶을 때가 있을 것입니다. 역할을 개념으로 변환하는 것을 *구체화(reification)* 라고 합니다. 예를 들어 부가역 중 `:cause`는 `cause-01`로 대신할 수 있습니다. `X :cause Y`의 문법 대신에, `X :ARG1-of (c / cause-01 :ARG0 Y)`와 같은 표현을 쓸 수 있는 것입니다.

~~~lisp
구체화되지 않은 AMR:                  구체화된 AMR:
(떠 / 떠나-01                       (떠 / 떠나-01
    :ARG0 (여 / 여자)                   :ARG0 (여 / 여자)
    :cause (도 / 도착-01                :ARG1-of (c / cause-01
        :ARG1 (남 / 남자)))                 :ARG0 (도 / 도착-01
                                                :ARG1 (남 / 남자))))
~~~
> 남자가 도착했기 때문에 여자는 떠났다.

구체화 없는 AMR이 더 간단한데, 왜 구체화가 필요할까요? 첫째, 초점이 되는 AMR 조각(fragment)에 관계를 부여하기 위함입니다. 예를 들어 서랍 안에 칼이 있다는 것을 가정할 때, 우리는 칼에 초점을 둘 수 있습니다:

~~~lisp
(알 / 알-01
    :ARG0 (우 / 우리)
    :ARG1 (칼 / 칼
        :location (서 / 서랍)))
~~~
> 우리는 서랍 안에 칼이 있는 것을 안다. (???)

혹은 서랍에 초점을 둘 수도 있죠.

~~~lisp
(알 / 알-01
    :ARG0 (우 / 우리)
    :ARG1 (서 / 서랍
        :location-of (칼 / 칼)))
~~~
> 우리는 칼이 들어 있는 서랍을 안다. (???)

하지만 '위치' 자체에 대해서만 초점을 주고 싶을 수 있습니다. 이러한 이유로 AMR은 여러 역할을 위한 구체화 방법을 제공합니다. 예를 들어 `:location`의 구체화는 `be-located-at-91`이며, 다음과 같이 표상될 수 있습니다:

~~~lisp
(알 / 알-01
    :ARG0 (우 / 우리)
    :ARG1 (b / be-located-at-01
        :ARG1 (칼 / 칼)
        :ARG2 (서 / 서랍)))
~~~
> 우리는 칼이 서랍 안에 들어 있다는 것을 안다.

`be-located-at-91`은 두 개의 필수역을 가집니다: `:ARG1`(공간에 존재하는 물체), `:ARG2`(물체가 존재하는 공간)

또한 관계를 수식하고자(modify) 할 때 구체화를 사용할 수 있습니다. 아래 예를 보세요. `:location`에 대해 부정 수식을 하기 위해 구체화한 것을 볼 수 있습니다:

~~~lisp
(알 / 알-01
    :ARG0 (우 / 우리)
    :ARG1 (b / be-located-at-01
        :ARG1 (칼 / 칼)
        :ARG2 (서 / 서랍)
        :polarity -
        :time (어 / 어제)))
~~~
> 우리는 어제만 해도 칼이 서랍에 없었다는 것을 안다.

아래는 AMR 구체화 목록입니다. 구체화는 Korean PropBank의 용언 프레임과 직접 대응될 수도 있으며, 이 경우에는 해당 프레임의 `:ARG` 관계를 따라 주석하면 됩니다. 예를 들어 English AMR의 `be-located-at-91`는 `:location`에 대응되는 특수 프레임(`-91`)의 하나지만, 한국어에서는 `위치-01`이 이를 완벽히 대체할 수 있습니다. 

**참고**: 한국어 AMR은 English AMR의 Reification을 그대로 상속받고, 이에 몇가지 한국어 용언을 더 추가하는 선에서 구체화 목록을 확정하고자 합니다. 관계와 구체화의 관계는 반드시 일대일 대응되어야 하는 것은 아닙니다. 또한 `-91`류 특수 프레임의 활용성을 최대화하는 것, 다국어 자원 간의 호환성, 적절한 한국어 어휘에 대응시킬 수 없는 경우에도 반드시 하나 이상의 구체화 방안을 보장해야 하는 문제 등을 두루 고려한 것입니다. 구체화는 '관계'와 서로 변환될 수 있는 '개념'을 지정하는 데에 의의가 있는 것이지, 어떤 개념을 일반화하고자 하는 목적에서 활용하는 것이 아닙니다. 한국어 AMR에서 `be-located-at-91`과 `위치-01`는 마치 유의어(alias)처럼 취급될 뿐입니다.

> 표는 다음과 같이 읽습니다: `x :Relation y`  =  `x :Domain-of (z / Reification :Range y)`
>
> 예시)  `x :location y`  =  `x :ARG0-of (b / be-located-at-91 :ARG1 y)` 또는 `x :ARG0-of (위 / 위치-01 :ARG1 y)`

관계            | 구체화                     | 정의역(domain)  | 치역(range)   | 사례
---------------|---------------------------------|---------|---------|-------------------------
`:accompanier` | `accompany-01`, `동반-01`*       | `:ARG0` | `:ARG1` | "그녀는 그와 함께 있다"
`:age`         | `age-01`, `들-04`*                | `:ARG1` | `:ARG2` | "그녀는 41세다"
`:beneficiary` | `benefit-01`                    | `:ARG0` | `:ARG1` | "가격의 10%는 아이들을 위한 기금이다"
`:concession`  | `have-concession-91`            | `:ARG1` | `:ARG2` | "그녀가 있음에도 그는 나타났다"
`:condition`   | `have-condition-91`             | `:ARG1` | `:ARG2` | "그녀가 온다면 그도 올 것이다"
`:degree`      | `have-degree-91`                | `:ARG1` | `:ARG2` | "아주 크다" (강조 또는 완화 부사)
`:destination` | `be-destined-for-91`            | `:ARG1` | `:ARG2` | "나는 애틀랜타로 떠난다"
`:duration`    | `last-01`                       | `:ARG1` | `:ARG2` | "15분쯤 걸린다"
`:example`     | `exemplify-01`                  | `:ARG0` | `:ARG1` | "애틀랜타같은 도시"
`:extent`      | `have-extent-91`                | `:ARG1` | `:ARG2` | "거리는 2,500 마일"
`:frequency`   | `have-frequency-91`             | `:ARG1` | `:ARG2` | "그는 세 번 왔다"
`:instrument`  | `have-instrument-91`            | `:ARG1` | `:ARG2` | "포크는 음식을 먹기 위한 식기다"
`:li`          | `have-li-91`                    | `:ARG1` | `:ARG2` | "(B)"
`:location`    | `be-located-at-91`, `위치-01`    | `:ARG1` | `:ARG2` | "그녀는 여기 없다"
`:manner`      | `have-manner-91`                | `:ARG1` | `:ARG2` | "빠르게 끝났다"
`:mod`         | `have-mod-91`                   | `:ARG1` | `:ARG2` | "그는 중국계 혼혈이다"
`:name`        | `have-name-91`                  | `:ARG1` | `:ARG2` | "이 도시의 이름은 원래 콘스탄티노플이었다"
`:ord`         | `have-ord-91`                   | `:ARG1` | `:ARG2` | "이게 그의 첫번째 실패인지 아닌지 모르겠다"
`:part`        | `have-part-91`                  | `:ARG1` | `:ARG2` | "집의 지붕"
`:polarity`    | `have-polarity-91`              | `:ARG1` | `:ARG2` | "난 모른다"
`:poss`        | `own-01`, `have-03`, `갖-01`     | `:ARG0` | `:ARG1` | "그 개는 내 개가 아니다"
`:purpose`     | `have-purpose-91`               | `:ARG1` | `:ARG2` | "벌레를 쫓아내기 위함이다"
`:quant`       | `have-quant-91`                 | `:ARG1` | `:ARG2` | "4마리의 토끼가 있다"
`:source`      | `be-from-91`                    | `:ARG1` | `:ARG2` | "그녀는 이파네마 출신이다"
`:subevent`    | `have-subevent-91`              | `:ARG1` | `:ARG2` | "컨퍼런스에서의 발표"
`:time`        | `be-temporally-at-91`           | `:ARG1` | `:ARG2` | "파티는 금요일이다"
`:topic`       | `concern-02`                    | `:ARG0` | `:ARG1` | "그 쇼는 나에 대한 것이다"
`:value`       | `have-value-91`                 | `:ARG1` | `:ARG2` | "전화번호는 1-800-555-1223이다."

\**전체 roleset의 수는 일치하지 않음.*

아래 관계들은 구체화되지 않습니다:

  - `:ARG0`, `:ARG2`, `:ARG2`, ..., `:op1`, `:op2`, `:op3`, `:op4`, …
  - `:calendar`, `:century`, `:day`, `:dayperiod`, `:decade`, `:era`, `:month`, `:quarter`, `:season`, `:timezone`, `:weekday`, `:year`, `:year2`
  - `:unit`, `:direction`, `:scale`

그럼 언제 구체화를 해야 할까요? 일단의 대답은 "해야할 필요를 느낄 때"입니다. "여자는 남자가 도착했기 때문에 떠났다."라는 하나의 문장은 (안타깝게도) 두 개의 다른 AMR으로 표현될 수 있습니다. (여기서는 `cause-01` 대신 `인하-02`로 설명하겠습니다.) 둘 다 AMR의 규칙을 따라 표상된 것이고 어느 쪽으로 하든 무방합니다. 둘 중 어느 것 하나가 규범으로 인정되는 것은 아닙니다.

~~~lisp
구체화되지 않은 AMR:                  구체화된 AMR:
(떠 / 떠나-01                       (떠 / 떠나-01
    :ARG0 (여 / 여자)                   :ARG0 (여 / 여자)
    :cause (도 / 도착-01                :ARG2-of (인 / 인하-02
        :ARG1 (남 / 남자)))                 :ARG1 (도 / 도착-01
                                                :ARG1 (남 / 남자))))
~~~

게다가 "여자는 남자가 도착했기 때문에 떠났다."에 대해서는 보통 첫 번째 AMR을 선택하는 경향이 있지만, "그 남자의 도착으로 인해 그 여자는 떠났다"와 같이 서술어 '인하다'가 쓰인 경우에는 두 번째 AMR을 선호하는 경향이 있습니다. 그래서 의미가 비슷한 두 문장이 동일한 AMR 표현을 얻는다는 것에 대한 보장이 없게 되는 것이죠.

또 하나 있을 수 있는 정책은 "항상 구체화한다"인데, `:time`이나 `:location` 같은 관계들을 모두 AMR에서 폐지하고 `be-located-at-91` 또는 `be-temporally-at-91`과 같은 것만을 쓰는 것입니다. 물론 이 방법은 무척 성가시죠. 쉽고 형식화된 `:location`을 사용하는 것이 훨씬 간단하니까요.

해결책: 우리는 '구체화를 포함한 AMR'을 '정품 AMR'로 간주하고, 구체화하지 않은 관계를 의미론적인 '슈가코드(sugarcode)'로 간주합니다. 따라서 한국어를 AMR로 변환할 때의 규칙은 '구체화하고 싶은 경우'에 (각자 알아서) 하는 것으로 합니다. 작업자가 작성한 AMR은 결국에는 구체화된 형식으로 정규화될 것이기 때문입니다.

AMR 말뭉치에서는, 일관성의 측면에서, 구체화는 꼭 필요한 경우가 아니면 피하는 것이 좋습니다.

## 동사구 ([Phrasal verbs](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#phrasal-verbs))

AMR에서는 경동사 구조(light-verb constructions)를 따로 고려하지 않습니다. 즉, 어근에 동사 파생 접미사 '-하다'가 붙은 구성이나, 명사의 곡용형(또는 조사 생략)에 동사 '하다'가 이어진 것 모두 동일하게 처리합니다.

~~~lisp
(설 / 설명-01
    :ARG0 (기 / 기술자)
    :ARG1 (원 / 원리))
~~~
> 기술자가 원리를 설명했다.
>
> 기술자가 원리를 설명을 했다.
>
> 기술자가 원리를 설명 했다.

~~~lisp
(시 /시인-01
    :ARG0 (범 / 범인))
~~~
> 범인이 시인했다.
>
> 범인은 시인을 했다.

Korean PropBank의 용언 프레임 중에서는 명사-명사 구성이나 본 용언-보조 용언 구성이 더러 있습니다.

~~~lisp
(가 / 가져다주-01
    :ARG1 (약 / 약))
~~~
> 약을 가져다 주었다.

~~~lisp
(맞 / 맞아떨어지-01
    :ARG1 (예 / 예상-01))
~~~
> 예상이 맞아 떨어졌다.

~~~lisp
(계 / 계획-01
    :ARG1 (준 / 준지방은행화-01
        :ARG1 (금 / 금고
            :mod (대 / 대형))))
~~~
> 대형 금고를 준지방은행화할 계획이다.

간혹 보조 용언의 여부가 본 용언의 의미를 크게 바꾸지 않는 경우도 있습니다. 예를 들어 KPB에는 `차-01`(fill)과 `채워넣-01`(fill)이 모두 있습니다. AMR에서는 `차-01`(fill)와 `채워넣-01`(fill)을 서로 유의어로 취급합니다. **활용할 수 있는 용언 프레임이 있다면** 문장에 나타난 어휘를 기준으로 주석하세요. "방을 채웠다."의 경우에는 `차-01`을, "기름을 채워 넣었다."의 경우에는 `채워넣-01`을 쓰면 됩니다.

"가져 가다"나 "가지고 가다", "갖고 가다"는 어떻게 할까요? '갖다(take)'와 '가다(go)'를 적절히 조합하면 될까요? VP1 + VP2 구성은 굉장히 까다롭습니다. 이런 경우에는 단순하게 `가져가-00` 혹은 `가지고가-00`, `갖고가-00`와 같이 미등재어 처리를 하세요. 더 안전하고 쉬운 대안이 됩니다.

## 한국어의 조사와 시간 및 공간 관련 표현 ([Prepositions](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#prepositions))

이 챕터는 [Prepositions](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#prepositions)의 내용을 바탕으로 작성되었습니다. 여기서는 한국어의 조사(**postposition**)와 몇몇 의존 명사에 대해 다룹니다.

AMR에서 의미 프레임 요소를 기호적으로 표현하는 대부분의 조사들은 누락시킵니다. 

~~~lisp
(부 / 부도내-01
    :ARG0 (국 / 국가
        :ARG1-of (해 / 해당-01))
    :time (d / date-entity
        :month 6))
~~~
> 해당 국가는 6월에 부도를 냈다.

~~~lisp
(죽 / 죽-01
    :ARG1 (남 / 남자)
    :location (집 / 집
        :poss 남))
~~~
> 남자는 그의 집에서 죽었다.

시간이나 장소를 나타내는 명사류에 부사격 조사가 동반되거나, 일부 명사류를 통해서 추가적인 정보가 주어진 경우에는 AMR의 `:opN`을 사용합니다. 여기에서 `:op1`은 접속에서 사용되는 `:op1`과는 다릅니다.

~~~lisp
(부 / 부도내-01
    :ARG0 (국 / 국가
        :ARG1-of (해 / 해당-01))
    :time (이 / 이후
        :op1 (전 / 전쟁))
~~~
> 해당 국가는 **전쟁 이후** 부도가 났다.

~~~lisp
(죽 / 죽-01
    :ARG1 (남 / 남자)
    :location (근 / 근처
        :op1 (집 / 집
            :poss 남)))
~~~
> 남자는 그의 **집 근처**에서 죽었다.
>
> 남자는 자기 집 근처에서 죽었다.

~~~lisp
(죽 / 죽-01
    :ARG1 (남 / 남자)
    :location (사 / 사이
        :op1 (집 / 집)
        :op2 (강 / 강)))
~~~
> 남자는 그의 **집과 강 사이**에서 죽었다.

때로는 부사절이나 관형절의 내용을 서술어-논항 구조로 나타내기 어렵거나, `:time`이나 `:location`과 같은 일반화된 역할로 처리할 수 없을 때가 있습니다. `:postp-x` 표현을 활용할 수는 있겠지만 꺼려지는 일이죠. 아래 문장은 "완벽한 성공을 향한 집념"과 같이 환언하여 표상할 수도 있을 것입니다.

~~~lisp
(집 / 집념
    :postp-으로-의 (성 / 성공
        :ARG1-of (완 / 완벽-01)))
~~~
> 완벽한 성공으로의 집념

여러 단어가 함께 쓰인 구, 복합 조사 등은 AMR에서 `-`로 구분해 줍니다.

~~~lisp
(나 / 나서-01
    :ARG0 (시 / 시민)
    :ARG1 (돕 / 돕-01
        :ARG0 시
        :mod (너 / 너-나-할-것-없이)))
~~~
> 시민들은 너 나 할 것 없이 돕겠다고 나섰다.

"~에 따르면(according to)"과 같이 흔히 쓰이는 일부 표현들은 아래와 같은 요령으로 처리합니다. 일종의 관습 같은 것입니다.

~~~lisp
(전 / 전하-01
    :ARG0 (관 / 관계자
        :mod (정 / 정부))
    :ARG1 (사 / 사고
        :time (어 / 어제)))
~~~
> 정부 관계자에 따르면 사고는 어제 발생했다고 전해진다.
>
> 정부 관계자는 어제 사고가 발생했다고 전했다.

보조사 '-도'의 처리는 [접속](#%EC%A0%91%EC%86%8D-conjunctions)을 참고하세요. '누구 또한, 역시'의 의미에 있어서는 `either`를 활용합니다. (여기서 `:op1`이 누락된 것에 유의하세요.)

~~~lisp
(재 / 재확인-01
    :ARG0 (e / either
        :op2 (관 / 관계자
            :mod (정 / 정부)))
    :ARG1 (사 / 사고
        :time (어 / 어제))
    :mod (마 / 마찬가지))
~~~
> 정부 관계자**도** 마찬가지로 어제 사고를 재확인 해주었다.

보조사의 처리는 대개 까다롭습니다. 강조의 의미로 쓰인 보조사 '-도'를 '또한' 등의 부사로 대신하는 방법이 있습니다.

~~~lisp
(지 / 지적-01
    :ARG1 (자 / 자리잡-01
        :ARG0 (위 / 위계
            :manner (군 / 군대))
        :ARG1 (직 / 직장)
        :manner (여 / 여전하-01))
    :mod (또 / 또한))
~~~
> 직장 안에 ‘군대식(式) 위계’가 여전히 자리 잡고 있다는 지적**도** 있다.

마찬가지로 보조사 '-만'을 '오직' 등으로 대신할 수도 있겠죠. **그러나 반드시 모든 것을 표상해야 하는 것은 아닙니다.** 보조사의 쓰임으로 인해 문장의 명제가 크게 달라지지 않는다면, 보조사의 표상은 그리 중요한 일이 아닐 수 있습니다.


## 관계절 ([Relative clauses](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#relative-clauses))

앞서 [서론](#i-%EC%84%9C%EB%A1%A0-introduction)에서도 언급하였듯이, AMR은 관계절을 표상할 때 흔히 역관계(inverse roles)를 활용합니다.

~~~lisp
(믿 / 믿-01
    :ARG0 (소 / 소년))
~~~
> 소년은 믿고 있다.

~~~lisp
(소 / 소년
    :ARG0-of (믿 / 믿-01))
~~~
> 믿고 있는 소년

관계절을 구성하는 관형어에 부정의 의미가 포함되어 있다면 이를 분명히 드러냅니다.

~~~lisp
(재 / 재보급-01
    :ARG1-of (충 / 충분하-01
        :polarity -))
~~~
> 불충분한 재보급

~~~lisp
(충 / 충분하-01
    :ARG1 (재 / 재보급-01)
    :polarity -)
~~~
> 재보급이 충분하지 않다


## 여러번 할당되는 동일 관계 ([Multiple relations with the same name](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#multiple-relations-with-the-same-name))

어떤 개체는 같은 관계를 여러번 가질 수 있습니다. 아래의 예시에서 "그녀는 오늘 일찍 도착했다." 에서는 2개의 `:time`을, "그녀를 믿고 싶은 소년"에서는 2개의 `:ARG0-of` 관계를 부여받았습니다.

~~~lisp
(도 / 도착-01
    :ARG1 (그 / 그녀)
    :time (오 / 오늘)
    :time (이 / 이전
        :op1 (지 / 지금)))
~~~
> 그녀는 오늘 일찍 도착했다.

~~~lisp
(소 / 소년
    :ARG0-of (원 / 원하-01
        :ARG1 (믿 / 믿-01
            :ARG1 (소2 / 소녀)))
    :ARG0-of 믿)
~~~
> 소녀를 믿고 싶은 소년


## 접속 ([Conjunctions](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#conjunctions))

한국어에서 접속은 접속조사, 연결어미, 접속부사로 나타납니다. 접속과 내포, 종속 접속과 대등 접속과 관련하여 많은 연구들이 있지만, 문법 연구의 모든 쟁점들을 AMR에 엄밀하게 반영하기는 현실적으로 쉽지 않은 일입니다.

한국어 AMR에서는 일단 English AMR의 요령을 차용하는 것으로 시작하고자 합니다. 한국어 AMR에서 접속을 어떻게 처리하는가에 대한 기준은 앞으로도 개정해야 할 부분이 많을 것입니다. 

접속을 표상하기 위헤서 AMR에서는 다음과 같은 개념들을 활용합니다: `:opx` 관계를 포함하는 `and`, `or`, `contrast-01`, `either` 등.

~~~lisp
(a / and
    :op1 (소 / 소년)
    :op2 (소 / 소녀))
~~~
> 소년과 소녀

~~~lisp
(e / either
    :op1 (소 / 소년)
    :op2 (소2 / 소녀)
    :op3 (강 / 강아지))
~~~
> 소년도 소녀도 강아지도 (각각 어떠하다)
>
> 소년이든 소녀든 강아지든 (어느 쪽이든 모두 어떠하다)

~~~lisp
(o / or
    :op1 (소 / 소년)
    :op2 (소2 / 소녀)
    :op3 (강 / 강아지))
~~~
> 소년, 소녀 또는 강아지 (중에 어느 하나)

나란히 연쇄되어 성분을 수식하는 관형절에 대해서는 `and`를 쓰지 않습니다.

~~~lisp
(공 / 공
    :ARG1-of (크 / 크-01)
    :ARG1-of (무 / 무겁-01))
~~~
> 크고 무거운 공
>
> 크고도 무거운 공

`:opx`는 절 접속에도 쓰입니다.

~~~lisp
(a / and
    :op1 (환 / 환호-01
        :ARG0 (사 / 사람))
    :op2 (달 / 달려가-01
        :ARG0 (소 / 소년)))
~~~
> 사람들이 환호했고, 소년이 달려갔다.

~~~lisp
(c / contrast-01
    :ARG1 (환 / 환호-01
        :ARG0 (사 / 사람))
    :ARG2 (달 / 달려가-01
        :polarity -
        :ARG0 (소 / 소년)))
~~~
> 사람들이 환호했으나, 소년은 달려가지 않았다.

간혹 `:op1`이나 `:ARG1`이 누락되는 경우도 있습니다.

~~~lisp
(c / contrast-01
    :ARG2 (달 / 달려가-01
        :polarity -
        :ARG0 (소 / 소년)))
~~~
> 그러나 소년은 달려가지 않았다.

AMR은 반복되는 성분이 생략되는 경우에도 명시적으로 표상합니다.

~~~lisp
(a / and
    :op1 (환 / 환호-01
        :ARG0 (소 / 소년))
    :op2 (달 / 달려가-01
        :ARG0 소))
~~~
> 소년은 환호하며 달려갔다.

이러한 요령은 서로 다른 서술어에 대해서 다른 논항 역할을 받는 경우에 특히 효과적이죠.

~~~lisp
(a / and
    :op1 (도 / 도착-01
        :ARG1 (소 / 소년))
    :op2 (수 / 수상-01
        :ARG0 소
        :manner (즉 / 즉시)))
~~~
> 소년은 도착한 즉시 수상했다.

다만 AMR에서 `:time`이나 `:location`은 '바깥으로' 꺼냅니다. 여기서 `:time`은 `and`로 묶인 접속 전체를 수식합니다.

~~~lisp
(a / and
    :time (d / date-entity
        :weekday (화 / 화요일))
    :op1 (도 / 도착-01
        :ARG1 (소 / 소년))
    :op2 (떠 / 떠나-01
        :ARG0 소))
~~~
> 화요일에 소년이 도착하고 떠났다.


## 양화사와 작용역 ([Quantifiers and scope](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#quantifiers-and-scope))

**참고**: 이 지침에서는 English AMR 1.2.6을 기준으로 서술합니다. 추후 [Pustejovsky et at.(2019)](https://www.aclweb.org/anthology/W19-3303/)의 내용에 따라 개정 사항이 반영될 예정입니다.

AMR은 아직 양화사에 대해 심도 있게 표상하지는 않습니다. 그저 양화사의 위치만을 나타낼 뿐이죠.

~~~lisp
(떠 / 떠나-01
    :ARG0 (소 / 소년
        :mod (모 / 모든)))
~~~
> 모든 소년들이 떠났다.
>
> 소년들이 모두 떠났다.

~~~lisp
(떠 / 떠나-01
    :polarity -
    :ARG0 (소 / 소년
        :mod (모 / 모든)))
~~~
> 모든 소년들이 떠나지 않았다.
>
> 소년들이 아무도 떠나지 않았다.
>
> 소년들 중 그 누구도 떠나지 않았다.

~~~lisp
(떠 / 떠나-01
    :ARG0 (소 / 소년
        :mod (모 / 모든
            :polarity -)))
~~~
> 모든 소년들이 떠난 것은 아니다.

~~~lisp
(떠 / 떠나-01
    :ARG0 (사 / 사람
        :mod (모 / 모든
            :polarity -)))
~~~
> 모두가 떠난 것은 아니다.
>
> 모든 사람들이 떠난 것은 아니다.

`:polarity`의 위치가 애매할 때가 있습니다.

~~~lisp
(생 / 생각-01
    :ARG0 (소 / 소녀)
    :ARG1 (일 / 일하-01
        :ARG0 (소2 / 소년)
        :manner (성 / 성실-01)))
~~~
> 소녀는 소년이 성실하게 일한다고 생각한다.

만약 "소녀는 소년이 성실하게 일한다고 생각하지 않는다."를 표상하고 싶다면 "생각하다", "일하다", "성실하게" 중 어디에 부정 극성을 두어야 할지를 결정해야 합니다. 여기서는 "성실하게"에 두어야 하겠죠.

~~~lisp
(생 / 생각-01
    :ARG0 (소 / 소녀)
    :ARG1 (일 / 일하-01
        :ARG0 (소2 / 소년)
        :manner (성 / 성실-01
            :polarity -)))
~~~
> 소녀는 소년이 성실하지 않게 일한다고 생각한다. 
>
> 소녀는 소년이 성실하게 일하지 않는다고 생각한다. (구어체적)
>
> 소녀는 소년이 성실하게 일한다고 생각하지 않는다. (구어체적)

`:polarity`의 위치가 달라지면, 의미도 달라지게 됩니다.

~~~lisp
(생 / 생각-01
    :ARG0 (소 / 소녀)
    :ARG1 (일 / 일하-01
        :polarity -
        :ARG0 (소2 / 소년)
        :manner (성 / 성실-01)))
~~~
> 소녀는 소년이 성실한 태도로, '일을 안 하고 있다'고 생각한다. (The girl believes that the boy refrains from work, in a hard manner.)

~~~lisp
(생 / 생각-01
    :polarity -
    :ARG0 (소 / 소녀)
    :ARG1 (일 / 일하-01
        :ARG0 (소2 / 소년)
        :manner (성 / 성실-01)))
~~~
> 소녀가 소년이 성실하게 일하고 있다고 생각한다는 것은 사실이 아니다. (It’s not true that the girl believes the boy works hard.)

~~~lisp
(생 / 생각-01
    :ARG0 (소 / 소녀
        :polarity -)
    :ARG1 (일 / 일하-01
        :ARG0 (소2 / 소년
            :polarity -)
        :manner (성 / 성실-01)))
~~~
> 소녀가 아닌 누군가는 소년이 아닌 누군가가 성실하게 일한다고 생각한다. (The non-girl believes that the non-boy works hard.)

현행 AMR은 양화사와 작용역에 대해서 명확한 지침을 제공하지 못하고 있습니다. (AMR apologizes for not advising on the placement of negation with respect to quantifiers.) 앞으로의 개정 방향에 대해서는 [Pustejovsky et at.(2019)](https://www.aclweb.org/anthology/W19-3303/)을 참고하세요.


## 정도 ([Degree](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#degree))

강조 부사(intensifiers; 매우, 아주)와 완화 부사(downtoners; 다소, 약간)들은 `:degree`로 주석합니다.

~~~lisp
(아 / 아름답-01
    :ARG1 (당 / 당신)
    :degree (정 / 정말))
~~~
> 당신은 정말 아름다워요.

비교급(comparative)과 최상급(superlative)은 `have-degree-91`을 활용하여 표상합니다.

~~~lisp
have-degree-91
    Arg1: 도메인, 속성으로 특징지어질 수 있는 개체 (예: 소녀)
    Arg2: 속성 (예: 키가 크다)
    Arg3: 정도 그 자체 (예: 더, 덜, 제일, 가장, 너무, 매우, 약간, 충분히 등)
    Arg4: 비교 대상(compared-to) (예: 소년(보다 어떠하다))
    Arg5: 최상급: 상위 집합(superset)에 대한 참조(reference)
    Arg6: 참조(reference), 충족 조건(threshold of sufficiency) (예: 롤러코스터를 타기(에 충분히 크다))
~~~

계사문을 포함해서 비교 자체가 문장의 주안점이 될 때(예: *소녀는 소년보다 키가 크다*, *그녀가 팀 내에서 제일 키 큰 선수다* ), 주석자들은 정도 부사어로 수식되는 용언(예: '얼마나' **빠르게**) 또는 수식어로 특징지어지는 개체(예: '빠른' **속도**)를 초점으로 두기 보다는 `have-degree-91`을 루트로 놓고 주석하는 것이 좋습니다. 아래를 참고하세요.

~~~lisp
(소 / 소년
    :ARG1-of (h / have-degree-91
        :ARG2 (똑 / 똑똑하-01)
        :ARG3 (더 / 더)))
~~~
> 더 똑똑한 소년

~~~lisp
(소 / 소년
    :ARG1-of (h / have-degree-91
        :ARG2 (똑 / 똑똑하-01)
        :ARG3 (가 / 가장)))
~~~
> 가장 똑똑한 소년

~~~lisp
(계 / 계획
    :ARG1-of (h / have-degree-91
        :ARG2 (좋 / 좋-01)
        :ARG3 (더 / 더)))
~~~
> 더 좋은 계획

~~~lisp
(계 / 계획
    :ARG1-of (h / have-degree-91
        :ARG2 (나 / 나쁘-01)
        :ARG3 (더 / 더)))
~~~
> 더 나쁜 계획

**참고**: '더 좋은 계획'의 반대가 되는 의미로 '더 좋지 않은 계획'을 쓰지 않도록 하세요. '좋은 정도'가 '더 좋지는' 않을 뿐 '여전히 좋은 편인 계획'일 수도 있습니다.

~~~lisp
(계 / 계획
    :ARG1-of (h / have-degree-91
        :ARG2 (지 / 지나치-01)
        :ARG3 (너 / 너무)))
~~~
> 너무 지나친 계획

~~~lisp
(h / have-degree-91
    :ARG1 (소 / 소녀)
    :ARG2 (크 / 크-01
        :ARG1 (키 / 키))
    :ARG3 (더 / 더)
    :ARG4 (소2 / 소년))
~~~
> 소녀가 소년보다 키가 더 크다.

`have-degree-91`은 상하위 집합 관계(subset/superset relation)를 갖는 최상급 구문에도 활용됩니다. 이는 `include-91`에 선행하여 적용되는 것으로, 상위 집합의 비교 대상과 최상급을 받는 개체 사이의 상하위 집합 관계를 나타내고자 할 경우에도 쓰입니다.

~~~lisp
(h / have-degree-91
    :ARG1 (그 / 그녀)
    :ARG2 (크 / 크-01
        :ARG1 (키 / 키))
    :ARG3 (가 / 가장)
    :ARG5 (선 / 선수
        :ARG0-of (h2 / have-org-role-91
            :ARG1 (팀 / 팀))))
~~~
> 그녀는 팀에서 가장 키가 큰 선수이다.

`have-degree-91`은 어떠한 상태의 정도와 그것의 결과 또는 후속 사건을 논항으로 하여 서술하는 정도-결과 구문(degree-consequence construction)에도 사용됩니다.

~~~lisp
(h / have-degree-91
    :ARG2 (이 / 이르-03)
    :ARG3 (너 / 너무)
    :ARG6 (결 / 결론-01))
~~~
> 결론에 이르기엔 너무 이르다. (It is too early to reach any conclusion.)
>
> 결론짓기엔 너무 이르다.

**참고**: 위 문장에서 보이는 바와 같이 '결과(consequence)'가 되는 논항과의 1차적(primary) 관계는 생략되거나 특정되지 않을 수 있습니다. 주석자들은 맥락에 맞는 논리적 관계를 분명히 보이는 것이 좋습니다. 정도-결과 구문에 있어서에 대해 양태나 가능성, 부정 극성(negative polarity) 등을 부여하고 싶을 수 있으나, (예: 결과가 '없다'는 것을 드러내는 등) 이러한 구문들을 분석한 바에 의하면 앞서 언급한 요소들을 문맥 상에서 일관되게 다루는 것이 쉽지 않다는 것을 알 수 있었습니다. 따라서 `ARG6`은 정도에 대한 '참조' 또는 '충족 조건'이 오는, 간단한 관계로 제한하도록 합니다. 추가적인 예시를 살펴보고 싶다면 [**AMR Dictionary**](https://amr.isi.edu/doc/amr-dict.html)에서 더 많은 예시를 찾아볼 수 있습니다. 부정 극성은 표면형에서 명확히 드러난 경우에 한해서만 (`have-degree-91`을 수식하는 것으로) 주석될 수 있습니다.

~~~lisp
(h / have-degree-91 :polarity - 
    :ARG1 (그 / 그)
    :ARG2 (크 / 크-01
        :ARG1 (키 / 키))
    :ARG3 (충 / 충분하-01)
    :ARG6 (타 / 타-01 
        :ARG0 그 
        :ARG1 (롤 / 롤러코스터)))
~~~
> 그는 롤러코스터에 타기에 키가 충분히 크지 않다.

더 심도있는 논의를 보고 싶다면 [Bonial et al.(2018)](https://www.aclweb.org/anthology/L18-1266)의 *Abstract Meaning Representation of Constructions: The More We Include, the Better the Representation*을 읽어 보세요.


## 변항과 상호참조 ([Variables and co-reference](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#variables-and-co-reference))

두 개의 변항(variable)이 동일하다면 그것은 같은 개체를 가리키는 것입니다.

~~~lisp
(원 / 원하-01
    :ARG0 (소 / 소년)
    :ARG1 (가 / 가-01
        :ARG0 소))
~~~
> 소년은 가고 싶다.

자연어 문장에서 외현적 대명사(overt pronouns)와 영대명사(zero pronouns)는 상호참조를 실현하는 데 쓰입니다. AMR에서는 이를 변항으로 대신합니다.

~~~lisp
(원 / 원하-01
    :ARG0 (소 / 소년)
    :ARG1 (믿 / 믿-01
        :ARG0 소
        :ARG1 소))
~~~
> 소년은 스스로를 믿고 싶다.

외현적 대명사가 문장 내에 선행사를 가지지 않는 경우에는 AMR에 대명사를 그대로 씁니다.

~~~lisp
(보 / 보-01
    :ARG0 (그 / 그)
    :ARG1 (그2 / 그들))
~~~
> 그는 그들을 보았다.

AMR에서 대명사 또는 대용어는 '나', '너', '그', '우리', '너희', '저 아이' 등을 기준으로 주석하며, '내', '네', '쟤' 또는 낮춤 '저', '저희' 등의 형태로 주석하지 않습니다.

## 소유 ([Possession](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#possession))

`:poss`("possessed by")는 소유를 나타내는 일반적인 형식입니다. AMR에서는 소유격형(possessive) 또는 관형격 조사 '-의'에 대해 `:poss`를 주석합니다.

~~~lisp
(차 / 차
    :poss (나 / 나))
~~~
> 내 차
>
> 나의 차

~~~lisp
(권 / 권리
    :poss (국 / 국민))
~~~
> 국민의 권리

~~~lisp
(체 / 체계
    :mod (교 / 교통)
    :poss (c / city 
        :wiki "서울특별시"
        :name (이 / 이름 :op1 "서울")))
~~~
> 서울의 교통 체계

모든 소유격형 또는 조사 '-의'가 `:poss`로 표상될 수 있는 것은 아닙니다. 경우에 따라 `:part-of`, `:consist-of` 등을 활용하기도 합니다.


## 관련어 ([Pertainyms](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#pertainyms))

이 챕터에서는 [Pertainyms](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#pertainyms)에서 제시하는 *관련어(Pertainym adjectives) 처리 지침을 바탕으로, 한국어의 '-적(的)' 또는 '-성(性)' 파생 명사(주로 명사-관형사 통용어)를 처리하는 방법을 다룹니다. **Pertainym의 역어 '관련어'는 임의로 결정한 것입니다.*

AMR에서 접미사 '-적' 또는 '-성', '-식' 등은 주석되지 않습니다. 적절한 역할을 부여하기 어려운 경우에는 명사형을 기준으로 어간화한 후 `:mod`로 주석합니다.

~~~lisp
(세 / 세균
    :mod (병 / 병원))
~~~
> 병원성 세균

~~~lisp
(출 / 출장-00
    :purpose (외 / 외유-00))
~~~
> 외유성 출장

~~~lisp
(선 / 선택-01
    :mod (극 / 극단))
~~~
> 극단적 선택
>
> 극단의 선택

~~~lisp
(치 / 치료-01
    :manner (집 / 집중-01))
~~~
> 집중적 치료
>
> 집중 치료

~~~lisp
(의 / 의자
    :ARG1-of (고 / 고정-01))
~~~
> 고정식 의자

## 순서 ([Ordinals](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#ordinals))

순서를 표상하기 위해 `:ord`와 `ordinal-entity`를 사용합니다.


~~~lisp
(행 / 행성
    :ord (o / ordinal-entity 
            :value 2))
~~~
> 두 번째 행성
>
> 행성 II

~~~lisp
(방 / 방문-01
    :ord (o / ordinal-entity
        :value 1
        :range (t / temporal-quantity
            :quant 10
            :unit (년 / 년))))
~~~
> 10년만의 첫 방문


## 부분집합 ([Subsets](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#subsets))

말을 하다 보면 부분집합을 언급하는 경우가 있죠. AMR에서는 `:subset`과 `:superset`을 씁니다.

~~~lisp
(죽 / 죽-01
    :ARG1 (군 / 군인
        :quant 9
        :superset (군2 / 군인
            :quant 20)))
~~~
> 스무 명의 중 아홉 명의 군인이 죽었다.
>
> 스무 명의 군인 중 아홉이 죽었다.

~~~lisp
(걸 / 걸리-02
    :ARG1 (사 /사람
        :quant 4
        :superset (사2 / 사람
            :ARG0-of (살 / 살아남-01)
            :quant 5)
        :subset (사3 / 사람
            :quant 3
            :ARG2-of (진 / 진단-01)))
    :ARG2 (질 / 질병
        :mod (그 / 그)))
~~~
> 5명의 살아남은 사람 중 진단을 받은 3명을 포함한 4명은 그 질병에 걸렸다.

부분집합과 상위집합(superset)이 공유하는 자질(feature)은 위의 "살아남다"와 같이 상위집합에만 적용됩니다. (`살아남-01`은 5명의 위치인 `사2`에 놓이지 4명의 위치인 `사`에 놓이지 않습니다.) `:subset`의 구체화 `include-91`을 활용하여 아래와 같이 동치가 되는 AMR을 작성할 수 있습니다.

~~~lisp
(죽 / 죽-01
    :ARG1 (군 / 군인
        :quant 9
        :ARG1-of (i / include-91
            :ARG2 (군2 / 군인
                :quant 20))))
~~~
> 스무 명의 중 아홉 명의 군인이 죽었다.
>
> 스무 명의 군인 중 아홉이 죽었다.

AMR에서 `:subset`을 활용하는 경우는 드문 편입니다. -- 그렇지 않으면 골치 아픈 일이 많아지죠. 예를 들면 "이 공장의 인부 중 셋이,"라는 표현을 AMR로 표상할 때 그냥 단순하게 "인부 셋이"라고 하는 것이 더 간단할 겁니다.

**참고**: AMR에서는 `:cause`, `:cost`, `:employed-by`, `:meaning`, `:role`, `:subset`, `:superset`과 그 역관계(예 `:cause-of`)들에 대해서 각각 `cause-01`, `cost-01`, `have-org-role-91`, `mean-01`, `have-org-role-91` 그리고 `include-91`로 구체화(reification)합니다. 즉 `:cause`와 같은 관계는 일종의 *단축어(shortcut)* 가 됩니다.


## 개체명과 위키피케이션 ([Named Entities and wikification](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#named-entities))

원칙적으로 AMR의 모든 개념 인스턴스들은 `:name` 관계를 가질 수 있습니다. AMR에서는 절대로 국가나 인물 같은 몇몇 부류에 대해서만 개체명 주석을 한다는 식으로 제약을 두거나 하지 않습니다. 선박, 애완동물, 컴퓨터 등등 역시 이름을 가질 수 있습니다.

이름을 가진 개체(named entities)들은 여러가지 방법으로 지칭되곤 합니다. 예를 들면 *"한국"*, *"대한민국"*, *"남조선"*, *"Korea"*, *"South Korea"*, *"ROK"*, *"Republic of Korea"* 하는 식이죠. 이런 경우에 개체명을 대표형(canonical form)으로 주석할 필요가 있을 수 있습니다. AMR에서는 대표형의 기준으로 한국어 위키백과의 문서 이름을 따르며, `:wiki`를 이용해 주석합니다. (예: `:wiki "대한민국"`과 같이 하며, 띄어쓰기는 `_`로 대체해야 합니다. 예를 들어 위키백과의 표기가 "대한민국 정부"라면 `:wiki "대한민국_정부"`와 같이 합니다. 다음 URL의 뒷부분을 보세요: https://ko.wikipedia.org/wiki/대한민국_정부) 

이러한 방식은 중의성이 발생할 수 있는 경우에 특히 유용합니다. ("제주"가 섬 이름으로서의 '제주도'를 뜻할 수도 있고, 행정구역 '제주시'를 뜻할 수도, 광역지방자치단체로서 '제주특별자치도'를 뜻할 수도 있습니다.) 만약 위키백과에 문서가 없는 경우에는 `:wiki -`와 같이 주석합니다.

~~~lisp
(p / person 
    :wiki "마거릿_브라운"
    :name (이 / 이름 
            :op1 "몰리" 
            :op2 "브라운") 
    :ARG0-of (주 / 주장-01 
               :ARG1 (돌 / 돌아가-01))) 
~~~
> 돌아가자고 주장했던 몰리 브라운

~~~lisp
(s / ship 
    :wiki "RMS_타이타닉"
    :name (이 / 이름
            :op1 "타이타닉")) 
~~~
> 타이타닉
>
> 타이타닉이라는 이름을 가진 배

~~~lisp
(u / university
    :wiki "연세대학교_신촌캠퍼스"
    :name (이 / 이름 
        :op1 "연세대학교"
        :op2 "신촌캠퍼스")) 
~~~
> 연세대학교 신촌캠퍼스

AMR은 단어들을 `:opN`으로 묶습니다. 여기에서는 개체명의 의미적 관계를 분석하거나 하지 않습니다. 예를 들어, <바람과 함께 사라지다>를 `사라지-01`를 활용하여 표상하지 않습니다.

고유명의 축약형은 복원(expand)하지 않습니다. 그러나 일반 명사의 축약은 복원합니다. 일반 명사에 오타(typo)가 있다면 정서법에 맞게 교정하세요. 그러나 방언형은 교정하지 않습니다.

~~~lisp
(u / university
    :wiki "연세대학교_신촌캠퍼스"
    :name (이 / 이름 
        :op1 "연대"
        :op2 "신촌캠")) 
~~~
> 연대 신촌캠

~~~lisp
(판 / 판매-01
    :manner (방 / 방문-01))
~~~
> 방문 판매
>
> 방판

고유명이나 '-자(者)', '-인(人)' 등의 명사류를 AMR로 표상하려면 루트 자리 또는 최상위 *인스턴스* 역할을 채워야 하죠. 예를 들어 일반적인 직위 수행자로서의 "대통령"이라는 표현과 특정 인물을 지칭하기 위한 표현인 "문 대통령"을 각각 어떻게 처리해야 할지 혼동될 수 있습니다.

앞서 원칙적으로는 AMR의 모든 개념 인스턴스들은 `:name` 관계를 가질 수 있다고 했습니다. 그 말은 `사람`, `여성`, `고양이`, `자동차` 등 일급 개념이기만 하면 `:name` 관계를 가질 수 있다는 것이죠. 그러나 `사람`, `여성` 등이 별도의 개체명 타입으로 취급될 필요는 없을 것입니다. 또한 어떤 것은 개체명 타입으로 취급되고, 어떤 것은 그럴 필요가 없는지 다소 혼동될 수 있습니다. 

때문에 기본적인 개체명 목록이 제공될 필요가 있습니다. 아래는 AMR에서 개체명으로 다루기로 하는 타입들의 리스트입니다.

다만 아래에서 제시하는 개체명 타입은 번역하여 쓰지 않습니다. 예를 들어 `(사 / 사람)`과 `(p / person)`은 (서로 Alias로써) 구분되어 쓰이며, 이때 `(p / person)`은 `:name` 관계를 가지는 경우에만 사용하는 것으로 한정합니다.

**참고**: `(사 / 사람)`이 `:name`을 가져서는 안된다는 것은 아닙니다. 만약 텍스트에서 더 상세한 개체명 타입이 명시적으로 드러났다면, 그것을 그대로 개체명 타입으로 쓰는 것은 바람직합니다. 예를 들어 *"국가기간통신사인 연합뉴스와 후발 민영 통신사인 뉴시스, 뉴스1이..."* 라는 문장이 있다면 '연합뉴스'에 대해 `(국 / 국가기간통신사)`로 주석하는 것이 더 좋은 방법입니다. 하지만 단순하게 *"연합뉴스와..."* 같은 문장에 대해서는 개체명 타입을 무엇으로 정해야 할지 고민될 수 있습니다. 이런 경우에 아래의 목록에서 하나를 고르세요. ([Selecting a Named Entity Type](https://www.isi.edu/~ulf/amr/lib/popup/ne-type-selection.html) 문서를 참고하세요.)

- **`person`**, `family`, `animal`, `language`, `nationality`, `ethnic-group`, `regional-group`, `religious-group`, `political-movement`
- **`organization`**, `company`, `government-organization`, `military`, `criminal-organization`, `political-party`, `market-sector`, `school`, `university`, `research-institute`, `team`, `league`
- **`location`**, `city`, `city-district`, `county`, `state`, `province`, `territory`, `country`, `local-region`, `country-region`, `world-region`, `continent`; `ocean`, `sea`, `lake`, `river`, `gulf`, `bay`, `strait`, `canal`; `peninsula`, `mountain`, `volcano`, `valley`, `canyon`, `island`, `desert`, `forest`, `moon`, `planet`, `star`, `constellation`
- **`facility`**, `airport`, `station`, `port`, `tunnel`, `bridge`, `road`, `railway-line`, `canal`, `building`, `theater`, `museum`, `palace`, `hotel`, `worship-place`, `market`, `sports-facility`, `park`, `zoo`, `amusement-park`
- **`event`**, `incident`, `natural-disaster`, `earthquake`, `war`, `conference`, `game`, `festival`
- **`product`**, `vehicle`, `ship`, `aircraft`, `aircraft-type`, `spaceship`, `car-make`, `work-of-art`, `picture`, `music`, `show`, `broadcast-program`
- **`publication`**, `book`, `newspaper`, `magazine`, `journal`
- **`natural-object`**
- **`award`**, `law`, `court-decision`, `treaty`, `music-key`, `musical-note`, `food-dish`, `writing-script`, `variable`, `program`

*의생명 도메인 특화 NE 타입 (BioAMR):*

- **`molecular-physical-entity`**, `small-molecule`, `protein`, `protein-family`, `protein-segment`, `amino-acid`, `macro-molecular-complex`, `enzyme`, `nucleic-acid`
- **`pathway`**, `gene`, `dna-sequence`, `cell`, `cell-line`, `species`, `taxon`, `disease`, `medical-condition`

NE가 **아닌** 것:

- 신문 기사의 헤드라인, 잡지 기사, 논문의 제목 등
- 특수 프레임: [`byline-91`](https://www.isi.edu/~ulf/amr/ontonotes-4.0-frames/byline-n.html), [`street-address-91`](https://www.isi.edu/~ulf/amr/ontonotes-4.0-frames/street-address-n.html) 바이라인과 도로명 주소는 이름으로 주석되지 않고, 부수적인 구성 요소로서 이름을 가지는 것으로 취급됩니다.

늘 가장 세분류된 개체명 타입을 사용해야 합니다. 위에서 보이는 타입들 중에서 찾을 수 없는 경우에는 `thing`을 사용할 수 있습니다.

~~~lisp
(a / award
    :wiki "노벨상"
    :name (이 / 이름
        :op1 "노벨상"))
~~~
> 노벨상

~~~lisp
(g / government-organization
    :wiki "대한민국_국가정보원"
    :name (이 / 이름
        :op1 "국정원")
    :mod (c / country
        :wiki "대한민국"
        :name (이2 / 이름 :op1 "한국")))
~~~
> 한국의 국정원

~~~lisp
(n / natural-object
    :wiki "정이품송"
    :name (이 / 이름
        :op1 "보은"
        :op2 "속리"
        :op3 "정이품송"))
~~~
> 보은 속리 정이품송

텍스트에서 개체명의 타입이 명시적으로 드러나 있다면, 해당 표현을 그대로 활용할 수 있습니다.

~~~lisp
(시 / 시인
    :wiki "윤동주"
    :name (이 / 이름 :op1 "윤동주"))
~~~
> 시인 윤동주
>
> 윤동주 시인

`시인`은 `person`보다 더 세분화된 타입이죠.

~~~lisp
(마 / 마을
    :wiki -
    :name (이 / 이름
        :op1 "낙천리"
        :op2 "아홉굿"
        :op3 "마을"))
~~~
> 낙천리 아홉굿 마을

마찬가지로 `마을`은 `city`보다 더 세분화된 타입입니다.

~~~lisp
(박 / 박사
    :wiki -
    :name (이 / 이름
        :op1 "한"))
~~~
> 한 박사님

아래 예문들은 `지방`, `정당`, `우주선`에 대해서 언급하고 있지만, 아래와 같은 경우에 대해서는 표준 NE 타입인 `country-region`, `political-party`, `spaceship`을 사용합니다. 후자가 더 세분화된 타입이거나 적어도 동등한 수준의 세분화를 보이고 있기 때문입니다.

~~~lisp
(c / country-region
    :wiki "다르푸르"
    :name (이 / 이름 :op1 "다르푸르")
    :location (c2 / country :wiki "수단" :name (이2 / 이름 :op1 "수단")))
~~~
> 수단의 다르푸르 지방

~~~lisp
(p / political-party
    :wiki "독일_기독교민주연합"
    :name (이 / 이름 :op1 "CDU")
    :mod (중 / 중도우파)
    :mod (c / country :wiki "독일" :name (이2 / 이름 :op1 "독일")))
~~~
> 독일의 중도우파 정당인 CDU

~~~lisp
(s / spaceship
   :wiki "보스토크_(우주선)"
   :name (이 / 이름 :op1 "보스토크"))
~~~
> 우주선 보스토크
>
> 보스토크 우주선

단순히 존칭에 해당되는 "선생", "선생님", "사모님", "사장님" 등은 이름의 일부로 포함시킵니다. 그러나 인명이나 직위명에 직접 붙여쓰는 '-님'은 포함시키지 않습니다. (예: "김연세님"은 `"김연세"`로 "과장님"은 `have-org-role-91`에서 `과장`으로 처리합니다.)

~~~lisp
(p / person
    :wiki "윤동주"
    :name (이 / 이름
        :op1 "윤동주"
        :op2 "선생"))
~~~
> 윤동주 선생께서는

다음 챕터인 "[역할, 직위를 위한 특수 프레임](#%EC%97%AD%ED%95%A0-%EC%A7%81%EC%9C%84%EB%A5%BC-%EC%9C%84%ED%95%9C-%ED%8A%B9%EC%88%98-%ED%94%84%EB%A0%88%EC%9E%84-special-frames-for-roles)"에서 "대통령" 등의 직위명을 어떻게 처리하는지 확인하세요.

동격어구(appositive)의 경우에도 정보들을 슬롯에 차근차근 채우면 됩니다.

~~~lisp
(c / company
    :wiki "성심당"
    :name (이 / 이름
        :op1 "성심당")
    :ARG1-of (자 / 자랑-01
        :ARG0 (시 / 시민
            :mod (c2 / city
                :wiki "대전광역시"
                :name (이2 / 이름 :op1 "대전")))))
~~~
> 성심당, 대전시민의 자랑거리

만약 "베이커리"나 "빵집"과 같은 단어가 텍스트에 나왔다면 `(c / company)` 대신 `(빵 / 빵집)`처럼 썼을 것입니다. 

간혹 같은 인스턴스에 대해 둘 이상의 타입이 언급될 때가 있습니다. 이런 경우에는 단순히 `:domain`의 역인 `:mod`를 활용하여 처리합니다.

~~~lisp
(변 / 변호사 :wiki - :name (이 / 이름 :op1 "최연세")
    :mod (작 / 작가
        :ARG1 (주 / 주목-01)))
~~~
> 주목받는 작가 최연세 변호사

만약 개체명이 하이픈으로 연결되어 있거나 소유격형일 때, 띄어쓰기가 잘못 되었을 때에도 표현된 그대로 주석합니다.

예를 들어 "연세-칼자이스 이미징센터"는 어절 단위로 `:op1 "연세-칼자이스"`와 `:op2 "이미징센터"`만 쓰입니다.


## 역할, 직위를 위한 특수 프레임 ([Special Frames for Roles](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#special-frames-for-roles))

기관이나 단체에서의 역할을 주석하기 위해 `have-org-role-91`을 사용합니다.

~~~lisp
(p / person 
    :wiki "도널드_트럼프"
    :name (이 / 이름 :op1 "트럼프")
    :ARG0-of (h / have-org-role-91
        :ARG1 (c / country :wiki "미국" :name (이2 / 이름 :op1 "미국"))
        :ARG2 (대 / 대통령)))
~~~
> 미국 트럼프 대통령

`have-org-role-91`의 필수역:

- `:ARG0`: 해당 인물 (office holder; 대개의 경우 자연인)
- `:ARG1`: 기관 및 단체 (the organization)
- `:ARG2`: 직위 또는 역할 (title of the office held, 예: 대통령)
- `:ARG3`: 담당 업무 (a description of responsibility; 거의 쓰이지 않음)

`have-org-role-91`이 쓰이는 전형적인 직위 또는 역할은 다음과 같습니다: 대사(ambassador), 대주교(archbishop), 주교(bishop), CEO, 의장(chairman), 수상(chancellor), 팀장(chief of staﬀ), 위원(commissioner), 국회의원(congressman), 대표자(deputy), 통치자(dictator), 황제(emperor/empress), 외교관(envoy), 외교부 장관(foreign minister), 지사(governor), 왕(king/queen), 시장(mayor), 군주(monarch), 사무관(oﬃcer), 공무원(oﬃcial), 교황(pope), 총리(premier), 대통령(president), 교장(principal), 교수(professor), 비서(secretary), 대변인(spokesman), 회계원(treasurer) 등. 

둘 또는 그 이상의 사람들 사이의 관계를 표상하기 위해 `have-rel-role-91`을 사용합니다.

~~~lisp
(h / have-rel-role-91
    :ARG0 (그 / 그)
    :ARG1 (나 / 나)
    :ARG2 (처 / 처남))
~~~
> 그는 내 처남이다.

`have-rel-role-91`의 필수역:

- `:ARG0`: 개체 A
- `:ARG1`: 개체 B
- `:ARG2`: 개체 A의 역할 (반드시 명시되어야 함)
- `:ARG3`: 개체 B의 역할 (대개 명시되지 않음)
- `:ARG4`: 관계의 근거 (계약, 판결 등 법적 효력; 거의 쓰이지 않음)

`have-rel-role-91`이 쓰이는 전형적인 직위 또는 역할은 다음과 같습니다: 아버지(father), 자매(sister), 남편(husband), 손자(grandson), 대부(godfather), 의붓딸(stepdaughter), 매형 또는 처남(brother-in-law); 친구(friend), 남자친구(boyfriend), 동료(buddy), 적(enemy); 집주인(landlord), 세입자(tenant) 등.


## 정확한 수 ([Exact numbers](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#exact-numbers))

AMR에서 수는 정규화됩니다.

~~~lisp
(궁 / 궁녀
    :quant 3000)
~~~
> 삼천 궁녀
>
> 궁녀 3,000

~~~lisp
(원 / 원자
    :quant 1500000000
    :unit (개 / 개))
~~~
> 15억 개의 원자
>
> 원자 1,500,000,000개

이런 식의 정규화는 아시아식 셈법(만 단위 기준)과 서양식 셈법(천 단위 기준) 사이의 일관된 주석을 가능하게 합니다.


## 대략적인 수 ([Approximate numbers](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#approximate-numbers))

근사값 등의 대략적인 수는 `:opN`을 활용합니다. ('수백'의 경우 하한점이 100이 되기 때문에 `:op1 100`입니다. 상한점은 특정할 수 없으니 표상하지 않습니다.)

~~~lisp
(소 / 소년
    :unit (명 / 명)
    :quant (수 / 수백
        :op1 100))
~~~
> 수백 명의 소년들
>
> 소년들 수백 명

~~~lisp
(소 / 소년
    :unit (명 / 명)
    :quant (수 / 수십
        :op1 10))
~~~
> 수십의 소년들
>
> 소년들 수십

~~~lisp
(소 / 소년
    :quant (이 / 이상
        :op1 4000))
~~~
> 4,000 이상의 소년들
>
> 4천 이상의 소년들

~~~lisp
(소 / 소년
    :quant (사 / 사이
        :op1 4000
        :op2 5000))
~~~
> 4,000에서 5,000 사이의 소년들
>
> 4~5천 명의 소년들


## 수량 ([Quantities](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#quantities))

정확한 수량은 타입(표현)과 `:unit`, `:quant` 역할들을 활용하여 표상합니다.

~~~lisp
(d / distance-quantity 
   :unit (미 / 미터) 
   :quant 100)
~~~
> 100 미터

대략적인 수량은 `:opN`을 활용하여 표상합니다.

~~~lisp
(약 / 약 
    :op1 (d / distance-quantity 
        :unit (미 / 미터) 
        :quant 100))
~~~
> 약 100 미터

AMR에서는 "2리터의 우유", "우유 2리터"와 같은 양화 표현을 ('리터'가 아닌) '우유'로 봅니다.

~~~lisp
(사 / 사-01
    :ARG0 (여 / 여자)
    :ARG1 (우 / 우유
        :quant (v / volume-quantity 
            :unit (리 / 리터) 
            :quant 2)))
~~~
> 2리터의 우유
>
> 우유 2리터

시간적 구간(stretch)이나 상대적인 시간은 `temporal-quantity`를 활용합니다. (절대적 시간은 `date-entity`를 활용합니다. [다음 챕터](#%EA%B8%B0%ED%83%80-%EA%B0%9C%EC%B2%B4-%EB%82%A0%EC%A7%9C-%EC%8B%9C%EA%B0%84-%EB%B0%B1%EB%B6%84%EC%9C%A8-%EC%A0%84%ED%99%94%EB%B2%88%ED%98%B8-%EC%9D%B4%EB%A9%94%EC%9D%BC-url-other-entities-dates-times-percentages-phone-email-urls)에서 설명합니다.)

~~~lisp
(t / temporal-quantity
    :unit (년 / 년)
    :quant 30)
~~~
> 30년

~~~lisp
(이 / 이전
    :op1 (지 / 지금)
    :duration (t / temporal-quantity
        :unit (년 / 년)
        :quant 30))
~~~
> 지난 30년간
>
> 지금으로부터 30년 동안

~~~lisp
(전 / 전
    :op1 (지 / 지금)
    :quant (t / temporal-quantity
        :unit (년 / 년)
        :quant 30))
~~~
> 30년 전

~~~lisp
(전 / 전
    :op1 (지 / 지금)
    :quant (이 / 이상
        :op1(t / temporal-quantity
            :unit (년 / 년)
            :quant 30)))
~~~
> 30년 전도 더 전에

논리합(disjunction)은 상위에 놓입니다.

~~~lisp
(o / or
    :op1 (t / temporal-quantity
        :unit (년 / 년)
        :quant 3)
    :op2 (t2 / temporal-quantity
        :unit (년2 / 년)
        :quant 4))
~~~
> 3년 혹은 4년
>
> 3년이나 4년

~~~lisp
(o / or
    :op1 (t / temporal-quantity
        :unit (개 / 개월)
        :quant 6)
    :op2 (t2 / temporal-quantity
        :unit (년 / 년)
        :quant 1))
~~~
> 반년이나 한 해
>
> 6개월 혹은 1년

상대적인 위치 역시 수량을 포함할 때가 있습니다.

~~~lisp
(추 / 추락-01
   :ARG1 (비 / 비행기)
   :location (r / relative-position
        :op1 (c / city :wiki "모스크바" :name (이 / 이름 :op1 "모스크바"))
        :quant (d / distance-quantity 
            :unit (마 / 마일)
            :quant 50)
        :direction (동 / 동쪽)))
~~~
> 비행기는 모스크바로부터 동쪽으로 50마일 지점에 추락했다.
>
> 모스크바 동쪽 50마일 떨어진 곳에 비행기가 추락했다.

`X-quantity` 노테이션은 명확한 수량에만 쓰이는 것입니다. 분명하지 않은 수량에 대해서는 단순히 `:quant`로만 주석하면 됩니다.

~~~lisp
(모 / 모으-01
    :ARG1 (사 / 사람
        :quant (수 / 수
            :ARG1-of (많 / 많-01))))
~~~
> 많은 수의 사람들이 모였다.

가끔 계량(measurement) 그 자체가 더 상위의 노드가 되기도 합니다.

~~~lisp
(증 / 증가-01
   :ARG1 (수 / 수
        :quant-of (사 / 사람)))
~~~
> 사람들의 수가 증가하고 있다.

수량 타입은 다음과 같습니다: `monetary-quantity`, `distance-quantity`, `area-quantity`, `volume-quantity`, `temporal-quantity`, `frequency-quantity`, `speed-quantity`, `acceleration-quantity`, `mass-quantity`, `force-quantity`, `pressure-quantity`, `energy-quantity`, `power-quantity`, `voltage-quantity` (빠지직!), `charge-quantity`, `potential-quantity`, `resistance-quantity`, `inductance-quantity`, `magnetic-field-quantity`, `magnetic-flux-quantity`, `radiation-quantity`, `concentration-quantity`, `temperature-quantity`, `score-quantity`, `fuel-consumption-quantity`, `seismic-quantity`

~~~lisp
(m / monetary-quantity
    :quant 20
    :unit (달 / 달러
        :mod (c / country
            :wiki "캐나다"
            :name (이 / 이름 :op1 "캐나다"))))
~~~
> 20 캐나다 달러
>
> C$20

`:quant 0` 값이 정말로 0-수량을 나타내는 게 아닌 경우에는 `:unit` 대신에 `:scale`을 활용하세요.

~~~lisp
(s / seismic-quantity
    :quant 7.9
    :scale (리 / 리히터))
~~~
> 7.9 리히터 규모

`have-quant-91`은 `:quant`의 구체화된 개념입니다. 논항은 `have-degree-91`와 유사하며, 사물의 질적인 부분이 아닌 양적인 부분에 대한 비교 또는 최상급을 표상하기 위해 활용됩니다. [AMR Dictionary](https://amr.isi.edu/doc/amr-dict.html)에서 `have-quant-91`과 `have-degree-91`이 각각 어떤 경우에 활용되는지 예제들을 확인할 수 있습니다.

~~~lisp
have-quant-91
    ARG1: 개체 (수량으로 취급될 대상)
    ARG2: 수량 (수치 또는 '많은'과 같은 양화사)
    ARG3: 정도 (더, 덜, 너무 등)
    ARG4: 비교 대상
    ARG5: 최상급: 상위집합에 대한 참조(reference to superset)
    ARG6: 후속 사건, 결과
~~~

~~~lisp
(파 / 팔-01
    :ARG0 (그 / 그)
    :ARG1 (차 / 차
        :ARG1-of (h / have-quant-91
            :ARG4 (차2 / 차
                :ARG1-of (팔2 / 팔-01
                    :ARG0 (사 / 사람
                        :ARG0-of (경 / 경쟁-01
                            :ARG1 그)))))))
~~~
> 그는 경쟁자들만큼 차를 팔았다.
>
> 그는 그의 경쟁자들이 파는 만큼의 차들을 팔았다.

~~~lisp
(파 / 팔-01
    :ARG0 (그 / 그)
    :ARG1 (차 / 차
        :ARG1-of (h / have-quant-91
            :ARG2 (많 / 많-01)
            :ARG3 (가 / 가장)
            :ARG5 (차2 / 차
                :ARG1-of (팔2 / 팔-01
                    :ARG0 (사 / 사람
                        :ARG0-of (경 / 경쟁-01
                            :ARG1 그)))))))
~~~
> 그는 경쟁자들 중에서 가장 많은 차를 팔았다.

~~~lisp
(얻 / 얻-01
    :polarity -
    :ARG1 (물 / 물
        :purpose (마 / 마시-01)
        :ARG1-of (h / have-quant-91
            :ARG2 (충 / 충분-01)
            :ARG6 (지 / 지속-01
                :ARG1 얻
                :duration (t / temporal-quantity :quant 1
                    :unit (주 / 주))))))
~~~
> 마실 물을 충분히 얻을 수 없는 상황이 1주일이나 지속됐다.


## 수학 연산자 ([Mathematical operators](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#mathematical-operators))

`product-of`와 `sum-of` 같은 특수 개념들은 텍스트의 의미가 담고 있는 수학적 연산을 표상하는 데 활용됩니다.

~~~lisp
(도 / 도달-01
    :ARG1 (속 / 속도
        :poss (함 / 함선))
    :ARG2 (p / product-of 
        :op1 3
        :op2 (속 / 속도
            :poss (음 / 음파))))
~~~
> 함선의 속도가 음속의 3배에 도달했다.

~~~lisp
(마 / 마치-01
    :ARG0 (p / person :wiki "일리우드_킵초게" :name (이 / 이름 :op1 "일리우드" :op2 "킵초게"))
    :ARG1 (달 / 달리-01
        :ARG0 p
        :ARG1 (마 / 마라톤)
        :duration (s / sum-of
            :op1 (t2 / temporal-quantity :quant 2
                :unit (시 / 시간))
            :op2 (t3 / temporal-quantity :quant 1
                :unit (분 / 분))
            :op3 (t4 / temporal-quantity :quant 39
                :unit (초 / 초)))))
~~~
> 일리우드 킵초게는 2시간 1분 39초의 기록으로 마라톤을 완주했다.


## 기타 개체: 날짜, 시간, 백분율, 전화번호, 이메일, URL ([Other entities: dates, times, percentages, phone, email, URLs](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#other-entities-dates-times-percentages-phone-email-urls))

기타 개체들은 표준화된 형태로 표상됩니다.

~~~lisp
 (d / date-entity
    :year 2012
    :month 2
    :day 29)
~~~
> 2012년 2월 29일
>
> 2012-02-29


~~~lisp
(d / date-entity
    :year 2012)
~~~
> 2012
>
> 2012년

~~~lisp
(d / date-entity
    :month 4)
~~~
> 4월

~~~lisp
(d / date-entity
    :weekday (금 / 금요일))
~~~
> 금요일

~~~lisp
(d / date-entity
    :year 2012
    :month 2)
~~~
> 2012년 2월

~~~lisp
(d / date-entity
    :month 2
    :day 29
    :weekday (수 / 수요일))
~~~
> 2월 29일 수요일

~~~lisp
(d / date-entity
    :day 29)
~~~
> 29일

~~~lisp
(d / date-entity
    :month 2
    :day 29
    :weekday (수 / 수요일)
    :time 16:30
    :timezone (p / PST))
~~~

> 2월 29일 수요일, 16:30 PST

~~~lisp
(d / date-entity
    :time 16:30)
~~~
> 16:30
>
> 4:30 PM
>
> 오후 4시 30분
>
> 4시 반

~~~lisp
(d / date-entity
    :era "세종"
    :year 28
    :month 10
    :day 9
    :calendar (c / country :wiki "조선" :name (이 / 이름 :op1 "조선조")))
~~~
> 조선조 세종 28년 10월 9일

~~~lisp
 (d / date-entity
    :year 2011
    :quarter 4)
~~~
> 2011년 4/4분기
>
> 2011Q4

~~~lisp
(d / date-entity
   :year 2011
   :season (여 / 여름))
~~~
> 2011년 여름

~~~lisp
(d / date-entity
    :year 2011
    :year2 2012
    :season (겨 / 겨울))
~~~
> 2011-2012 동계 시즌

~~~lisp
 (d / date-entity
    :year 2011
    :year2 2012
    :calendar (학 / 학년도))
~~~
> 2011-2012 학년도

~~~lisp
 (d / date-entity
    :year 2012
    :calendar (연 / 연도
        :mod (회 / 회계)
        :mod (g / government-organization
            :wiki "대한민국_정부" 
            :name (이 / 이름 :op1 "한국" :op2 "정부"))))
~~~

> 한국 정부 2012 회계 연도

~~~lisp
(d / date-interval
   :op1 (d2 / date-entity :year 2012 :month 3 :day 8)
   :op2 (d3 / date-entity :year 2012 :month 3 :day 9))
~~~
> 2012년 3월 8-9일
>
> 2012.03.08 ~ 2012.03.09

~~~lisp
(d / date-interval
   :op1 (d2 / date-entity :year 1939 :month 9 :day 1)
   :op2 (d3 / date-entity :year 1945 :month 5 :day 8))
~~~
> 1939년 9월 1일 - 1945년 5월 8일

~~~lisp
(p / percentage-entity :value 25)
~~~
> 25%
>
> 25 퍼센트

~~~lisp
(p / phone-number-entity :value "1-800-555-1212")
~~~
> 1-800-555-1212
>
> 1 (800) 555-1212

~~~lisp
(e / email-address-entity :value "president@korea.kr")
~~~
> president@korea.kr

~~~lisp
(u / url-entity :value "https://www.president.go.kr")
~~~
> https://www.president.go.kr

그 밖에 다양한 특수 프레임과 개체들을 더 살펴 보세요: `byline-91`, `correlate-91` (*"많을 수록 기쁨도 커진다"*), `course-91`, `have-degree-of-resemblance-91` (*"X는 Z이기 보다는 Y에 더 가깝다"*), `hyperlink-91`, `instead-of-91`, `publication-91`, `request-confirmation-91`, `score-entity`, `score-on-scale-91`, `statistical-test-91`, `street-address-91`, `string-entity`, `value-interval`, `variable`, 

아래 페이지를 참고하면 특수 프레임과 논항 정보를 쉽게 찾을 수 있습니다.

 * AMR Dictionary: [https://amr.isi.edu/doc/amr-dict.html](https://amr.isi.edu/doc/amr-dict.html) 
 * AMR용 PropBank의 프레임 목록 (English AMR 기준): [https://amr.isi.edu/doc/propbank-amr-frames-arg-descr.txt](https://amr.isi.edu/doc/propbank-amr-frames-arg-descr.txt)


## 추가 정보 ([Further information](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#further-information))

아래의 웹페이지에서 English AMR의 예시 등을 참고할 수 있습니다. 한국어 AMR을 작성할 때에 (정말로) 많은 도움이 되니 고민이 될 때엔 꼭 찾아 보세요!

+ AMR Dictionary: https://amr.isi.edu/doc/amr-dict.html
+ AMR page at ISI: https://amr.isi.edu
+ List of AMR NE types: https://amr.isi.edu/doc/ne-types.html
+ List of AMR roles: https://amr.isi.edu/doc/roles.html
+ List of AMR quantity types: https://amr.isi.edu/doc/quantity-types.html
+ List of frame arguments in PropBank (AMR version): https://amr.isi.edu/doc/propbank-amr-frames-arg-descr.txt

한국어 PropBank는 Linguistic Data Consortium에서 얻을 수 있습니다.
+ Korean PropBank: https://catalog.ldc.upenn.edu/LDC2006T03

AMR과 관련 논문들을 찾아보고 싶다면, 아래 페이지에 정리가 잘 되어 있습니다.
+ AMR Bibliography: https://nert-nlp.github.io/AMR-Bibliography/

한국어 AMR 가이드라인의 일부 내용은 아래 논문을 토대로 합니다.
+ Hyonsu Choe, Jiyoon Han, Hyejin Park, Hansaem Kim. ["Copula and Case-Stacking Annotations for Korean AMR."](https://www.aclweb.org/anthology/papers/W/W19/W19-3314/) *Proceedings of the First International Workshop on Designing Meaning Representations* (2019)

한국어 AMR 가이드라인은 [제가](mailto:choehyonsu@yonsei.ac.kr) 관리하고 있습니다. 한국어 AMR과 관련된 의견들을 기다립니다!
+ ***[Hyonsu Gabrielle Choe](mailto:choehyonsu@yonsei.ac.kr)*** (연세대학교 언어정보연구원 언어관측소, 연세대학교 언어정보학협동과정 전산언어학 전공)

한국어 AMR 가이드라인에 대한 인용은 아래의 논문을 기준으로 부탁드립니다.

+ 최현수, 한지윤, 박혜진, 오태환, 박석원, 김한샘. ["문장 의미의 그래프 구조 표상을 위한 한국어 Abstract Meaning Representation 가이드라인"](http://hclt.kr/symp/?lnb=conference) *제31회 한글 및 한국어 정보처리 학술대회 논문집* pp.252-257 (2019) 


## AMR 기인열전 ([AMR Freak Show](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#further-information))

이 챕터는 읽지 않아도 그만입니다. AMR에 내재된 수학적 문제를 향한 호기심은 결국 몇몇 수학자나 아이들에 대한 관심으로 이어지고 말 거예요.

### 순환성 ([cycle](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#cycles))

아래 보이는 AMR은 순환(cycle)을 가진 것처럼 보입니다. `여`가 `여`의 하위 노드(sub-node)로 있기 때문이죠. 그러나 실제로는 순환이 생긴 것은 아닙니다. 저 중에 하나는 역관계(`:ARG0-of`)에 해당하고, 해당 관계를 뒤집으면 어쨌거나 루트가 재귀적으로 참조되는 일은 없습니다.

~~~lisp
(여 / 여자 
    :ARG0-of (잃 / 잃-01 
        :ARG1 (스 / 스카프 
            :poss 여)))
~~~
> 스카프를 잃어 버린 여자

(영어를 기준으로) 대략 0.3%의 AMR에서 순환이 발생했다고 합니다.

~~~lisp
(공 / 공정 
    :purpose (확 / 확보-01 
        :ARG0 공
        :ARG1 (품 / 품질)))
~~~
> 품질 확보를 위한 공정

이러한 순환성은 주로 `:concession`, `:condition`, `:manner`, `:purpose`, `:time`를 활용한 AMR에서 나타납니다.

구체화를 활용하면 마법처럼 사라지기도 하죠.

~~~lisp
(공 / 공정 
    :ARG1-of (h / have-purpose-91 
        :ARG2 (확 / 확보-01 
            :ARG0 공
            :ARG1 (품 / 품질))))
~~~

### 그래프로 인코딩할 때의 여러 방법들 (Different textual ways to encode a graph)

마지막으로, 같은 문장을 AMR로 표상할 때 방법들이 조금씩 다른 경우가 있습니다. ("소년은 누군가 자신을 믿는 것을 좋아한다.")

~~~lisp
(좋 / 좋-02                    (좋 / 좋-02
   :ARG0 (소 / 소년)                 :ARG0 (소 / 소년
   :ARG1 (믿 / 믿-01                     :ARG1-of (믿 / 믿-01))
             :ARG1 소))             :ARG1 소)
~~~

현명한 작업자들이라면 왼쪽 AMR을 더 선호할 겁니다. 같은 트리플 사이의 연결을 어떻게 할까의 문제일 뿐, 결국 구조는 똑같기 때문이죠.

## 참고 문헌 ([References](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#references))

- Banarescu, Laura, Claire Bonial, Shu Cai, Madalina Georgescu, Kira Griffitt, Ulf Hermjakob, Kevin Knight, Philipp Koehn, Martha Palmer, and Nathan Schneider. "Abstract Meaning Representation for Sembanking." *Proceedings of the 7th Linguistic Annotation Workshop* (2013).
- Bonial, Claire, Bianca Badarau, Kira Griffitt, Ulf Hermjakob, Kevin Knight, Tim O'Gorman, Martha Palmer and Nathan Schneider. "Abstract Meaning Representation of Constructions: The More We Include, the Better the Representation." *11th Language Resources and Evaluation Conference* (2018).
- Carpenter, Bob. "The Logic of Typed Feature Structures". *Number 32 in Cambridge Tracts in Theoretical Computer Science.* (1992).
- Davidson, Donald. "The logical form of action sentences." (1967).
- Elhadad, Michael. "Using argumentation in text generation." *Journal of Pragmatics* 24.1 (1995): 189-220.
- Higginbotham, James. "On semantics." *Linguistic inquiry* 16.4 (1985): 547-593.
- Kay, Martin. "Functional grammar." *Annual Meeting of the Berkeley Linguistics Society.* Vol. 5. (1979).
- Knight, Kevin. "Unification: A multidisciplinary survey." *ACM Computing Surveys (CSUR)* 21.1 (1989): 93-124.
- Knight, Kevin, and Vasileios Hatzivassiloglou. "Two-level, many-paths generation." *Proceedings of the 33rd annual meeting on Association for Computational Linguistics* (1995).
- Mann, William C. "An Overview of the Penman Text Generation System". No. ISI/RR-83-114. (1983).
- Moore, Robert C. "Unification-based semantic interpretation." *Proceedings of the 27th annual meeting on Association for Computational Linguistics* (1989).
- Shieber, Stuart M. "An Introduction to Unification-Based Approaches to Grammar." (1986).