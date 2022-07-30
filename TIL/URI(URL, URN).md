## **URL이란?**

우리는 매일 URL을 처리해야 합니다. *URL은 Uniform Resource Locator* 의 약자입니다 . 간단히 *address* 라고 부를 수 있습니다 . 주소라는 용어는 URL의 역할을 잘 설명합니다. 집 주소와 같은 URL을 생각할 수 있습니다. 여기에는 집을 찾는 데 필요한 모든 정보가 포함되어 있습니다.

마찬가지로, 웹 페이지, 이미지, 사서함 등 인터넷에서 주어진 리소스의 위치를 나타내는 문자열로 URL을 정의 할 수 있습니다.

```
URL의 예입니다.

https://jwt.io
https://auth0.com/docs/get-started#learn-the-basics
https://identicons.dev/static/icons/mono/png/icon-access-token.png
mailto:yourfriend@somewhere.com
ftp://ftpserver.com/myfolder
```

### **URL 및 링크**

URL과 링크라는 용어는 일반적으로 같은 의미로 사용되지만 기술적으로는 동의어가 아닙니다. URL은 리소스를 찾을 수 있는 문자열입니다. 링크(하이퍼링크의 줄임말)는 브라우저의 지정된 URL에서 리소스를 로드할 수 있도록 하는 HTML 요소입니다. 따라서 링크는 URL에 의존하고 URL은 링크 없이 존재할 수 있지만 URL이 없는 링크는 의미가 없습니다(적어도 [원래 의미](https://christianheilmann.com/2019/02/05/links-that-dont-go-anywhere-should-be-buttons/) 에서는 ).

### **URL 분석**

URL 약어 의 *Uniform* 부분은 이러한 로케이터 문자열의 공통 구조에 관한 것입니다. 다음 이미지는 이 표준 구조를 보여줍니다.

![https://images.ctfassets.net/23aumh6u8s0i/67pmAyqHVJOOSlR4hVGkrS/5cd75492ee2ffba9720906099236939c/url-anatomy.png](https://images.ctfassets.net/23aumh6u8s0i/67pmAyqHVJOOSlR4hVGkrS/5cd75492ee2ffba9720906099236939c/url-anatomy.png)

URL은 다음 부분으로 구성됩니다.

- *Scheme*
    
    URL에서 리소스에 액세스하는 데 사용해야 하는 프로토콜입니다. [잘 알려진 HTTP 및 HTTPS 외에도 많은 다른 체계](https://www.iana.org/assignments/uri-schemes/uri-schemes.xhtml)를 사용할 수 있습니다 .
    
- *도메인*
    
     **이 부분은 리소스를 호스팅하는 서버를 나타냅니다. [도메인 이름](https://en.wikipedia.org/wiki/Domain_name) 또는 IP 주소 일 수 있습니다 .
    
- *포트*
    
    리소스에 대한 액세스 요청을 보낼 프로토콜 포트입니다. 일반적으로 생략되므로 기본 프로토콜 포트를 사용해야 합니다.
    
- *경로*
    
    호스팅 서버의 리소스 경로입니다.
    
- *매개변수*
    
    : 호스팅 서버에 제공되는 선택적 추가 정보입니다.
    
- *Anchor조각*
    
    이 부분은 리소스 내부의 특정 부분을 나타냅니다. *조각* 이라고도 합니다 .
    

*도메인 이름과 포트(있는 경우)로 구성된 그룹은 Authority* 라고도 합니다 . 체계와 권한은 문자열로 구분됩니다 . URL에 권한이 없는 경우 스키마와 URL의 나머지 부분은 콜론으로만 구분됩니다 . 권한 부분이 없는 URL의 일반적인 예는 와 같이 이메일 주소를 나타내는 URL 입니다.`://:mailto:yourfriend@somewhere.com`

## ****URI란?****

*Uniform Resource Identifier* 를 나타냅니다 . 간단히 말해서 리소스를 식별하는 문자열입니다. 구문론적 관점에서 URI 문자열은 대부분 URL과 동일한 형식을 따릅니다. 😲

그렇다면 URL과 URI는 같은 것일까요? ( 흠… )

URL과 URI는 모두 동일한 사양을 따릅니다 . 그러나 URL을 사용하면 리소스를 *찾을* 수 있지만 URI는 단순히 리소스를 식별합니다. 이것은 URI가 반드시 리소스를 얻기 위한 주소로 의도된 것은 아님을 의미합니다. 그것은 단지 식별자로 의미됩니다.

주소 예제로 돌아가서, 당신이 당신의 마을에서 유일한 노란 집에 산다고 말하면, 당신은 거기에 가는 방법에 대한 지시를 제공하지 않습니다. 그러나 이 정보는 당신의 마을에 있는 다른 사람들 사이에서 당신의 집을 식별합니다.

반면에 URL은 URI입니다. 동일한 URI 구문을 사용한다는 사실 외에도 주소를 통해 리소스를 식별합니다. 즉, URL은 리소스를 식별하는 동시에 리소스에 액세스하는 방법을 알려주는 식별자입니다.

집 주소는 집 주소를 찾는 방법을 제공할 뿐만 아니라 또한 다른 것과 혼동하지 않도록 식별합니다.

간단히 말해서 URL은 URI의 하위 집합입니다.

## **URN이란 무엇입니까?**

URN 약어는 URL 및 URI보다 덜 유명하지만 같은 계열에 속합니다. *이는 Uniform Resource Name* 의 약자 이며 그 범위는 해당 리소스가 더 이상 존재하지 않는 후에도 *영구적으로* 리소스를 식별하는 것입니다.

URI와 달리 URN은 공공 표준 조직에서 발급한 식별자이며 컴퓨터 및 소프트웨어 시스템뿐만 아니라 인간 활동에서 표준 식별자가 필요한 모든 것을 포함할 수 있습니다.

중복개념차이점 요약

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c8ef0a94-a6d6-4dfb-86a4-f1a0774b826e/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c8ef0a94-a6d6-4dfb-86a4-f1a0774b826e/Untitled.png)

출처 : [https://auth0.com/blog/url-uri-urn-differences/](https://auth0.com/blog/url-uri-urn-differences/)
