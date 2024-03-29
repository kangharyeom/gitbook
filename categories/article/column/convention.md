# Code Convention의 중요성

'OKKY' 라는 커뮤니티 글을 서핑하던 중 흥미로운 글을 읽게 되어 칼럼을 남깁니다.
{% embed url="https://okky.kr/articles/1485829#note-1779432" %}

## 이야기를 시작하며

 흔히 개발자의 skill set 중에 가장 중요한 요소로 'communication'을 이야기 합니다. 일반적인 직업군들은  'communication'이라고하면
기본적인 의사소통을 뜻하거나 더 나아가 일종의 '업무 센스(sense)'를 뜻하기도 하는데요. 
 즉, 업무의 효용성을 높이는 언어적, 비언어적 소통 능력을 통칭하여 "커뮤니케이션이 잘되는 직원"이라고 판단합니다.  

 반면, 개발자의 'communication'은 앞서 언급한 기본적인 의사소통과 업무 센스에 더불어 '클린코드(Clean Code)'와 '코드 컨벤션(Code Convention)'을 갖추어야 합니다.
우선 '클린코드(Clean Code)'는 추후에 자세하게 이야기 해보는 것으로 하고 이번 칼럼에서는 '코드 컨벤션(Code Convention)'에 대해서 다뤄보도록 하겠습니다.

## '코드 컨벤션(Code Convention)'은 우리의 언어

 코드 컨벤션은 언어입니다. 다만, 한국어와 미국어 처럼 상호간에 소통이 불가능한 언어가 아닌 서울말과 부산말같은 일종의 방언과 같다고 할 수 있습니다.
의사소통에는 전혀 문제가 없지만 명확한 의사소통이 필요한 부분에서는 다소 불편함이 있는 그런 관계의 언어 입니다.
 방언은 내가 하고싶다면 하고 하기 싫다면 얼마든지 하지 않을 수 있으며, 그것이 내가 생활하는 것에 치명적인 영향력을 미치지 않지만, 
만약 상대방이 내가 구사하는 방언에 익숙하지 않다면 나의 의사를 전달할 때 내가 본래 의도했던 것을 명확하게 전달하지 못할 수 있습니다.

 코드 컨벤션도 마찬가지 입니다. 링크에 있는 예시와 같이 K&R 방식의 코드스타일을 활용하는 회사에서 BSD 코드스타일을 활용하게 된다면 K&R 방식에 익숙해진
직원들이 BSD 코드스타일을 읽는 것에 피로감이 있을겁니다. 단순하게 생각해보면 시원한 라거를 즐기는 모임에서 새로 들어온 멤버가 미지근한 에일을 함께 마시자고 하는 것과 같은 느낌일 것입니다.
따라서 코드 컨벤션은 "강제는 아니지만 가능하면(우리는 이것을 '반강제'라고 읽습니다)" 지키는 것이 좋습니다.

#### * BSD 코드 스타일
```java
    if(d==1)
    {
        if(b==1)
        { 
            로직
        }
        else
        {
            로직
        }
    }
```

#### * K&R 코드 스타일
```java
    if(d==1){
        if(b==1){
            로직
        }
        else{
            로직
        }
    }
```

## 코드 컨벤션의 중요성

### 가독성 향상 

 앞서 언급하였듯이 코드 컨벤션을 지키면 협업하는 개발자들이 코드를 읽기 쉽고 이해하기 쉬워집니다. 따라서 새로운 멤버가 유입되더라도 일관된 
교육을 진행할 수 있습니다.

### 유지 보수성 향상

 동일한 원칙으로 개발하면 개발과정에서 발생하는 에러나 버그를 더 빨리 발견할 수 있습니다. 문서 작성 - 이해 - 개발 - 에러 발견 - 에러 해결 과정이
동일하기 때문에 비교적 쉽고 간결하게 유지보수할 수 있습니다. 도화지에 그림을 그릴때 백지에서 시작하는 것보다 밑그림이 그려진 그림에서 시작하는 것이
더욱 쉽고 간결하듯 코드 컨벤션을 따르면 쉽고 간결하게 유지보수 할 수 있습니다.

### 팀 협동 능력 향상

 앞서 언급한 팀 커뮤니케이션 (또는 협동 능력)이 향상됩니다. 가령 "유지 보수를 용이하게 하기 위한 코드의 변경 및 줄임"을 "Refactor"라고 약속한다면
굳이 긴 문장을 활용하지 않고도 해당 기능을 표현할 수 있습니다. 또는 "치명적인 에러를 발견하였을 때"를 "Fixed"라고 하고 "단순히 코드를 가독성 좋게 변경하였을 때"는
"Refactor"라고 쓰기로 약속한다면 비슷한 의미로 표현되는 두가지 문장을 보다 명확하고 간결하게 구분지을 수 있습니다.


## 코드 컨벤션이 꼭 필요할까?

 앞서 언급한 코드 컨벤션의 중요성을 종합적으로 고려해 봤을 때 집단의 규모가 커지면 커질 수록 코드 컨벤션은 효율적일 것이라고 판단됩니다. 
가령 solo 프로젝트에서는 코드컨벤션을 지키지 않아도 전반적인 코드를 내가 알고 있기 때문에 불편함을 느끼지 못할 수 있습니다. 다만 solo 프로젝트라고 하더라도 
장기간 프로젝트를 진행하지 않은 경우 나만의 코드 컨벤션이 없다면 프로젝트를 다시 분석해야 하는 비효율을 야기할 수 있습니다.

 따라서, solo 프로젝트를 진행하든 team 프로젝트를 진행하든 코드 컨벤션을 구축하는 것을 지향하며 객관적인 시선에서 코드 컨벤션을 구축할 것을 권장합니다.