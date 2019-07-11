# 한국어 추상 의미 표현(AMR) 주석 지침: Korean Abstract Meaning Representation(AMR) Specification
**July 11, 2019**


*최현수, 박혜진, 한지윤, 김한샘*
*(Secondary condtributors: 김미경, 김영상, 노영빈, 류보람, 오태환, 이보미, 장연지, 정진경, Fei Li)*


# Disclaimer & dependency
한국어 AMR 주석 지침은 Abstract Meaning Representation (AMR) 1.2.6 Specification [[Banarescu et al., 2019](https://github.com/amrisi/amr-guidelines/blob/master/amr.md)](이하 English AMR)을 기반으로 합니다. English AMR의 주석 예시를 바탕으로 한국어의 주석 지침을 확정하기 위해 아래의 자료들을 참고하였습니다. 본 문서에서 제시하는 한국어 AMR 주석 지침은 공인된 지침이 아닙니다.

+ [AMR Annotation Dictionary](https://www.isi.edu/~ulf/amr/lib/amr-dict.html)
+ [AMR Roles](https://www.isi.edu/~ulf/amr/lib/roles.html)
+ [Named Entity types for AMRs](https://www.isi.edu/~ulf/amr/lib/ne-types.html)

각 챕터의 내용은 English AMR을 한국어의 현상에 맞게 수정(Localization)한 것입니다. 각 챕터의 제목에는 대응되는 원문의 링크가 포함되어 있습니다.


# I. 서론 ([Introduction](https://github.com/amrisi/amr-guidelines/blob/master/amr.md#part-i-introduction))

AMR은 문장의 “누가 누구에게 무엇을 한다”하는 의미에 집중한다. 모든 문장들은 **루트를 가지고(rooted), 방향을 갖는(directed), 비순환 그래프(acyclic Graph)**로 표현된다. AMR은 관계를 드러내는 엣지(edge)와 개념을 나타내는 노드(leaves)로 이루어진다.

AMR은 파스 트리(Parse tree)처럼, 모든 노드에 도달 가능한(traversable) 단일 그래프 상에 연관된 단어들을 포괄한다. 즉 여러 층위의 주석이 분리된 것이 아니다. 파스 트리와는 다르게 AMR은 추상적이다. 각각의 문장들이 가지는 개념적 의미가 동일하다면, 이들 문장들은 동일한 AMR로 표현될 수 있다. (이는 하나의 AMR과 특정한 한 문장 사이의 관계를 보장하지 않음을 뜻한다. 뜻은 같더라도 말을 어떻게 하는가는 다른 문제다.) 또한 의존 파싱(Dependency parse)처럼 문장 내의 모든 개별 단어에 대해 주석을 하는 것은 아니다.

개별 언어의 문장을 AMR로 표현하는 작업에 있어서, 어떻게 작업해야 한다는 원칙에 대해서는 특별히 제약을 두지 않는다. 한국어 문장을 바탕으로 표현된 AMR은 한국어에만 적합한 것일 수 있다. AMR은 언어 간의 호환성을 보장하지 않는다. (AMR is not an interlingua.)
