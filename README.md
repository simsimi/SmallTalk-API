https://workshop.simsimi.com/document

# 일상대화 API
심심이챗봇공방(SimSimi Workshop Services, SWS)은 전세계 약 3억 5천만 사용자들에게 즐거움을 제공해 온 일상대화챗봇 '심심이'를 바탕으로 서비스를 제공합니다. '심심이'가 꾸준히 성공적으로 서비스를 해 올 수 있었던 이유는, 세계 각지에서 다양한 배경을 가진 2천 2백만 명 이상의 패널들이 각자의 재치와 영감을 담아 만들어 온 생동감 넘치는 1억 건 이상의 일상대화 전용 대화세트들에 있습니다. 일상대화 API는 이 대화세트들과 심심이팀의 대화처리엔진 AICR를 활용해서 당신의 챗봇이 사용자들에게 웃음과 힐링을 제공할 수 있도록 돕습니다.

## 작동원리
각 대화세트(`talkset`)는 질문문장(`qtext`)과 답변문장(`atext`)의 쌍으로 이루어집니다.

<img src="https://workshop.simsimi.com/static/img/smalltalk_diagram_01.png" width="300px" alt="대화세트 개념도">

심심이 대화처리엔진(AICR)은 수많은 대화세트들이 쌓여 있는 대화세트 저장소에서 적절한 응답을 찾는 작업을 합니다. 일상대화 API를 통해 요청이 접수되면 AICR은 대화세트 저장소에서 요청문장(`utext`)과 유사도 등의 관련성이 높은 질문문장(`qtext`)들을 찾아서 후보군을 만들고, 요청에 포함된 파라미터들과 다른 조건들을 고려하여 가장 적절한 하나의 대화세트를 선택합니다.

일상대화 API가 제공하는 답변문장(`atext`)은 이 과정에서 선택된 대화세트의 답변문장(`atext`)입니다. 예를 들어 요청의 `utext`가 "밥은 먹었어?"일 때 일상대화 API는 다음과 같은 과정을 거쳐 `atext`로 "응 먹었어"를 반환합니다.

<img src="https://workshop.simsimi.com/static/img/smalltalk_diagram_02.png" width="600px" alt="일상대화 API 개념도">

## 기본요청
일상대화 API 엔드포인트(`https://wsapi.simsimi.com/{VERSION}/talk`)를 향해 프로젝트키, 필수파라미터(`utext`, `lang`)를 명시하여 POST 요청하면 응답을 받을 수 있습니다.

#### 요청예시
``` bash
curl -X POST https://wsapi.simsimi.com/190410/talk \
     -H "Content-Type: application/json" \
     -H "x-api-key: PASTE_YOUR_PROJECT_KEY_HERE" \
     -d '{
            "utext": "안녕", 
            "lang": "ko" 
     }'                     
```
- `utext` : 사용자가 챗봇에 입력한 메시지
- `lang` : 사용자의 언어코드([일상대화 API가 지원하는 언어 및 언어코드](#지원언어-및-언어코드))

#### 응답예시
``` json
{
  "status":200,
  "statusMessage":"Ok",
  "atext":"뭐이눔아",
  "lang":"ko",
  "request":{
    "utext":"안녕",
    "lang":"ko"
    }
}    
```
- `atext` : 답변, 요청의 `utext`에 대해 AICR이 선택한 talkset 의 `atext` ([작동원리](#작동원리) 참조)
- `request` : 요청 본문
- `status`, `statusMessage` : 상태정보 ([상태코드표](#상태코드표) 참조)


## 지원언어 및 언어코드
대부분의 언어코드는 ISO-639-1과 동일하지만, 다른 사례(*)가 있으니 주의하세요.

|언어명	|	 언어명(네이티브)	|	 언어코드|
| --- | --- | --- |
|갈리시아어	|	 galego	|	 gl|
|구자라트어	|	 ગુજરાતી	|	 gu|
|그루지야어	|	 ქართული	|	 ka|
|그리스어	|	 Ελληνικά	|	 el|
|네덜란드어	|	 Nederlands	|	 nl|
|네팔어	|	 नेपाली	|	 ne|
|노르웨이어(보크몰)	|	 norsk	|	 nb|
|덴마크어	|	 Dansk	|	 da|
|독일어	|	 Deutsch	|	 de|
|라트비아어	|	 latviešu	|	 lv|
|러시아어	|	 русский	|	 ru|
|루마니아어	|	 Română	|	 ro|
|리투아니아어	|	 lietuvių	|	 lt|
|마라티어	|	 मराठी	|	 mr|
|마케도니아어	|	 македонски	|	 mk|
|말라얄람어	|	 മലയാളം	|	 ml|
|말레이어	|	 Melayu	|	 ms|
|몽골어	|	 Монгол	|	 mn|
|바스크어	|	 euskara	|	 eu|
|버마어	|	 မြန်မာဘာသာ	|	 my|
|베트남어	|	 Tiếng Việt	|	 vn*|
|벨로루시어	|	 беларуская	|	 be|
|벵골어	|	 বাংলা	|	 bn|
|보스니아어	|	 bosanski	|	 bs|
|불가리아어	|	 български	|	 bg|
|세르비아어	|	 српски	|	 rs*|
|세부아노	|	 Cebuano	|	 cx*|
|스와힐리어	|	 Kiswahili	|	 sw|
|스웨덴어	|	 svenska	|	 sv|
|스페인어	|	 español	|	 es|
|슬로바키아어	|	 slovenčina	|	 sk|
|슬로베니아어	|	 slovenščina	|	 sl|
|신할라어	|	 සිංහල	|	 si|
|아랍어	|	 العربية	|	 ar|
|아르메니아어	|	 հայերեն	|	 hy|
|아이슬란드어	|	 íslenska	|	 is|
|아제르바이잔어	|	 Azərbaycanca	|	 az|
|아프리칸스어	|	 Afrikaans	|	 af|
|알바니아어	|	 Shqip	|	 al*|
|에스토니아어	|	 eesti	|	 et|
|영어	|	 English	|	 en|
|우르두어	|	 Урду	|	 ur|
|우즈베크어	|	 O‘zbek	|	 uz|
|우크라이나어	|	 українська	|	 uk|
|웨일즈어	|	 Cymraeg	|	 cy|
|이탈리아어	|	 Italiano	|	 it|
|인도네시아어	|	 Bahasa Indonesia	|	 id|
|일본어	|	 日本語	|	 ja|
|중국어	|	 中文	|	 ch*|
|체코어	|	 čeština	|	 cs|
|카자흐어	|	 қазақ	|	 kk|
|카탈로니아어	|	 català	|	 ca|
|칸나다어	|	 ಕನ್ನಡ	|	 kn|
|캄보디아어	|	 ភាសាខ្មែរ	|	 kh*|
|쿠르드어	|	 Kurdî (Kurmancî)	|	 ku|
|크로아티아어	|	 hrvatski	|	 hr|
|타갈로그어	|	 Filipino	|	 ph*|
|타밀어	|	 தமிழ்	|	 ta|
|타직어	|	 Тоҷикӣ	|	 tg|
|태국어	|	 ภาษาไทย	|	 th|
|터키어	|	 Türkçe	|	 tr|
|텔루구어	|	 తెలుగు	|	 te|
|파슈토어	|	 پښتو	|	 ps|
|펀자브어	|	 ਪੰਜਾਬੀ	|	 pa|
|페르시아어	|	 فارسی	|	 fa|
|포르투갈어	|	 português	|	 pt|
|폴란드어	|	 polski	|	 pl|
|프랑스어	|	 Français	|	 fr|
|프리지아어	|	 Frysk	|	 fy|
|핀란드어	|	 suomi	|	 fi|
|한국어	|	 한국어	|	 ko|
|헝가리어	|	 magyar	|	 hu|
|히브리어	|	 עברית	|	 he|
|힌디어	|	 हिन्दी	|	 hi|
|아삼어	|	 অসমীয়া	|	 as|
|브르타뉴어	|	 Brezhoneg	|	 br|
|과라니어	|	 Guarani	|	 gn|
|자바어	|	 Basa Jawa	|	 jv|
|오리야어	|	 ଓଡ଼ିଆ	|	 or|
|키냐르완다어	|	 Ikinyarwanda	|	 rw|
|중국어 (번체)	|	 繁體中文	|	 zh*|

## 상태코드표

|`status` | `statusMessage` | 설명 | 
| --- | --- | --- |
|200 | 	OK | 정상 |
|227 | 	Parameter Required | 필수 파라미터 누락 |
|228 |	Do Not Understand | 질문에 대한 답변을 찾을 수 없음 |
|403 |	Unauthorized | 유효하지 않은 API Key |
|429 |	Limit Exceeded | 사용 한도 초과 |
|500 |	Server error | 서버 오류 |


TBD
