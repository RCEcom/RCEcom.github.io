# WinAPI_tutorial
>###### [*]이 글은 WinAPI를 제가 공부한걸 적은것입니다.
![image](https://user-images.githubusercontent.com/87273590/152352768-fb2150f2-494b-4548-9aef-b33c4cb065fa.png)
### 처음 프로젝트를 만드시면 위와 같이 Main이 보이고, 여러 인자들이 있습니다. 어떻게 보면 현재 저희는 윈도우에서 돌아가는 프로그램을 만드는 것입니다.
### 이 저희가 윈도우에서 돌아갈 프로세스를 만든다는 것은, 결국 "운영체제" 위에서 동작한다는걸 의미하고
### 컴퓨터를 키면 메모리를 가장 많이 점유하는게 바로 'os'입니다. 하나의 프로그램이자 모든걸 장악하고 있죠.
### 아무튼 main'함수'에서 여러 인자가 들어오면서 시작을 하게 됩니다. 근데 프로젝트를 만들기만 했는데도 많은 코드가 저희에게 주어졌습니다.
### 이렇게 기본 동작 코드가 있다는건 '기본적인 설계 원칙' 있다고 볼 수 있지 않을까요?
### 한번 '코드들'을 둘러보며 어떠한 문법을 사용하고 있는지, 대충 실감을 해보시길 바랍니다. 마치 학교에서 수업 시간 5분전에 오늘 배울 단원을 훓어보는 것처럼 말입니다.
### 하지만 역시나 모르는게 있을수도 있기 떄문에 같이 보도록 하겠습니다.
### ![image](https://user-images.githubusercontent.com/87273590/152355163-04420a7b-7a53-4edd-a04a-943369a9cc2f.png)
### Main코드 바로 밑에 위 처럼 이상한 함수가 있습니다.
### ![image](https://user-images.githubusercontent.com/87273590/152355257-91ebefba-2beb-451a-9333-d84760ca43eb.png)
### 원형은 이것이며, define은 치환하는 문법입니다. 어떠한 인자값을 넣어주면 그걸 그냥 define으로 치환해 준다는 것이죠.
### 한 마디로 그냥 아무런 의미가 없이 변수를 그냥 적어놓은것이라고 보면 됩니다.
### 컴파일러는 이를 인식하지 않고 그냥 넘어가기에 충분히 '주석'(으)로도 채울 수 있는데 굳이 이렇게 하나 봅니다.
### 그럼 여기서 말하고자 하는게 무엇인가? 바로 문자열 자체가 의미있는 겁니다. 잘 읽어보면 "이건 참조되지 않는 변수입니다." 라고 쓰여져 있네요.
### ![image](https://user-images.githubusercontent.com/87273590/152355898-d493c12e-5c99-40ad-898e-583a22839301.png)
### 위 코드처럼, 앞에 _IN_, _IN_OPT는 무엇일까? 바로 용도를 설명해주기 위한것인데, 이걸 SAL(이)라고 부릅니다.
### 간추리자면 이것도 코드를 설명하는 하나의 '주석'역할입니다. _IN_은 "이 인자 변수는 입력한다"라는 의미를 함축해 놓은것입니다.
### _IN_OPT_ 이것은 "딱히 필요없지만 부가적으로 들어올 순 있다"라는 뜻입니다.
### 이런식으로 각각 키워드를 통해 짧고 굵게 사용자에게 전달할 수 있는 겁니다.
### 더 많은 의미들에 정보는 link를 달아두겠습니다.
### SAL : https://docs.microsoft.com/ko-kr/cpp/code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects?view=msvc-170
### ![image](https://user-images.githubusercontent.com/87273590/152357115-4f22f350-e073-44e3-a30e-a3c432ed1b2f.png)
### 이제 그럼 이 2개의 인자가 뭘 하는지 알아볼건데요.
### hInstance(은)는 실행된 프로세스의 시작 주소를 담고 있습니다.
### 어쨌든, 이 프로그램도 메모리에 올라가게 됩니다.
### 그럼 자동으로 hPrevInstance(은)는 나보다 실행되기 전, 이전의 시작 주소가 아닐까요?
### 즉, 윈도우에 "그림판"도 하나의 프로그램입니다. 여러개 실행시킬수도 있죠.
### 하지만 이 hPrevInstance(인자)는 윈도우 초창기때 사용했던 방식입니다. 지금은 이렇게 동작하지 않습니다.(과거의 잔재 같은 느낌)
### 그럼 현재는 어떨까요? 아무리 제가 여러개를 실행해도 hInstance(은)는 같은 값이 나옵니다.
### 근데 이건 정말 말이 이상하지 않나요? 이 말은
### int a;
### int b;
### int c;
### (을)를 선언했을 떄 메모리 주소가 같다는 거 아니에요?, 분명히 말이 안되는 소리겠죠
### 근데 왜 이러한게 가능했는가? 바로 "가상 메모리 시스템"을 쓰기 때문입니다.
### 분명 내가 프로그램을 여러개 만들었지만, 사실상 다른 메모리 공간에 있었고 따로 가상 메모리 주소를 만들어서
### 사용자에게 보여줍니다. 
### 예를 들자면
### ![image](https://user-images.githubusercontent.com/87273590/152359175-2287c68f-f119-4245-9f91-0ce462120e88.png)
### 분명 무인도가 여러개인데, '나' 자신 한테는 여기가 하나의 세계인 마냥 보는것입니다.
### 그래서 hInstance(인자)에 각 프로세스마다 동일한 주소가 들어왔다는 것은
### 자기만의 가상 메모리 공간에서의 지칭을 하는 말입니다. 
### 그래서 오해하면 안되는게 똑같은 프로세스를 2개 실행시킨 뒤 "주소를 반환시키면" 똑같이 나올겁니다.
### "? 메모리가 겹쳐져서 실행되는건가?"(이)가 아닙니다.
### 그러므로 hPrevInstance는 현재 가상 메모리 시스템 도입 후, 아무런 쓸모가 없어진겁니다.
### ![image](https://user-images.githubusercontent.com/87273590/152360150-ed027dd4-3a82-4e08-be69-058e59d9decc.png)
### lpCmdLine(은)는 추가적으로 프로그램을 실행하기 전, 문자열을 인자로 주고 싶을 때 
### 이(lpCmdLine) 자리에 넣으시면 됩니다.
### 이건 이제 어떨떄 쓰이냐면 ![image](https://user-images.githubusercontent.com/87273590/152360464-c54b4b4d-6742-454a-a83d-587beb3bd5dc.png)
### 이런식으로 cmd에게 명령어를 내릴 떄 옵션(-e)같은것을 줬을 겁니다. 이떄 사용합니다.
### LPWSTR(은)는 문자열 포인터 타입입니다.
### ![image](https://user-images.githubusercontent.com/87273590/152361074-5f99975b-f24a-4c5b-bce9-e48baa5ac31c.png)
### 즉, wchar_t*인데 타입을 재정의 한거라고 보시면 되겠습니다. win api만드신 분은 이런식으로 재정의 하는걸 좋아합니다.
### ![image](https://user-images.githubusercontent.com/87273590/152362605-1b3ed758-354d-44c0-94f9-39397d4f8b44.png)
### 위 함수는 무엇을 하는 것일까요. 이제 프로그램을 시작하기 전에 사용할 자원 목록이
### ![image](https://user-images.githubusercontent.com/87273590/152363054-dcc0623c-a545-4cdf-8c77-8b3b7487bce2.png)
### 리소스 뷰에 있는데요. 여기서 저희는 string table에 들어갈겁니다
### ![image](https://user-images.githubusercontent.com/87273590/152363138-ef7353a9-4cf9-4eb7-9742-f9c846c84c6e.png)
### 보시다시피 저희가 처음에 프로젝트를 만들때 적어놓은 프로젝트 이름이 있는걸 보실 수 있습니다.
### id값은 2개이며 [소문자, 대문자]로 나누고 있고 전처리기를 사용해서 치환하고 있네요
### 리소스 헤더 파일에 가보시면
### ![image](https://user-images.githubusercontent.com/87273590/152363438-38b5678e-41cb-4ed2-8b0d-e43c1e764fb9.png)
### 실제로 전처리 하고 있는 코드가 보입니다. 103, 109 보이시죠
### ![image](https://user-images.githubusercontent.com/87273590/152363512-0ef672f7-b93d-44fc-865a-b1257ded58c9.png)
### 즉, 해당 함수는 전처리기에 등록된 문자열을 szTitle, szWindowClass배열에 저장을 하겠다. 라는 뜻이 됩니다.
### 원한다면 저희도 등록할 수 있겠습니다.
### 그럼 이걸 왜 하고 있냐면
### ![image](https://user-images.githubusercontent.com/87273590/152363863-285e05fd-3289-4ad3-bdd4-d49491380df9.png)
### 바로 기본형태가 바로 아 '윈도우 창'이기 떄문입니다. 위에 프로젝트 이름이 있는 이유가 string table에 등록하고 따로 배열에다가 저장해주는 loadstring함수를 썼기 떄문입니다.
### 근데 이 프로그램 이름을 "프로젝트 명"(으)로 하기 싫습니다.
### ![image](https://user-images.githubusercontent.com/87273590/152364243-0641046e-816f-4558-a8ae-d90c38bb11b3.png)
### 윈도우창을 만들 떄, 아까 저장한 szTitle(을)를 인자로 넣어서 쓰고 있지만, 저희가 원하는 값으로 바꾼다면 바뀔 수 있겠죠
### ![image](https://user-images.githubusercontent.com/87273590/152364393-0c558c02-903d-4e07-8b2b-d2ef96c8699e.png)
### ![image](https://user-images.githubusercontent.com/87273590/152364438-53dffb2c-ab93-4d17-9beb-ed9c0748c06a.png)
### 비쥬얼 스튜디오는 처음에 뭘로 title명(으)로 할지 모르기 떄문에 프로젝트 명(으)로 해놨던 것입니다. 사실상 이것도 무의미한 코드죠.
### 여러분 어떤가요? 막 복잡해 보였는데, 막상 코드를 까보고 분석해 보니 무의미한 코드들이 많았습니다.
### ![image](https://user-images.githubusercontent.com/87273590/152365680-9342c4a8-a2c8-4f5e-90c7-4bc25b83526a.png)
### 이 함수는 여러 윈도우 정보들을 세팅합니다.
### 그리고 최종적으로 윈도우를 만드는 로직은
### ![image](https://user-images.githubusercontent.com/87273590/152369087-5ba73ed0-461d-4429-9781-6ca9ca074034.png)
### 여기라고 볼 수 있겠습니다.
### ![image](https://user-images.githubusercontent.com/87273590/152369708-edeecddb-6f87-4394-bc82-2a3c130831b0.png)
### 레지스터 클래스 함수쪽에서 위와 같이 설정한것을
### ![image](https://user-images.githubusercontent.com/87273590/152370131-96bf2f02-f4a2-4142-a074-5a47b7fc9674.png)
### 제 마음대로 바꿀수도 있겠죠.
### ![image](https://user-images.githubusercontent.com/87273590/152370193-3269ff47-e805-4eee-853c-1a7d2e1b307b.png)
### 이것도 마찬가지로, 비쥬얼 슈튜디오 측에서 class name할게 없으니까 프로젝트 명(으)로 해놓은것입니다.
### ![image](https://user-images.githubusercontent.com/87273590/152370554-e95fa1a7-ab5f-410b-959a-9f7bc2bdd7d8.png)
### 기본적인 윈도우 창이 생기지 않는다면 종료하겠다는 의미입니다. 실제로 해당 함수 호출할 떄 이상이 생긴다면 return false를 하게 됩니다.
### !(역반전)이 일어나면 true가 되면서 프로그램이 종료되게 됩니다.
### ![image](https://user-images.githubusercontent.com/87273590/152578261-dbf6609b-c3ed-46b1-b2c7-0db65bc992da.png)
### 이제 그 밑에 위와 같은 코드들이 있을실텐데요. 이것은 "단축키"를 설정하고 검증하는 로직입니다.
### 실제로 string_table처럼, 이 역시 단축키 table(을)를 저장하고 있는 곳이 있습니다.
### ![image](https://user-images.githubusercontent.com/87273590/152578598-c918018a-dc3e-4143-b8a9-a61986181443.png)
### ![image](https://user-images.githubusercontent.com/87273590/152578610-d687f8cc-437c-4f48-bea2-37235972a2c8.png)
### 이렇게 단축키값들이 등록되어 있습니다.
### ![image](https://user-images.githubusercontent.com/87273590/152578704-0223507a-56cd-467a-910d-e9b35b850658.png)
### 그리고 여기서 단축키가 눌렸는지, 안눌렸는지 확인하죠
### 프로그램 실행 후 아까 봤던 단축키 Alt + ?를 동시에 누르면.
### ![image](https://user-images.githubusercontent.com/87273590/152578779-223e079e-4272-42c9-b94f-778d38c8bc87.png)
### 이 처럼, 아까 등록된 단축키로 인하여 상호작용이 가능합니다.
### 이에 관해서는 나중에 더 깊게 들어갈 것이기 떄문에, 그냥 일단 "단축키가 등록된 곳을 변수에 담고 단축키가 눌러졌는지 체크하는 로직이다." 라고만 이해해도 괜찮습니다.
### 그럼 GetMessage함수는 뭘까요?
### ![image](https://user-images.githubusercontent.com/87273590/152579795-9a3027fc-1b08-46b6-a415-54e20a47786f.png)
### ![image](https://user-images.githubusercontent.com/87273590/152579878-e53429f2-b70d-47c5-88cf-036fcca66635.png)
### 여기 os위에 돌아가는 프로세스 '하나'가 있습니다.
### os에서는 [마우스 클릭, 키보드 입력, 등등...]여러가지 메시지들이 '큐'에 담겨 있습니다.
### ![image](https://user-images.githubusercontent.com/87273590/152580007-48872210-8564-49b3-a2c5-b71b7c8f237c.png)
### 그럼, os는 현재 '포커싱'된 프로세스한테 메시지를 보내봅니다.
### ![image](https://user-images.githubusercontent.com/87273590/152580075-3c955326-e260-4e87-8022-ec47a197b6fc.png)
### 프로세스는 해당 메시지를 받고, 어떤 일을 수행하게 됩니다. 만약 마우스 클릭 메시지를 받았다면. 그림판을 기준으로 봤을 떄 
### 점을 찍을겁니다.
### 즉, Getmessage함수는 os(으)로부터 받은 메시지가 있는지 반복문(while)(으)로 수시로 확인합니다.
### 혹시나 유저로부터 온 이벤트가 있는지.
### ![image](https://user-images.githubusercontent.com/87273590/152580329-3baffb05-a38e-4915-a98d-54009c1faf9b.png)
### 또한 메시지를 받기 위해, 메시지 받는 전용 구조체로 선언한 변수 주소값을 넘겨줍니다.
### why? : 발생한 정보를 채우기 위해.
### ![image](https://user-images.githubusercontent.com/87273590/152581383-f6e55ead-87ed-463f-8473-be30e51a06fa.png)
### hwnd는 (핸들)이라고 불리며, window입니다.
### 하나의 프로세스 안에서 '창'(을)를 여러개 만들수도 있어요.
### 즉, 구체적으로 발생한 'window'(이)가 누군지까지 알수 있도록 모든 정보가 msg에 있습니다.
### 그럼 그걸 각 윈도우마다 처리해주는게 누구일까?
### 바로 따로 각자 소유하고 있는 함수가 처리합니다. 이걸 "프로시저 함수" '처리기'라고 합니다.
### ![image](https://user-images.githubusercontent.com/87273590/152581832-e1ac6ebb-8cbc-4c50-b602-c1e7193618c5.png)
### 이 기본적인 윈도우에 대해 정보를 등록하는 함수안에서, 각 윈도우마다 처리할 프로시저가 이미 등록되어 있었습니다.
### ![image](https://user-images.githubusercontent.com/87273590/152582039-60d7c8fb-4246-4883-af6b-07c402b2da75.png)
### 자 그래서, 이 메시지값을 꺼냈는데 메시지가 발생한 윈도우가 현재 '창' Main_window입니다.
### ![image](https://user-images.githubusercontent.com/87273590/152582182-34f80f40-52cc-43f6-bcaf-4ee8a65923ea.png)
### 그럴경우 해당 윈도우쪽에 "프로시저를 호출해라." 라고 함수를 호출하게 됩니다.
### "너한테 온 메시지야. 너가 처리해" 이런것이죠
### ![image](https://user-images.githubusercontent.com/87273590/152582303-91289235-78c8-4617-ab13-86c9c30c0fff.png)
### 해당 프로시저 함수에서는 메시지가 어떤것인지 switch문(으)로 확인한 뒤 역할을 수행합니다.
### ![image](https://user-images.githubusercontent.com/87273590/152582405-558e539c-11a4-4f4d-b3ee-d50e173e64d7.png)
### 하지만 윈도우에서 제공하는 메시지는 종류가 수십개가 되기 떄문에, 따로 원하는 메시지가 아닐경우 흘러 보냅니다.
### 자 그럼 Getmessage가 반복문을 종료시킬 조건은 무엇인가? 바로 메시지 값에 대해 달라질 거 같은데요.
### 맞습니다. 실제로 WM_QUIT일 경우, 반복문을 탈출합니다. false를 반환한다는 것이죠.
### WM_QUIT가 존재한다는건 이미 프로그램의 기능이 모두 완료가 되었고 끝낼 준비가 되어 있다는것도 알 수 있습니다.
### 근데 이 구조자체가 어떠한 메시지가 무조건 있어야 프로그램이 돌아간다는 겁니다. getmessage로 메시지르 얻어오는데, message가 없다면 허구한날 주구장창 메시지 오기만 기다리는겁니다
### 그래서 현재 구조는 "게임 클라이언트"(으)로 사용하기에는 부합당 하다는 겁니다. 이 방식(메시지 큐)으로도 게임을 만들 수 있긴 한데
### 왜 (메시지 큐 구조)가 비휼적인가? 그리고 이 구조(메시지 큐)를 바꿔볼것입니다.
### 그 전에, 일단 한번 이 구조로 한번 만들어보고 천천히 바꿔봅시다.
### 그럴려면 VM_PAINT가 도대체 어떤 경우에 메시지가 날라오는가?
### 바로 '무효화 영역'이 발생했을 때인데요. 바로 특정 프로그램에 의해 일정 부분이 가려진다거나, 창을 내렸다가 올렸을 떄
### 무효화 영역이 되었다고 판단합니다. 하지만 윈도우 버전이 업데이트가 되면서 "특정 부분이"가려진다고 해서 무효화 영역이 발생하지 않습니다.
### 이제 OS에서는 윈도우 창을 만들어주는 함수를 제공해 주고 있는데, 그렇게 만들어진 윈도우 객체는 함부로 접근할 수 없습니다. 이것을 '커널 객체'라고 하며
### 특정 권한을 얻어야만 이 윈도우를 저희가 제어할 수 있습니다. 이 권한은 OS가 역시나 주며, '핸들값' 즉, ID값을 줍니다.
### ![image](https://user-images.githubusercontent.com/87273590/153417556-101b7dea-dade-4183-ad0f-ecc64adbe3cb.png)
### 그래서  이렇게 D.C라는 객체 아이디값. 그릴 수 있는 권한에 대한 핸들값을 얻어온겁니다.
###![image](https://user-images.githubusercontent.com/87273590/153417665-d7a48572-86cb-46bb-9e62-d7cd5f620368.png)
### 이 가져온 핸들값을 사용하여 여러가지 제공하는 함수를 쓸 수 있는것이죠
### ![image](https://user-images.githubusercontent.com/87273590/153417833-0eda9226-3c39-4dfd-94eb-0244724cd1ac.png)
### 그리고 이 특정 객체에 대한 핸들값에 대한 구조체는 많습니다. 이름만 다르고, 그냥 int형을 받을 수 있는 구조체 입니다.
### 그럼 이렇게 많은 이유가 뭘까요? 바로 받으려는 객체 핸들값 종류가 굉장히 많기 떄문입니다.
### ![image](https://user-images.githubusercontent.com/87273590/153418147-5815034b-9ed2-4349-8f15-48e97c51257c.png)
### 윈도우에 그림을 그릴 수 있는 펜 and 부러쉬 등등
### 한 가지로 정의하기에는 그렇다는 거죠. 또한 특정 함수는 HDC핸들값을 원했지만 저희가 잘못주었을 떄 빠르게 인지도 가능하구요
### ![image](https://user-images.githubusercontent.com/87273590/153418484-9ba7ceb2-9875-4446-9210-b0c9a2bcfa96.png)
### 윈도우 자체 핸들을 처음으로 인자를 통해 받아서, Device context 객체 ID값을 만들어 냅니다.
### 이 윈도우에서만 또 D.C가 작동하는 이유도 처음 
### ![image](https://user-images.githubusercontent.com/87273590/153418869-29758545-619b-4440-80dc-f4db3bfb0a90.png)
### Wproc에서 이미 윈도우 자체에 대한 핸들값을 가지고 있기 떄문에, 특정 윈도우을 선택할 수 있는겁니다.
### 윈도우가 여러개가 있더라도, 윈도우 하나가 가지고 있는 고유의 ID값 떄문에 구분이 가능합니다.
### 그럼 저희는
### ![image](https://user-images.githubusercontent.com/87273590/153419202-4861ae0c-af04-48d0-a59c-c03f5531a3de.png)
### 이제 이 코드가 뭘 하고 있는지 알 수 있습니다. BeginPaint함수로 특정 윈도우에 대한 D.C(그릴 수 있는 권한)을 저장할 수 있는 핸들 구조체에다가 (iD)값을 저장하겠다.
### 그럼 D.C는 무엇인가? 바로 종합적으로 그림에 대해서 관리합니다. 그리고 그리는 목적지를 알려주는데요. 저희가 그릴곳을 정한다는 겁니다. 여기서는 넘겨준 핸들값이 윈도우겠죠
### 저희가 본격적으로 움직이는 사각형을 만들기 전에, 픽셀과 RGB를 어떻게 표현할까?를 좀 알아봐야 합니다.
### 픽셀 하나는 RGB를 가지고 있으므로 총 3byte입니다. ![image](https://user-images.githubusercontent.com/87273590/153420209-40a9dc25-2921-4015-a8d5-562901c1d770.png)
### 1byte마다 0~255까지 표현할 수 있습니다.
### ![image](https://user-images.githubusercontent.com/87273590/153420312-02b17351-8f2d-4820-b1ad-a5b4653b1ca7.png)
### 아까전에 그릴 수 있는 종이(D.C)를 준비했다면 이제 그릴 수 있는 "Pen(펜)"을 준비해야 합니다.
### 첫번째 인자는 펜의 종류 이며 MS_Docs에서 더 많은걸 찾아보실 수 있습니다. 두번째 인자는 두께 이고요. 세번째 인자는 색상입니다.
### RGB에 저장하는 방법은 ![image](https://user-images.githubusercontent.com/87273590/153420555-50f0e118-8b40-44a8-bece-58c9e41bcdbe.png)
### 이렇게 비트쉬프트를 통해 하는데요.
### ![image](https://user-images.githubusercontent.com/87273590/153420697-4bfd0bac-ec40-4db7-bb85-af085089c9f0.png)
### 충분히 이해하실 수 있을거라고 생각합니다.
### ![image](https://user-images.githubusercontent.com/87273590/153420782-af642025-e088-4886-896f-66616f885430.png)
### 이제 펜을 만들었으니 선택을 하도록 해야 합니다. 그냥 저희는 펜을 만든것일 뿐이고 제가 쓸지 안쓸지는 모르는거잖아요?. 그래서 펜을 골라주는 작업을 하고요.
### ![image](https://user-images.githubusercontent.com/87273590/153420925-0bd21c12-ca45-43e2-9ec1-8f3ee16a3c2c.png)
### 마지막 끝나기 전에는, 펜 객체를 삭제시켜줍니다.
### ![image](https://user-images.githubusercontent.com/87273590/153421064-015fdee1-d39a-4b3a-956b-2d859ca8edb7.png)
### 이렇게 브러쉬까지 만들어주고, 선택까지. 해줍니다. 중간에 사각형 그리는 함수에서 좌표값을 막 계산하는데 조금있다가 보게 될겁니다. 지금은 그냥 넘기셔도 됩니다.
### 자 그럼 이제 그리는것까지는 준비했는데, 이 그린것을 움직여야 하잖아요? 키보드 입력을 받아야 겠죠
### 키보드 입력도 메시지가 있습니다.
### ![image](https://user-images.githubusercontent.com/87273590/153421245-2d299e29-6665-4287-8e7c-e4bd24e035ec.png)
### 이렇게 메시지로 키보드가 눌렸는지 안눌렸는지 판단하도록 하죠
### ![image](https://user-images.githubusercontent.com/87273590/153421293-543a3d32-d803-45bf-990f-f514e04df88a.png)
### 그럼 키가 눌렸는데 그 키보드 값도 또 받아야 겠죠
### ![image](https://user-images.githubusercontent.com/87273590/153421354-8ab6ea4b-bd3a-4ac4-8da5-c7611fb19d47.png)
### 이 파라미터는 이미 저희가 WndProc에서 부가적으로 받습니다. 만약 키보드 값을 입력했다면 WndProc에서 해당 파라미터를 가져오겠죠
### ![image](https://user-images.githubusercontent.com/87273590/153421461-e5162dcb-fefd-4fbb-a785-aceaa44e364d.png)
### 만약 마우스 관련 메시지였다면 마우스 입력에 대한 파라미터값을 가져옵니다.
### ![image](https://user-images.githubusercontent.com/87273590/153421583-61aea697-7773-4e88-9ecd-918a21373ec9.png)
### 이제 해당 메시지는 좌클릭을 눌렀을떄 발생되는 이벤트인데, LOWORD, HIWORD 모두 매크로이며 역시 비트값으로 값을 등록합니다.
### 그냥 이건 알아만 두시면 되고요
### ![image](https://user-images.githubusercontent.com/87273590/153421753-7dc69839-455e-469d-acf5-151c8f4d469e.png)
### 이제 저희는 키 눌림에 대한 이벤트를 인식했다면 그 키값에 대해서도 인식을 해야 돼요,
### ![image](https://user-images.githubusercontent.com/87273590/153421834-e41dd892-0d63-4953-9d7e-c870860dc1e5.png)
### 수 많은것중에 방향키 위에 있는게 눌려졌다면,,으로 가겠습니다.
### 자 근데, 이 아무리 방향키를 눌러도 사각형의 좌표가 이동하지 않는다면 별 의미가 없겠죠
### 그래서 좌표가 바뀌도록 상수값이 아닌 변수로 선언을 해야합니다
### 이 좌표값을 선언하도록 도와주는 구조체가 또 있어요. 바로 "POINT"인데
### ![image](https://user-images.githubusercontent.com/87273590/153422134-ef294b14-f78d-4649-93d0-ccebdceef086.png)
### 2개 정의해줍니다.
### ![image](https://user-images.githubusercontent.com/87273590/153422175-d8010944-d7a1-43df-8906-cd5cf0b19749.png)
### ![image](https://user-images.githubusercontent.com/87273590/153422280-9bdb6fad-9bab-4edd-9a5c-5e82955b6bbe.png)
### 좌상단 좌표값을 구하기 위한 식을 그대로 옮긴겁니다.
### ![image](https://user-images.githubusercontent.com/87273590/153422398-c3d110fc-8b61-44fb-b459-86bc8bc5a2e6.png)
### 우하단도 마찬가지로요. 우하단은 더해야 겠죠? 좌표값에다가, 좌상단은 빼야 하구요
### 이 /2를 하는 이유도 해당 사각형에 대한 중심으로 기준을 잡을려고 했기 떄문입니다.
### ![image](https://user-images.githubusercontent.com/87273590/153422545-1dc767b3-894f-447a-a49a-8e7545e766de.png)
### 본격적으로, 좌표를 빼보고 실행하면?
### 아마 안움직일 것이고 창을 내렸다 올리면 이동할것입니다. 이게 왜냐하면 무효화 영역이 있을떄만 현재 그림을 그리기 떄문입니다.
### ![image](https://user-images.githubusercontent.com/87273590/153422823-40048770-3311-4934-90cd-77107e088aaa.png)
### VM_PAINT가 그런 특성이구요.
### ![image](https://user-images.githubusercontent.com/87273590/153422889-5da28c10-68e5-44d4-ad7f-6df413f282bc.png)
### 이 함수를 사용하여 강제로 무효화 영역이 생기도록 합니다.
### 그럼 계속 그리면서, 횐색 픽셀로 바꿉니다.
### ![image](https://user-images.githubusercontent.com/87273590/153423236-b41c0c33-adc4-498c-be3f-b9f989eb8aea.png)
### 좌-우-상-하 움직이게 하도록 추가해 줍니다.
### 이제 그럼, 사각형을 움직일 수 있습니다.
### 만약 이 사각형이 하나가 아니라 여러개라면, 어떨까?
### 100개가 있다면, 매일 매일 정의해야 해줘야 합니다. 편하도록 바꿔줍시다.
### ![image](https://user-images.githubusercontent.com/87273590/153426357-f1f75d55-2790-471b-9de0-6299ef203682.png)
### 잠시만 한번 아까 배웠던걸 응용해 볼까요?
### 스타크래프트에서 용병을 선택할 떄 그 드레그를 구현해 봅시다.
### ![image](https://user-images.githubusercontent.com/87273590/153427859-13c9b5e0-85d0-4438-88fe-49669d045da8.png)
### ![image](https://user-images.githubusercontent.com/87273590/153427914-daee0e31-b1ed-4f67-94d3-12535b852600.png)
### 최상단 좌표는, 왼쪽 마우스 좌표값을 기준으로 잡고 마우스무브 메시지를 통해 최상단 좌표기준으로 최하단 좌표값을 유지한채 계속 그립니다.
### 넓이만 커지고, 최상단 좌표는 그대로 있게 그립니다.
### ![image](https://user-images.githubusercontent.com/87273590/153428385-f5e2c6cb-96fb-4351-a0e3-775794ba38ce.png)
### 이제 이 프로그램을 실행하면 드레그를 구현한것입니다.
### ![image](https://user-images.githubusercontent.com/87273590/153428720-982cae22-50dd-45fb-8514-d80985dbfa6d.png)
### 자 그럼 이걸 사용해서  좌클릭을 다시 한번 눌렀을 떄 사각형을 그리도록 할거에요. 마치 그림판에 있는 사각형 그리는 틀 처럼 말이죠
### 마우스로 그린 것을, 사각형으로 그리게 하려면 역시나 좌표값을 얻어야 합니다.
### ![image](https://user-images.githubusercontent.com/87273590/153431685-61d57482-9444-4246-b919-ba7c57297b94.png)
### 마우스 좌클릭이 떼어졌을 떄 물체를 만들것이기 떄문에, 해당 메시지를 쓰고요
### ![image](https://user-images.githubusercontent.com/87273590/153431825-099623d3-ace0-4a18-9f9d-f71235bdcbfb.png)
### 사각형의 중심 좌표를 구하는 것이고
### ![image](https://user-images.githubusercontent.com/87273590/153431876-8ed2af0c-c608-4fcb-a818-96e9badd2460.png)
### 사각형 넓이를 구하기 위한 값입니다.
### 해당 수식은 생각만 하시면 충분히 이해하실 수 있습니다.
### 그리고 만든 사각형을 어디에 담아놔야 되지 않을까요?
### ![image](https://user-images.githubusercontent.com/87273590/153432153-77748d27-6b18-4fe3-99ba-9c9fb70a95cb.png)
### vector 자료형으로 담을겁니다.
### ![image](https://user-images.githubusercontent.com/87273590/153432611-ced69727-3043-41b3-97b7-5942f1fcb39e.png)
### 자 근데, 한 가지 수정해야 할게 있습니다.
### ![image](https://user-images.githubusercontent.com/87273590/153432681-ddfdd148-630d-4653-ad54-241a5ca89bea.png)
### 저희가 마우스를 움직인다면 계속해서 사각형이 생겨져 있으므로
### 마우스 좌클릭을 눌렀을떄 해당 사각형 그리는 틀이 생기게 하고, 다시 좌클릭을 뗐을 떄는 사각형 틀이 생기지 않게 하도록 bool값으로 트리거 해줍시다.
### ![image](https://user-images.githubusercontent.com/87273590/153433296-6b8f5d88-2a55-4d81-ba3b-62faec9586b7.png)
### ![image](https://user-images.githubusercontent.com/87273590/153433335-d62d7659-77dc-4e38-9ee6-16f701cbe7d1.png)
>### true/fales 되는 부분 잘 확인해 주세요.
###  ![image](https://user-images.githubusercontent.com/87273590/153433384-f4a2c43b-51a3-4e5f-af45-14207ebce4ee.png)
### 자 이렇게 하신다면, 이제 마우스를 눌렀을떄만 해당 사각형 틀이 나오실겁니다.
###![image](https://user-images.githubusercontent.com/87273590/153433785-45f8a03a-baf2-474c-b6c0-a77b063ac8c6.png)
### 하지만 저희가 마지막에 이 사각형을 지워주지 않았기 떄문에 마우스를 움직이지 않고 가만히 있으면 이렇게 삭제되지 않고 가만히 잔재가 남습니다
### 그래서 강제 무효화 영역을 활성화 시켜서 지워줍시다.
### ![image](https://user-images.githubusercontent.com/87273590/153433933-dbf3d859-8939-4df9-8537-eb755f062961.png)
### ![image](https://user-images.githubusercontent.com/87273590/153434656-a3ff4918-5f87-4ce2-9135-318a8c475b71.png)
### vector에 있는 값만큼 그려줍니다.
### ![image](https://user-images.githubusercontent.com/87273590/153434765-24a5c8c3-c48e-4935-96c1-bd8e23cc4e0c.png)
### 잘 그려집니다.
### 근데 그림을 그릴수록 깜빡임이 심해집니다.
### 이게 PC사양이 낮아서 그런걸까요?
### 바로 이건 그리는 과정까지 저희에게 보였기 때문인데요. 60프레임씩 찍힐 떄 저희는 현재 vector 안에 있는 값을 계속해서 그리므로
### 해당 과정이 나올수밖에 없습니다. 어쩌다가 저희에게 그 그리는 과정 프레임이 동체시력으로 인지를 한것이죠
### 이를 해결하기 위해 이 윈도우창에 그려진 픽셀데이터를 하나 더 만들겁니다. 그리고 이 하나는 그리는과정 없이 결과만을 보여줄것입니다.
### 그러면 깜박임이 전혀 엾겠죠
### 메시지 기반에서 이를 구현하려면 Timer함수를 쓰면 되긴 하는데,,특정 시간마다 저희가 원하는 기능을 수행하게 해줍니다.
### 그러므로 드디어 메시지 기반말고, 게임 개발에 순조로운 구조로 바꿀겁니다.
### 일단, 저희 프로그램이 특정 메시지가 왔을떄만 동작하는 구조인 이유가 바로 Getmessage때문입니다.
### 그래서 이 구조를 바꾸기 위한, Peekmessage를 도입할것입니다. 이 함수는 '메시지 유무와 관계없이 결과를 반환'합니다.
### 해당 함수는 인자를 하나 더 받는데, 그래도 일단 큐에 있는 값을 확인해야 하니까 그것을 확인하도록 설정해주는 인자가 있습니다.
### ![image](https://user-images.githubusercontent.com/87273590/153608371-606f1cd6-4d25-41e6-b1a5-b50205738e08.png)
### 근데 메시지 유무와 상관없이 반환하면은 while문에 대한 조건문으로 있을 수 있을까요?
### ![image](https://user-images.githubusercontent.com/87273590/153608779-795c390d-bbd3-4031-b58e-9cab7519f5b8.png)
### 안되겠죠. 그러므로 위와 같이 변경해 주어야 합니다. 음? 근데 이러면 Getmessage랑 무슨 차이인가?
### ![image](https://user-images.githubusercontent.com/87273590/153608860-9a90cf6a-6028-44e4-bf0c-c45cab3055f1.png)
### else을 사용하여, 메시지가 없는 동안에 제가 원하는 일을 수행시킬 수 있습니다. 이게 Getmessage와 다른점이라고 볼 수 있겠습니다.
### else에다가는 주로 비동기 함수를 사용합니다. 윈도우에 마우스가 눌리면 메시지가 오는게 아니라, 그냥 백그라운드 자체에서 처리하기 떄문에 아무데다가 마우스(을)를 누른다면.
### 그걸 인지할 수 있다는거죠. 즉, 메시지 루틴을 얻는게 아닙니다.
### 만약 비동기로 그림판을 구현한다면 바탕화면에다가 그리고 있는데, 윈도우에도 똑같이 그려지는거랑 마찬가지죠
### 반대로 프로그램 자체가 화면이 안띄워지고 백그라운드에서만 실행돼야 했을떄 메시지 기반으로 만들면 굉장히 치명적입니다.
### 그러므로 저희는 이 else부분에 "게임 코드"(을)를 적을겁니다.
### 하지만 막 적는게 또 아니겠죠. 설계 유형들이 여러가지 있는데 꼭 필요한 "싱글톤 패턴"(으)로 코드를 설계할 것입니다.
### ![image](https://user-images.githubusercontent.com/87273590/153613085-cab36237-02e1-4c0e-bcfc-ffb64f9afd5d.png)
### ![image](https://user-images.githubusercontent.com/87273590/153613663-5c408bbf-c261-44a8-8bcd-57718320a513.png)
### ![image](https://user-images.githubusercontent.com/87273590/153613755-7f56efc2-e86c-422c-a290-6f2f29fce894.png)
### 폴더를 하나 만들고, 여기 안에 또 다른 폴더인 'Core'(으)로 된 폴더를 추가해 줍니다.
###![image](https://user-images.githubusercontent.com/87273590/153613926-bf893898-ab90-4daf-a78b-5ac14aae87cd.png)
### ![image](https://user-images.githubusercontent.com/87273590/153613955-a5fdf988-e32c-4215-8321-cb741590e81f.png)
### 클래스 추가 해주세요
###![image](https://user-images.githubusercontent.com/87273590/153614058-da59a1fb-1b94-4833-a6d1-86384aced5c9.png)
### 저희가 추가한 이 Core는 이 게임을 만들기 위한 중요한 역할을 하신다고 보시면 되겠습니다. 
### ![image](https://user-images.githubusercontent.com/87273590/153614641-dd58132f-fee8-45b9-a8be-95ff97448a61.png)
### 1개로 제한하는 만큼 특별하고 여러 곳에서 쓸 수 있어야 겠죠
### 모든 파일이 언제나 접근할 수 있는. "exturn"
### 하지만, 이 Core라는 객체는 몇십, 몇백개 만들 수 있기 떄문에 방지가 안되죠
### 자 그래서 이것을 불가능하게 하려면 제일먼저 떠오르는게
### ![image](https://user-images.githubusercontent.com/87273590/153615422-c1307fc5-9860-4b99-8475-2b9b2346d4a9.png)
### 생성자를 private멤버로 숨기는 것입니다.
### 하지만 이렇게 된다면 아예 객체 선언 조차되지 않죠..
### 그래서 또 어떤 아이디어가 나왔냐면, private은 자기 멤버 안에서는 호출이 가능하니, public으로 특정 함수를 만들고
### 거기서 생성자를 호출해 주는것입니다. 즉, 함수가 객체를 만들고 반환해 주는겁니다.
### ![image](https://user-images.githubusercontent.com/87273590/153615781-95546c03-e28a-482f-a96f-a69b87f57056.png)
### 근데 여기서 또 문제가 생기죠. 애초에 멤버 함수 호출은 객체를 가지고 있어야 하지 않나요?
### 그러므로 다시. 객체가 없어도 호출할 수 있는 멤버함수를 만들겁니다.
### 어떻게요? =? static~
### 자. 근데 객체가 없이 호출됐다는데 static 함수 내부에서도 Core클래스에 대한 멤버 접근을 못해요. 어떻게보면 따로 분리가 된거죠
### 또 신기한건 static멤버는 접근이 가능합니다. 이게 왜 그러냐면 static자체 특성이 그래요. static이라는건 해당 자리에 그냥 아예 꽁꽁 얼어서, 가만히 있습니다. 어디에도 이동하지 않아요
### 그래도 클래스 멤버긴 해서 Core::static_funck(); 이런식으로 접근해야 합니다.
### ![image](https://user-images.githubusercontent.com/87273590/153621611-9b63befa-3d48-43d1-a206-8a944b859ad6.png)
### 다시 본론으로 돌아와서 static으로 만들어, 외부에서 접근하도록 합시다. 객체 없이.
### ![image](https://user-images.githubusercontent.com/87273590/153622036-aab97365-bbad-489b-a6c3-08e94f5c4d8a.png)
### 새로운 객체를 만들어서 보내줍시다.
### ![image](https://user-images.githubusercontent.com/87273590/153622160-dbbb8e85-18c2-49c5-9cc3-4735663a667a.png)
### 하지만 저희는 1개만 만들 수 있다 했는데, 여러개 생성이 가능하네요? 조건문이 필요하겠습니다. 1개만 만들도록.
### 근데, 이게 생겼는지 어떻게 파악할 수 있을까.. 함수가 끝나고 나면 메모리가 분실될텐데 말이죠
### 그래서 다시 한번 static을 사용합니다.
### ![image](https://user-images.githubusercontent.com/87273590/153623094-92d4ebb7-d2f7-4c32-8b8c-e5f756224980.png)
### 자,,이렇게 작성한다면 아주 멋진 코드가 생깁니다. 처음에는 담아두었다가 나중에 다시 호출하더라도 한번 이상 호출되면
### 똑같은 객체만 리턴하겠죠
### 그럼, Release도 static으로 선언해야 되는 이유가 애초에 객체에 대한 생성자랑 그런게 아무런 정보가 없으니까
### 기계적으로 반응해야 합니다.
### ![image](https://user-images.githubusercontent.com/87273590/153624960-17260c4b-4aff-4900-9da0-91c6e6ed6d04.png)
### 근데 막상 지워가지고, 다시 달라고 할떄 뭘 줄까요?. pCore가 nullptr일까요?
### 삭제된 주소를 주겠죠.(깔끔하게 지워지지가 않음)
### ![image](https://user-images.githubusercontent.com/87273590/153625364-53fba5e4-acdf-4c75-9e33-ace019cb6f69.png)
### 해제하는 입장에서는 원본값을 모르는거에요. 어떻게 보면 static이라는 또 다른 함수 지역 변수에 접근하는건 말이 안되죠.
### 그럼 양쪽 두 함수(GetInstatnc, Release)접근하기 위해 따로 만듭시다.
### ![image](https://user-images.githubusercontent.com/87273590/153627772-2ff16fe4-63f6-471a-aac0-7cb11e38698f.png)
### ![image](https://user-images.githubusercontent.com/87273590/153627737-f500d6e9-fa83-45cd-af32-420d5c09cd1e.png)
### ![image](https://user-images.githubusercontent.com/87273590/153627950-e97d2474-8820-45a3-8f15-545e22411868.png)
### 최종적인 코드는 이렇게 되겠네요.
### Release함수에서 마지막 부분에 delete로 지워준 후에 nullptr을 다시 넣어줘야 조건문이 잘 작동할겁니다.
### 이번엔 좀 다른 방법인, 힙 영역이 아니라 데이터 영역에다가 올리는 방법도 보겠습니다.
### ![image](https://user-images.githubusercontent.com/87273590/153714386-70d42602-a58a-4f84-bc7c-eaa0c6309339.png)
### 굉장히 쉽습니다. 일단, static으로 함수 포인터는 만들어야 하긴 합니다.
### static CCore core; 이렇게 선언하면 데이터 영역을 쓴 거 아녜요?
### 동적할당을 하지 않았으므로 return은 주소값이여야 합니다. 다른곳에서도 접근할 수 있도록 말이죠
### 그리고 장점이 하나 추가되었습니다. 데이터형이기 떄문에 동적해제를 해주지 않아도 된다는겁니다.
### 단점 => 지울 수 없다.
### 한번 선언하면 계속 질질 끌어야 합니다.
### 그럼 이 2가지 방법중 뭐가 더 선호될까요?
### 저도 모릅니다. 상황에 따라 다르죠
### 근데 이 싱글톤 자체가 메모리를 딱히 안쓰기에,, 이건 정말 상황에 따라 달라질 거 같습니다.
### ![image](https://user-images.githubusercontent.com/87273590/153714554-5fd77f3b-820b-4d26-bc7c-b0381d18a2d2.png)
### 아무튼 현재 위 코드가 많이 쓰일것이므로 '매크로'(으)로 등록해 주겠습니다.
### ![image](https://user-images.githubusercontent.com/87273590/153714707-15765c09-1c10-4c1c-af48-9396170257ed.png)
### 새로운 파일과, header파일 만들어 줍시다
### 그 전에, 매크로로 어떻게 선언할까요?
### ![image](https://user-images.githubusercontent.com/87273590/153714741-d9202bea-c6ce-4729-9d68-a9207d498bb3.png)
### 간단하게 더하기를 하는 매크로를 만들었습니다. a, b인자 2개를 주면 a + b(으)로 치환해 주는겁니다.
### ![image](https://user-images.githubusercontent.com/87273590/153714772-690e6e79-04d3-4a72-94e7-6509a6dabb29.png)
### 그래서 많이 착각할 수 있는게, 10 * 10 + 20이므로 연산자 우선순위 떄문에
### (10 * 10) + 20이 됩니다. 저희는 10 * (10 + 20)을 원했는데 말이죠. 주의가 필요합니다
### ![image](https://user-images.githubusercontent.com/87273590/153714887-2320c47e-a4db-4d1f-9d18-a4b59662fd71.png)
### 암튼, 저희는 위 처럼 type(을)인자로 받아서 싱글톤 객체를 만들어 주면 됩니다.
### ![image](https://user-images.githubusercontent.com/87273590/153714909-9e1a1032-e06a-4496-84a3-0132b5e22f1b.png)
### type이 객체겠져
### ![image](https://user-images.githubusercontent.com/87273590/153714947-266df7ec-91a8-4408-a98e-90a781d439f7.png)
### ![image](https://user-images.githubusercontent.com/87273590/153714978-419af69a-7f8f-4019-9c1d-9bbc79ee73b5.png)
### 하지만 코드가 한줄로 되어 있어서 이해하기가 힘듭니다. "역슬래시(\\)"(을)를 사용하여 편하게 보이도록 합니다.
### Core클래스가 저희 프로그램에서 굉장히 중요한 역할을 할것입니다. 그렇기에 초기화 함수  init()을 만들어 보겠습니다.
### ![image](https://user-images.githubusercontent.com/87273590/153716336-2e2965d2-55a9-464c-ac9a-fdca32c176dd.png)
### 실패할수도 있으니 int형으로 선언하구요
###![image](https://user-images.githubusercontent.com/87273590/153716396-52c2a402-b004-434d-aed1-916a6cba1bc8.png)
### 일단, 윈도우에서 제공해주는 매크로를 써서 음수값을 리턴해 줍니다.
### main.cpp로 와서
### ![image](https://user-images.githubusercontent.com/87273590/153716442-d7a6971b-ca08-4e76-a3af-6c5f52c66127.png)
### FAILED는 리턴값이 음수일떄 true반환 합니다. 
### 그리고 윈도우 기능을 써서 간단하게 사유도 적어주면 좋을듯 합니다.
### ![image](https://user-images.githubusercontent.com/87273590/153716523-0bfef64d-f5d5-4425-804e-707691d1d67b.png)
### MB_OK는 약간 option입니다. 사용자가 클릭할것이 OK만 뜨는겁니다(확인 버튼)
### 그리고 Getinstanc()->int()접근은 어떻게 가능하냐면, 애초에 코어 객체를 만드는건 객체를 새로 만드는거라 멤버에 접근 가능합니다.
### ![image](https://user-images.githubusercontent.com/87273590/153716667-e92bc8fb-ea04-4d1e-b0f5-b4278b9be526.png)
### E_FAIL을 리턴하도록 했으므로 경고창이 뜹니다.
### 다시 본론으로 돌아와서 init()함수에는, 윈도우 창을 설정해 줄겁니다.
### ![image](https://user-images.githubusercontent.com/87273590/153716725-283ffb9e-8761-40dd-b2a3-5313a31cef82.png)
### ![image](https://user-images.githubusercontent.com/87273590/153717092-f5113acb-9c4b-451e-9173-045ddaf4e304.png)
### ![image](https://user-images.githubusercontent.com/87273590/153717143-435fe64a-43a9-4089-b636-5e0d99f6738e.png)
### 일단, 인자를 저장하는것만 하겠습니다.
### 본격적으로 프로그램에 메시지가 없을떄는
### prgress라는 함수를 실행시켜서 전반적인 일을 맡게될겁니다.
### ![image](https://user-images.githubusercontent.com/87273590/153717218-ac73439a-2d46-4859-a4e4-9a793bf68098.png)
### ![image](https://user-images.githubusercontent.com/87273590/153717243-702cfa06-aee4-4b8f-aa07-aa4c7e7a8a1d.png)
### ![image](https://user-images.githubusercontent.com/87273590/153717423-1aa62b7d-3ff6-4e80-a810-2a534045f286.png)
### ![image](https://user-images.githubusercontent.com/87273590/153717435-e4fad90a-93f0-4822-8a08-43d300d66b05.png)
### 핸들 전역값으로 설정합니다.
### ![image](https://user-images.githubusercontent.com/87273590/153717415-ed976b85-fe2a-4402-bef1-3d58dc32bb59.png)
### ![image](https://user-images.githubusercontent.com/87273590/153717583-b7f045cb-e1eb-42b2-ae78-32416c27a0ba.png)
### 변수명을 전부 바꿔야 하므로
### 컨트롤 + 쉬프트 + h로 열어서 바꿉니다.
### ![image](https://user-images.githubusercontent.com/87273590/153717598-ff48e183-d78d-40bf-86a5-c6490c457d8c.png)
### 잘 실행되는걸 알 수 있고, 이제 정말로 윈도우 창을 변경해 보겠습니다.
### ![image](https://user-images.githubusercontent.com/87273590/153755522-1d67d5f7-a01a-4796-ad3f-cff33d9457b9.png)
### 해당 함수를 사용하여 해상도 설정이 가능하긴 한데, 한 가지 알아야 할게 있습니다. 이 함수에서 말하는 윈도우 크기는 모두를 다 포함한 크기를 의미하기에
### ![image](https://user-images.githubusercontent.com/87273590/153755610-7e9bad0d-5874-4cd4-9dec-9872a17614a5.png)
### 윈도우 7에서는 8px정도 두께를 설정하고, 윈도우 10은 한 1px?정도 합니다. 아무튼 이러한 두께 정보라든지 예외를 감안해서
### 저희가 설정하려는 해상도보다 더 크게 값을 잡아야 겠죠
### 이걸 세팅해주는 함수가 또 있습니다.
### ![image](https://user-images.githubusercontent.com/87273590/153755726-722a396d-efd5-49de-95bf-7dd8132c515e.png)
### WS_OVERLAPPEDWINDOW는 하나의 약간 여러가지 해상도에 대한 스타일 정보인데, 따로 윈도우에서 제공해주는 기본 set들이 있습니다.
### 다이아몬드 갑옷, 금 갑옷, 철 갑옷 처럼 3가지는 기본으로 설정되어 있고 나머지 커스텀 해서 만드려면 비트값을 끄고 키면서 여러 설정들을 키고 끄면서 실험해야 하는데
### 저희는 그럴 시간이 없으니 기본으로 제공해주는 스타일을 쓰자는 겁니다.
### ![image](https://user-images.githubusercontent.com/87273590/153755792-b445c911-276e-437a-916b-e450d6f8d192.png)
### 실제로 이렇게 매우 많이 있습니다
### 한 마디로 WS_OVERLAPPEDWiNDOW는 이러한 비트값을 여러개 합쳐놓은 set입니다.
### ![image](https://user-images.githubusercontent.com/87273590/153755820-c63dc00e-b95b-4f04-b2b3-bcc5fa70eb88.png)
### 이 세번째 인자 true는 메뉴바를 감안해서 계산을 해달라는 겁니다.
### 그래야 정확한 계산이 나올테고,, rt주소값을 인자로 넣는 이유는 값이 너무 방대하기 떄문입니다.
### 함수에서 따로 return하는건 대부분 메모리 크기가 적습니다. 하지만 이렇게 큰 값일 경우 메모리를 하나 더 만들고 주는게 손해입니다. 그러므로 해당 변수 주소를 줘서 변수값을
### 바꿔서 절약하도록 합니다.
### ![image](https://user-images.githubusercontent.com/87273590/153755933-6ff5e066-4832-40b5-8d89-c6acef39305b.png)
### 값을 확인하기 위해 좌상단 우하단 좌표값을 넣고 bp를 걸어 확인해 봅시다.
### ![image](https://user-images.githubusercontent.com/87273590/153756241-df283323-daf9-4856-9b74-16807a7472dc.png)
### ![image](https://user-images.githubusercontent.com/87273590/153756255-f0b4ec9c-ad75-4773-b525-8044b18cd4cc.png)
### 8px 더 추가된걸 보실 수 있습니다. 그리고 -8, -51 빠졌습니다.
### ![image](https://user-images.githubusercontent.com/87273590/153756632-07181b43-3c17-4de8-80a2-6759c7cab820.png)
### 지금 여기 보이시는것처럼, '타이틀 바'가 51px이라는 거니깐 -51을 해야 한다는 겁니다. 더해주라는 거죠 
### ![image](https://user-images.githubusercontent.com/87273590/153756689-9d80e4fd-e071-4d38-af8b-d63b24f45578.png)
### 이것은 좌측 -8px, 우측 +8px이 돼어야 768이 보장된다는겁니다. (대칭)
### ![image](https://user-images.githubusercontent.com/87273590/153756719-934b259b-9b0d-4c6d-9c52-7549da98f052.png)
### 아래도 두께가 있으니깐 +8px
### 그러므로 오차가 난 만큼 빼겠습니다.(그럼 프로그램에서 말한 +8px가 됩니다. 음수 끼리 곱하면 +)
### 이렇게 나온 이유는 요 정도는 해줘야, 세팅에 맞다는 겁니다.
### ![image](https://user-images.githubusercontent.com/87273590/153756782-d273de0b-b1f9-4ef2-ac2d-cabebd765daf.png)
### 암튼 이렇게 작성해 주시고 실행하면
### ![image](https://user-images.githubusercontent.com/87273590/153756805-1fd579ba-8a39-45df-b791-f9ab7d0c587a.png)
### 화면이 설정되었습니다.
### 이제 더 이상 메시지 기반이 아니라, 그냥 내가 그리고 싶을떄 그릴겁니다.
### ![image](https://user-images.githubusercontent.com/87273590/153756954-31507b21-13e8-49ad-ade4-00fc9124c48b.png)
### ![image](https://user-images.githubusercontent.com/87273590/153756980-3c9e4a0c-3581-4dee-85e7-e6fe39ea7cdf.png)
### 그리고 init함수에서 DC값을 가져와서 이 변수를 쓰는건 곧 그리는 거겠죠(in window)
### ![image](https://user-images.githubusercontent.com/87273590/153757035-1c72563e-cf95-4018-b33d-d41b489e3272.png)
### 초기화 과정 거쳐주고요
### ![image](https://user-images.githubusercontent.com/87273590/153757082-f77d4837-c20b-463e-9230-6b2db396ddcd.png)
### 다 썼으면 해제를 해줘야 겠죠
### ![image](https://user-images.githubusercontent.com/87273590/153757239-0ee6704d-c972-4771-b9de-30e7980d0f3b.png)
### 자 이제 저희는, 메시지에 대한 한계를 벗어나서 여기에다가 원하는 코드를 적으면 됩니다. 계속 실행될것이기 떄문이져
### ![image](https://user-images.githubusercontent.com/87273590/153757409-62ed735a-bb60-4447-9ce0-d81aaa9442c1.png)
### 오브젝트라는 파일과 클래스, 헤더를 만드겠습니다.
### ![image](https://user-images.githubusercontent.com/87273590/153757501-bcfe23d0-1cf7-4794-aae3-c9d908b3e7b0.png)
### ![image](https://user-images.githubusercontent.com/87273590/153757507-36ca120c-71c0-4651-8026-5576353f3b2d.png)
### CCore.cpp파일에서
### ![image](https://user-images.githubusercontent.com/87273590/153757603-01a5d2c3-5058-4fe5-8db7-5df1ceefa67b.png)
### 객체 하나 전역변수로 선언한 뒤, 객체 좌표 초기화 해줍니다(변수)
### ![image](https://user-images.githubusercontent.com/87273590/153757799-14960d84-a0b2-4bbd-8741-bcc6b78d2458.png)
### (멤버 private말고 public으로 변경)
### ![image](https://user-images.githubusercontent.com/87273590/153757821-a35d78a1-38df-4735-886e-6db80a0bf746.png)
### progress함수에서는 업데이트와 랜더링 2가지만 일단 사용할겁니다.
### ![image](https://user-images.githubusercontent.com/87273590/153757854-57de5208-57f4-499b-b605-72ed7a1eea06.png)
### ![image](https://user-images.githubusercontent.com/87273590/153758189-c799442f-779e-47ba-95d6-133dbe3b2f09.png)
### 0x8000비트를 확인해보겠습니다. 이 bit부분이 눌렸는지 안눌렸는지 확인하기에.
### ![image](https://user-images.githubusercontent.com/87273590/153758234-5a736fbd-2df3-45ff-840a-61602b0b5bfe.png)
### 결과적으로 왼쪽 키 누르면 -1, 오른쪽 키 누르면 +1
### 이제 이 움직인걸 그려내기 위해 render함수 작업을 해줄겁니다.
### ![image](https://user-images.githubusercontent.com/87273590/153758485-818e7dc8-d432-410f-a513-3c5b279f4fa1.png)
### ![image](https://user-images.githubusercontent.com/87273590/153758484-d3cdefc8-282e-45f7-80c9-918579702e69.png)
### 근데 막 엄청 빠르게 이동하시는 경우가 있을겁니다. 이게 처리 속도가 굉장히 빨라서 1초에 +1이 4만번 실행됩니다.
### 하지만 이런식으로 접근하면 컴퓨터 속도가 좋은 사람은 많이 움직이고, 컴퓨터 속도가 느린 사람은 움직임이 적어진단 말이죠
### 그래서 정수로 설정하면 안된다는겁니다. 저희는 실수형태로 Vector구조체를 만들어서 미세한 움직임도 인지하도록 할겁니다.
### ![image](https://user-images.githubusercontent.com/87273590/153880095-b4907267-9004-4871-abcc-33feb7a28d0e.png)
### 헤더 파일하나 만들어 줍시다
### ![image](https://user-images.githubusercontent.com/87273590/153880200-a22538cf-9cf7-4c2b-911a-8dc15a356361.png)
### ![image](https://user-images.githubusercontent.com/87273590/153880336-ac95b730-fb8a-416b-9151-bd6797ffbca3.png)
### ![image](https://user-images.githubusercontent.com/87273590/153880353-15d9a03f-b2e3-4004-af3b-cb280a5d8030.png)
### ![image](https://user-images.githubusercontent.com/87273590/153880615-daea1afc-5b72-4fb0-a6be-cb16e4db1a31.png)
### 멤버는 private으로 하는 대신, 값을 얻어오거나 수정하기 위해 각각 함수들을 만들어 줍니다.
### ![image](https://user-images.githubusercontent.com/87273590/153880879-cb483944-c971-46e9-b7da-81508f08ead1.png)
### 실수값도 받아야 하고, 정수값도 받아야 하는데 그러한 형변환적인게 없으므로 생성자를 만들어 줄겁니다.
### ![image](https://user-images.githubusercontent.com/87273590/153881231-7b0151fa-21ea-49b1-8e04-cc00b9df93fd.png)
### ![image](https://user-images.githubusercontent.com/87273590/153881398-8d463810-290c-4995-acc5-666defa766e1.png)
### ![image](https://user-images.githubusercontent.com/87273590/153881606-63fbf127-e303-46b5-a2f9-24381b55448d.png)
### ![image](https://user-images.githubusercontent.com/87273590/153881864-ad4f4ad9-ed18-460c-81c1-72ccea39c5e0.png)
### ![image](https://user-images.githubusercontent.com/87273590/153882768-b5451c22-954c-4e72-86a7-09e3025b43f3.png)
### 저희는 정수값으로 받으면 실수로 값을 넣는걸 원했는데
### ![image](https://user-images.githubusercontent.com/87273590/153882845-10afff9e-97ad-4933-aa9e-06abe8f44571.png)
### 이 부분에서 안되므로, 위 코드처럼 바꿔줍니다.(원래 값 / 2) 정수로 넘겨줄려 했으나 안되므로 float로 캐스팅해줘서 보냅니다. 그럼 정수로 인자 받아서 float되는거랑 기능 같음.
### ![image](https://user-images.githubusercontent.com/87273590/153883197-977fd2c2-480b-4b64-bde0-9538f89e6ca3.png)
### 또한 Rectangle함수는 정수 인자값을 원하므로 int로 캐스팅 해줍니다.
### 자 그럼 우리가 이렇게 실수로 구조를 바꾼 이유가 뭘까요?
### 좀 더 작은 단위로 접근할 수 있기떄문입니다.
### ![image](https://user-images.githubusercontent.com/87273590/153883601-6302e0e5-4433-4964-ad07-94c137e17d9f.png)
### ![image](https://user-images.githubusercontent.com/87273590/153885348-ce375d2a-8106-4e54-9201-cbe804f9b3da.png)
### 그리고 키보드 입력 부분 마지막에 값을 계속해서 갱신해줘야 합니다.
### 하지만 이 마저도 한계가 있습니다. 소수점이라고 하더라도 컴퓨터 속도가 좋으면 장땡이죠
### 저희 목표는 현재시각으로 초당 100px이 나와야 합니다.(컴퓨터가 아무리 빨라도)
### 그럼 저희가 현재 설정한 0.01f처럼 고정값이 아니여야 한다는걸 이해하셔야 합니다.
### 느린컴퓨터는 초당 100px이 나오도록 값을 큼직하게, 빠른 컴퓨터는 초당 100px이 나오도록 값을 줄이기
### ![image](https://user-images.githubusercontent.com/87273590/153886199-0b933a3d-e83e-44d9-90a6-3f99efc98b4f.png)
### 다음과 같이 파일을 만들고 시간을 동기화 해줄겁니다.
### 그런데 어떻게 해야 할까요?
### 약간의 수학이 나오는데, 
### ![image](https://user-images.githubusercontent.com/87273590/153887487-d4a75aa1-02fe-480b-a846-b75f7af8caef.png)
### 제 컴퓨터가 만약 200FPS라고 합시다. 그럼 1초에 100px을 가려면 1/200, 2/200. 3/200....을 하면 200까지 누적이 되겠죠 결국엔 그럼 200/200이 되니깐 약분이 되므로 100이 됩니다.
### 이것은 수학에서 비율을 활용한 것입니다. 이런곳에 쓰인다는걸 보면 나름대로 배운 이유가 뿌듯합니다.
### 그럼 저희가 구해야 하는건 컴퓨터의 FPS(1초 동안 프레임 몇번) 즉, Delta Time(델타 타임)
### 앞으로 모든 게임 동작에는 이 델타타임이 들어가게 됩니다.
### ![image](https://user-images.githubusercontent.com/87273590/153889792-a71f0ac9-97dd-4ad3-afe5-c8869176b271.png)
### 코어쪽에서 코드 실수가 있습니다. 여기서 private을 public으로 바꿔주면 싱글톤을 만든 이유가 없으므로 같이 넣어줘야 합니다.
### ![image](https://user-images.githubusercontent.com/87273590/153890009-d43da2a3-22ce-42ac-b5d2-c32a17df530a.png)
### 코어쪽 생성자와 소멸자 지우고, 싱글톤에다가 써줍니다
### 일단, FPS구하려면 현재 시간과 일정  시간의 차를 구하고 천만으로 나눈 만큼을 리턴하면 됩니다.
### 천만은 너무 값이 큰데, 이걸 커버쳐주는 자료형이![image](https://user-images.githubusercontent.com/87273590/153890523-06912a0a-707e-4cc5-b758-d390537c1ef8.png)
### 입니다.
###![image](https://user-images.githubusercontent.com/87273590/153890743-631caa93-0a6d-4edd-a108-4bed0585b272.png)
###![image](https://user-images.githubusercontent.com/87273590/153890757-34b1d82b-d02e-4407-b95d-4c69e5b8e27b.png)
### ![image](https://user-images.githubusercontent.com/87273590/153890840-3cfeb18c-bb1f-45b6-9351-d82aa2c6a690.png)
### 그리고 1초에 카운트가 얼마나 발생하는지도 알아야 합니다.
### ![image](https://user-images.githubusercontent.com/87273590/153891036-50ef825a-597c-4f7d-8b6b-61d56c0ee289.png)
### ![image](https://user-images.githubusercontent.com/87273590/153891147-63fcc176-2d27-4451-affa-d6cf03dcb19b.png)
### ![image](https://user-images.githubusercontent.com/87273590/153891174-a3f0ff99-f705-4608-8df6-23ecaf3ad1e2.png)
### ![image](https://user-images.githubusercontent.com/87273590/153891220-94f72da8-ef91-4628-a24b-130c921f420a.png)
### 이제 빠르게 구현해 봅시다
### ![image](https://user-images.githubusercontent.com/87273590/153892252-38f53b03-6ed6-4092-83e8-a5e7672154b5.png)
### progress함수 부분입니다.
### ![image](https://user-images.githubusercontent.com/87273590/153892444-11395217-400b-4d99-b7bb-c43ca369f893.png)
### ![image](https://user-images.githubusercontent.com/87273590/153892662-e28983fd-a863-457c-ab5c-692221f527c3.png)
### 전값이랑 현재값 차이를 알기 위해, 변수 하나 더 선언합니다
### ![image](https://user-images.githubusercontent.com/87273590/153892869-9d9f6555-70a5-456f-9b7b-6bc4e17e1227.png)
### ![image](https://user-images.githubusercontent.com/87273590/153892919-9635d294-9c65-4c59-b352-4fae53ea3991.png)
### ![image](https://user-images.githubusercontent.com/87273590/153893496-2ca7a1e7-6d64-480d-9476-43a439d31dc0.png)
### ![image](https://user-images.githubusercontent.com/87273590/153893625-5a72a9e7-112a-4b5c-b1e0-37d9fed033d6.png)
### ![image](https://user-images.githubusercontent.com/87273590/153894274-c8503c9b-eadd-4379-b6af-a138072aee72.png)
### ![image](https://user-images.githubusercontent.com/87273590/153894301-751faedf-276c-4340-9407-a5e5700e9836.png)
### ![image](https://user-images.githubusercontent.com/87273590/153894447-bc78c0f1-9e80-4b2a-a76a-b6cbfce52e23.png)
### 이제 이렇게 증가하다가, 1초가 되는 순간을 알아야 겠습니다.
### 그럼 델타타임을 누적해서 비교문에 넣으면 되겠죠?
### ![image](https://user-images.githubusercontent.com/87273590/153895843-70a25e43-165e-4c30-864b-e327e8392e25.png)
### ![image](https://user-images.githubusercontent.com/87273590/153895904-413937d3-f6f1-4ebe-a587-25709ee7ad35.png)
### ![image](https://user-images.githubusercontent.com/87273590/153896319-842e4510-d621-4bfa-9459-9f4c196776ce.png)
### FPS값도 얻기 위해 변수 선언합시다
### ![image](https://user-images.githubusercontent.com/87273590/153896416-e3e1a3d5-224b-4eb5-a7c9-353b14cee7de.png)
### ![image](https://user-images.githubusercontent.com/87273590/153896723-0e1dd135-a605-4906-817c-7c56d6f0772c.png)
### ![image](https://user-images.githubusercontent.com/87273590/153896964-19707cff-8651-43ca-8012-b3970cd5c0c2.png)
### 윈도우에 출력하려고 하는데, 핸들값이 필요합니다.
### ![image](https://user-images.githubusercontent.com/87273590/153897230-cd15935e-7a99-43dc-a10b-32d75c5da4ff.png)
### 값을 얻어오는건 코어쪽에서 담당하는게 좋겠습니다.
### ![image](https://user-images.githubusercontent.com/87273590/153897396-224dd23b-2b65-4320-b62d-0e6837c93363.png)
### ![image](https://user-images.githubusercontent.com/87273590/153897441-a3950934-7f84-42d6-9ac9-cf0e76c513d3.png)
### 누적시간말고, 시간을 넣어줍시다.
### ![image](https://user-images.githubusercontent.com/87273590/153914401-d4a652c1-18ef-4446-a047-c54eaea79c43.png)
### 위에서 말한 것을 그림으로 종합적으로 표현하면 위와 같습니다.
### 1초에 천만씩 계산하니, 그 전까지 계속 카운트 값을 현재랑 전이랑 뺀값을(1이라 가정) 1초에 100(컴퓨터마다 다름)번 카운트 할 수 있는 비율로 나눠보면
### 시간을 구할 수 있을겁니다.
### ![image](https://user-images.githubusercontent.com/87273590/153912906-4e072aa7-583f-40bc-a64e-5915976e4a37.png)
### 1초라는걸 알 수 있죠
### PC : 1초 100번은, 이 PC는 1초에 100번 카운트 할 수 있다는겁니다.
### 즉, 횟수에 대해서 어느정도 인지 알 수 있다는 거죠
### ![image](https://user-images.githubusercontent.com/87273590/153915836-5b0f5ab2-3bda-4af9-b5fb-a5f0addc29fa.png)
### 델타타임을 쓰기 위해, 함수 선언하겠습니다.
### ![image](https://user-images.githubusercontent.com/87273590/154079362-f80fd51a-18a5-45b4-9633-4a4ec7beb7fd.png)
###![image](https://user-images.githubusercontent.com/87273590/154079413-a22fc404-1cbd-4684-bef7-003462770ed6.png)
### 이제 저희는 델타타임을 곱하여 이동속도를 거의 고정시키게 됩니다.
### 그리고 렌더링에도 한계가 있습니다.
### 일단 잔상이겠죠
### ![image](https://user-images.githubusercontent.com/87273590/154080929-ece52fee-e532-402b-a243-7048ce619f5e.png)
### 그래서 이런식으로 좌상단 우하단 좀 더 크게 잡아, 할려 했는데
### ![image](https://user-images.githubusercontent.com/87273590/154082263-bc51672e-2982-4c2d-830e-8887b8ce647a.png)
### FPS가 1까지 떨어지며 굉장한 효율을 보여주지 못하고 있습니다. 이게 왜냐하면 1초에 몇만번씩 저 동작을 하고 있기 떄문에 효율이 낮아질뿐더러
### 보여지다가 안보여지다가 깜빡임이 더 심해지죠
### 그래서 Double Buffering이라는 기법을 쓸겁니다
### ![image](https://user-images.githubusercontent.com/87273590/154082844-e0b4f9fd-a078-4abc-b5f2-3c4d90eee498.png)
### 유저는 다 그려진 그림만 볼테고, 과정은 따로 처리합니다. 그리고 만약 또 플레이어가 움직였다면
### ![image](https://user-images.githubusercontent.com/87273590/154082977-1f2b0b33-2d0d-4b3c-b3b1-08f53445250a.png)
### 우측에서 다 지우고, 다시 그린 후에 결과만 다시 또 보여줍니다.
### ![image](https://user-images.githubusercontent.com/87273590/154083172-6b7451d6-6656-4ff8-aef9-6cb79a447225.png)
### CCore.h에서 변수 2개를 선언 하겠습니다.
### ![image](https://user-images.githubusercontent.com/87273590/154083332-454c8fe3-7a86-4626-b260-477aee597915.png)
### 근데 비트맵이 무엇일까요?
### ![image](https://user-images.githubusercontent.com/87273590/154083687-3c4e64f9-c46a-41e9-9fb8-0fb8f1c2e143.png)
### 윈도우에서 해상도가 하나하나 픽셀들을 전부 가지고 있습니다. 이 픽셀 덩어리들을 비트맵이라고 부르죠
### 즉, 윈도우 내부에는 비트맵이 존재하는겁니다.
### 저희는 이걸 가지고 그럼 무엇을 할 수 있는가?
### 윈도우 비트맵을 복사해서 그 데이터를 가지고 과정을 거친 다음 결과를 또 다시 윈도우로 돌려주는거죠
### ![image](https://user-images.githubusercontent.com/87273590/154084502-10efd69c-30fa-4a12-93d8-5aa5f849c4e0.png)
### 일단 비트맵을 얻어와야 겠습니다. 첫번째 함수는 호환이 될 수 있도록 하는 비트맵을 새로 만든다는 것입니다.
### 그리고 역시나 이 함수도 핸들값을 줍니다. 
### 자 두번째 함수는 새로 만든 비트맵에 대한 그림을 그릴 수 있도록 목적지를 정해주어야 합니다. 복사를 하면 다시 그린다는 것이고, 그릴 수 있는 A4용지 같은게 없다면 안되겠죠
### ![image](https://user-images.githubusercontent.com/87273590/154084960-7779ed62-09d7-4fc5-9376-c640b6ba6c70.png)
### 비트맵은 나중에 지워줘야 합니다.
### ![image](https://user-images.githubusercontent.com/87273590/154085754-9b4902de-1c69-4a96-a3d7-8e39d51bf8af.png)
### 그리고 만들었다면 선택하는것도 있어야 겠죠
### ![image](https://user-images.githubusercontent.com/87273590/154085874-734744f6-9d8a-4122-bbde-46ac4128187b.png)
### 새로 만든 DC도 해제 해야 하는데, 이건 Release가 아니라 Delete입니다. 근데 이건 저도 왜 이런지 모릅니다. 그냥 윈도우 만든 사람이 이렇게 쓰라고 래퍼랜스에 밝혔으니, 이렇게 하면 됩니다.
### ![image](https://user-images.githubusercontent.com/87273590/154086398-7b0818a2-fa02-4d74-8a86-ed1381a33243.png)
### 이제 비트를 한땀한땀 복사해야 합니다. 
### 이걸 해주는 함수가
### ![image](https://user-images.githubusercontent.com/87273590/154086813-936fe308-4f28-46bb-b6d8-031aba8b3167.png)
### 인데
### ![image](https://user-images.githubusercontent.com/87273590/154086838-18987302-821d-4759-92a4-f789114cef17.png)
### 이 기존 윈도우하고 좌상단 우하단 0, 0 해상도 좌표는 (m_memDC비트맵으로 부터)복사당할 좌표들입니다.
### ![image](https://user-images.githubusercontent.com/87273590/154086943-9d8ef99c-a408-4a3a-85e6-b33d28e695a9.png)
### 거기에 전달할 그림은 m_memDC가(소유하고 있는 비트맵) 되겠죠 이것도 0, 0부터 SRCCOPY(으)로 메모리 복사
### SRCCOPY가 해상도를 어떻게 알죠? 이미 아까전에 전부 해상도 입력 받았습니다.
### ![image](https://user-images.githubusercontent.com/87273590/154087303-d072e43e-0088-4af2-a94c-f493032a3da7.png)
### ![image](https://user-images.githubusercontent.com/87273590/154089580-3c8e3f37-20ac-4900-a1b1-cb10d1385ad3.png)
### 화면 그리는거랑, clear할떄 m_memDC로 바꿔줘야 합니다. 내부 윈도우로 복사하기 전, 그려야 하는 과정이 노출되면 안되니까요.
### 직접적으로 화면으로 보여주는건 BitBlt함수가 하고 있습니다.
### ![image](https://user-images.githubusercontent.com/87273590/154089998-8ab6fee2-1c96-4cfb-b5e8-03522d510c99.png)
### 이 함수를 통해  상당히 많은 프레임을 먹고 있지만, 어차피 게임은 60FPS만 유지하면 됩니다.
### 이제 KeyManager라는걸 만들겁니다. 이건 왜 필요할까요?
### ![image](https://user-images.githubusercontent.com/87273590/154097915-d3cdfac8-cb21-4b9a-8488-aa1523600231.png)
### 1frame당, 업데이트와 랜더링 코드들이 있고, 이 기능들은 DT시간만큼 발생합니다.
### ![image](https://user-images.githubusercontent.com/87273590/154098283-0e15ef9c-cad5-47a9-8dc2-625de9184708.png)
### 여기 처음에 LEFT가 눌려서, 왼쪽으로 간다고 생각했습니다.
### 근데 또 맨 마지막쯤에도 LEFT가 눌리면 어떤 기능을 수행하는 코드가 있습니다. 근데, 정말로 찰나에 맨 마지막쯤에 LEFT가 떼졌어요
### ![image](https://user-images.githubusercontent.com/87273590/154098527-107edbb1-efef-449c-89df-bc7a38283605.png)
### 마지막쯤에 UP이 된거에요. LEFT가 실행될려다가 말이죠
### 그럼 누구는 왼쪽에 대한 처리를 받았고, 누구는 UP에 대한 처리를 못받고 난리가 납니다.
### 물론, DT가 굉장히 짧은 시간이라 쉽지는 않겠지만 분명히 발생할 수 있다는 겁니다.
### 일단 키매니저를 사용하는 이유 첫번쨰 프레임 동기화(한 프레임에서 발생한 키입력은 제대로 처리)
### 즉, 모든 키에 대한 상태값을 저장해 놓고 한 프레임에 키값이 겹친다면 동일한 이벤트로 가져오겠다는 겁니다(상태값 중에)
### 두번째는 현재 저희가 키보드 입력에 대한 구체적인 이벤트 정보가 없습니다.
### ![image](https://user-images.githubusercontent.com/87273590/154272688-07bb8ed2-f735-4452-905b-3c13deb3accc.png)
### 이 구체적인 이벤트 정보가 없다면 이전 프레임에서 엔터를 누르지 않고, 현재 프레임에서 누르면 최초로 눌렀다고 알고 싶은데
### 그런게 없다보니 ![image](https://user-images.githubusercontent.com/87273590/154272855-67d54ecf-7644-46f4-ab6d-d9aad561af9d.png)
### 다음 프레임에서도 엔터를 누르면 최초의 코드가 연쇄적으로 실행되겠죠
### 다시 엔터를 떼거나 누르지 않는 이상 조건 트리거를 발생하고 싶지 않아요
### 그럼 엔터가 최초로 눌려 있을떄만 하도록 해야 한다는 겁니다.
### 계속 누르고 있을떄는 조건 트리거에 걸리면 안되구요
### 또한 계속 쭉 누르다가 뗐을떄 조건에 걸리고 싶습니다.
### ![image](https://user-images.githubusercontent.com/87273590/154273432-2695fb42-f84e-412e-93bd-d80c41ea078a.png)
### 암튼, 이런식으로 키 입력을 구체적으로 정해주고 싶기에 키매니저가 필요한겁니다.
### ![image](https://user-images.githubusercontent.com/87273590/154273684-0e7fff95-6247-4d58-abe9-04aaed7050b1.png)
### 파일 새로 만들어 줍니다.
### ![image](https://user-images.githubusercontent.com/87273590/154274765-880673db-e86b-41c8-9bf8-afd570d33879.png)
### ![image](https://user-images.githubusercontent.com/87273590/154275179-a6adcee3-e419-487b-a8ed-63df9e35e0ad.png)
### 이것은 상태값이라 정말로 키값을 의미합니다.
### ![image](https://user-images.githubusercontent.com/87273590/154275386-ada54cec-ba25-4045-8f84-6dc332a890dd.png)
### 특수까지 추가+
### ![image](https://user-images.githubusercontent.com/87273590/154275569-7cb3d305-20ab-47de-a934-90a05a7a4f70.png)
### 그리고 하나의 구조체를 만들어서 vector에 저장해 줄겁니다.
### ![image](https://user-images.githubusercontent.com/87273590/154275938-8f035edd-2034-4ab0-bb74-adcea8bade2b.png)
### 근데 잘 생각해보니, 키값은 없어도 되겠네요. vector라는게 애초에 인덱스를 담고 있으니 말이죠
### ![image](https://user-images.githubusercontent.com/87273590/154276194-ca42e741-6795-4cd9-9d4b-7588054db686.png)
### 그러므로 bool값을 추가하여, 이 전 프레임에서 키가 눌렸는지 안눌렸는지 확인하는 변수를 추가 하겠습니다.
### ![image](https://user-images.githubusercontent.com/87273590/154277103-f66b6bb5-e521-46a7-a892-834f6ecd55d1.png)
### 초기화 해줍니다.
### 인덱스가 곧 키값을 말해줍니다
### ![image](https://user-images.githubusercontent.com/87273590/154277594-684c6e6c-9611-49bf-b539-a1098a334328.png)
### 그럼 접근할 떄 이렇게 할 수 있는겁니다
### 사실은 m_vecKey[0].eState이렇게 접근하는거랑 같지만요
### ![image](https://user-images.githubusercontent.com/87273590/154278325-7037d708-6984-4c7d-9b30-8456664635b2.png)
### 이제 여기서 키값을 받긴 받아야 하는데, 문제가 생깁니다. enum값은 그냥 정수이기 떄문에 VK_UP이든 뭐든 절대 관련이 없습니다. 그래서 전역변수에다가
### 저희 enum순서를 똑같게 해서 키값을 넣어주면 된다는겁니다.
### ![image](https://user-images.githubusercontent.com/87273590/154280901-f8ab06a6-f3b1-402a-b126-967ceef69c69.png)
### ![image](https://user-images.githubusercontent.com/87273590/154281464-ae32a883-d2b1-4548-b092-daf0fdbc9f75.png)
### 키가 눌려있는데 이전에도 눌려있는 상태였다면 계속 누르고 있다고 판단할 수 있겠습니다.
### 그게 아니라면 막 누른 시점이겠죠
### ![image](https://user-images.githubusercontent.com/87273590/154282459-31dd039e-389b-428f-b04f-5c8719be6c8a.png)
### 마지막에는 처음 초기값이 false이기 떄문에 true로 바꿔줘서 이전에 TAP이 였으니, true가 되면 이전에도 눌려져 있는 조건문으로 이동하겠죠
### ![image](https://user-images.githubusercontent.com/87273590/154283098-9924395a-8fa9-4190-845a-71cacf1400f1.png)
### 키가 눌리지 않았는데 전에 눌렸다면 막 뗀걸로 해석이 가능하다.
### 키가 눌리지도 않고 전에도 눌리지 않았다? 아무런 상태가 아니라고 판단이 가능하겠죠
### 그리고 마지막에는 전에 눌려져 있는 상태값을 false로 바꿉니다.
### false로 바꾼 후 키가 눌려졌다면, 이제 막 누른시점으로 조건문이 걸릴수가 있기 떄문입니다.
### 키가 눌려지지 않는다면 당연히 아무런 상태값이 아닌걸로 조건문이 걸리겠죠
### 이런겁니다. 키가 눌려졌다면 true로 바꿔서 다음에 전에 눌렸는지 확인이 가능하고, 키가 눌려지지 않았다며 false로 바꿔서 다음에 전에 있던값을 확인했을 떄 안눌렸는지 확인 가능.
### ![image](https://user-images.githubusercontent.com/87273590/154285432-d79ad753-9063-4ba9-959a-2fe9575a7883.png)
### 가상키는 16진수로 넣어야 잘 들어갑니다.
### ![image](https://user-images.githubusercontent.com/87273590/154285762-30f72790-8370-4378-936c-84e2321553e7.png)
### 키값이 들어오면 상태값을 알려주는 함수를 만들어야 합니다. 그래야 쓸 수 있겠죠
### ![image](https://user-images.githubusercontent.com/87273590/154286485-c95e8dfb-7b0b-4840-8251-f037aa34de5c.png)
### 이제 누르면 움직입니다. 그 외에는 움직이지 않아요
### 키매니저에서 마지막으로, 윈도우에서 포커싱이 되지 않았을떄에 처리입니다.
### 포커싱이 안되어 있을 떄 입력값을 처리해야 하는데
### ![image](https://user-images.githubusercontent.com/87273590/154289223-b6836eca-c478-4400-ba02-cc3d43915716.png)
### 순차적으로 처리해 주어야 결함이 생기지 않습니다.
### ![image](https://user-images.githubusercontent.com/87273590/154289533-16ddc6e6-8890-44fd-9428-734318ad0827.png)
### 일단 윈도우 포커싱이 되었는지 알아야 하기 위해, 핸들값과 포커싱이 되어있는지 함수를 통해 알아냅니다.
### 포커싱 return값이 윈도우라면 일반적인 처리를 해주고, 그게 아니라면 다른 처리 방식을 도입해야 겠죠
### ![image](https://user-images.githubusercontent.com/87273590/154289811-4b5f8cfd-c095-4bb5-af10-dae431398ae8.png)
### 근데 굳이 이 핸들값을 얻어올 필요가 없습니다. 포커스 함수는 윈도우가 아니면 nullptr을 리턴하기 떄문입니다.
### 빡세게 할 필요가 없다는 겁니다.
### ![image](https://user-images.githubusercontent.com/87273590/154290854-c6891eae-f12a-4c7c-b09c-53cd06b11f55.png)
### ![image](https://user-images.githubusercontent.com/87273590/154290827-b8e73eda-f4b3-40c1-9c45-2a17f4741e21.png)
### 자 이렇게 포커싱이 되어 있을떄와, 안되어 있을떄를 구분해 줍니다.
### 이제 창을 내리면 아무리 키를 입력해도 움직이지 않습니다.
### 저희가 현재 오브젝트를 하나 만들어 놨는데, 정사각형이죠?
### 그러나 여러가지 많을 수 있어요. 총을 잡은 오브젝트, 또는 UI면에서의 오브젝트들 등등
### 그럼 이 오브젝트를 관리해주는 것이 필요합니다.
### ![image](https://user-images.githubusercontent.com/87273590/154500781-3b6521f3-535b-4f55-9857-e815ed7fb432.png)
### 이 관리하는 것을 Scene즉, 스테이지와 비슷한겁니다.
### 잠시 define.h파일에 오셔서
### ![image](https://user-images.githubusercontent.com/87273590/154501195-53d09563-1a56-41a3-9347-0be382cb0a1d.png)
### 이러한 각 스테이지마다 오브젝트 그룹들을 enum자료형으로 만들도록 할게요,
### ![image](https://user-images.githubusercontent.com/87273590/154503227-108cac9d-f717-4abe-a107-b73bf4f5b976.png)
### 일단, CObject써야 하는데 현재 아무런 타입을 모르므로 포인터 형식으로 선언해야 합니다.
### 그리고 백터에다가 END인덱스를 저장하고 있는데 특정 오브젝트를 가르킬 수 없어서 마지막을 기준으로 잡은겁니다. 그럼 메모리를 너무 많이 잡아먹는게 아닌가?
### 실제로 쓰지 않는 데이터는 그렇게 많이 잡아먹지 않습니다. 데이터를 추가하는 동시에 힙메모리 영역을 쓰기 떄문에 텅 빈곳은 그렇게 먹지 않으니 걱정 하지 않으셔도 됩니다.
### 이제 이 Scene을 관리할게 필요합니다. 그것을 SceneManager라고 하겠습니다
### ![image](https://user-images.githubusercontent.com/87273590/154503946-1e005568-f762-4b84-9245-73ac16714470.png)
### 근데, 이 오브젝트들을 담은 여러 Scene도 있지 않을까요?
### ![image](https://user-images.githubusercontent.com/87273590/154504269-6a8b4682-e3f4-44ad-aaca-ec9a61950948.png)
### 이렇게 만들어 보겠습니다. 
### ![image](https://user-images.githubusercontent.com/87273590/154504727-3dc9626f-daa8-419e-ab0c-29ac5fd66b73.png)
### Scene까지 담아 보았고,
### 현재 Scene이 무엇인지 알 수 있는 변수를 만듭시다.
### ![image](https://user-images.githubusercontent.com/87273590/154505117-d0c4b899-c2e2-41a1-86a2-65771dfb9d24.png)
### SceneMgr에서 생성자 만들어 주고 초기화도 해줍시다.(m_pCurScene)
### ![image](https://user-images.githubusercontent.com/87273590/154505295-1c106e39-3b55-421d-99b5-d053fd6203a4.png)
###![image](https://user-images.githubusercontent.com/87273590/154506721-37ce7d6e-2f4c-4950-b0d2-08f58eb05716.png)
### SCene을 생성하려면 정말로 만들어야 겠죠
### 현재 저희는 부모 클래스들만 만들었습니다.
###![image](https://user-images.githubusercontent.com/87273590/154507273-e71bc231-8dbd-46e4-8522-3f0acc700744.png)
### ![image](https://user-images.githubusercontent.com/87273590/154507330-8da64973-1c0e-4a00-ae9c-4de7d6afde55.png)
### 저희가 현재 만든 이 SCene은 실제로 쓸것이 아니라, 상속으로 받는애들로 부터 공통된 기능이죠?
### 이럴 경우에 절대 까먹지 말고 해줘야 하는게 모든 Scene관련이 전부 상속으로 부터 전해져 오기 떄문에 
### 소멸자 호출부분을 virtual로 만들어야 합니다.
### 이 virtual로 만들면 Scene에서만 소멸자가 호출되는게 아니라, 자식까지도 소멸자가 호출되기 떄문입니다
### ![image](https://user-images.githubusercontent.com/87273590/154507957-a4a3a9fd-c357-49c9-a15e-560fbce34cff.png)
### ![image](https://user-images.githubusercontent.com/87273590/154507996-aa2dd33b-7981-4e6d-ac7d-ab630b81417d.png)
### Object같은 경우에도 예외는 아니죠. 상속으로부터 받으니까요
### ![image](https://user-images.githubusercontent.com/87273590/154508683-18e09042-e706-4fec-9653-9e5e0ea0bd12.png)
### 일단 스테이즈 start헤더파일에서 상속을 받습니다
### SCeneManager.cpp파일에서
### ![image](https://user-images.githubusercontent.com/87273590/154508881-762ba127-2a96-4caa-8e0a-4da10c5a5d29.png)
### START로 된 스테이지를 동적할당 해줍니다
### ![image](https://user-images.githubusercontent.com/87273590/154509012-33861aea-242b-4760-ad0f-17b4cf3a36a1.png)
### Scene도 지정해 주고요
### ![image](https://user-images.githubusercontent.com/87273590/154509224-56c3b074-1a37-4e6b-a26f-3e32fbf7a28a.png)
### Core.cpp파일 가서 초기화도 합니다.
### ![image](https://user-images.githubusercontent.com/87273590/154509452-29c8dfde-4c0b-4eae-9089-d3d3a5d0f71b.png)
### 이제 부모쪽에서 Scene들을 다 지우는 기능을 넣으려 하는데, 처음에 nullptr로 변수들을 초기화 했기 떄문에 막 지워버리면 nullptr일수도 있잖아요.
### 예외 처리 해줍시다
### ![image](https://user-images.githubusercontent.com/87273590/154509693-e396956e-9d0e-4695-b2ea-2c513a3c2c3c.png)
### 준비는 이제 마쳤고, 구조도 조금 바꿔야 합니다.
### ![image](https://user-images.githubusercontent.com/87273590/154509835-7956618d-f74c-4227-8bb0-819bc565f5d6.png)
### 코어쪽 코드에서 오브젝트를 전역으로 두고 그냥 그렸는데 이제는 씬을 만들고 그 해당 씬에서 오브젝트들을 만들어 내는 방식으로
### ![image](https://user-images.githubusercontent.com/87273590/154510595-4b302d96-ecda-430f-8c71-db3b6853d553.png)
### 잠시 수정사항이 있습니다.(start_SCene에서 생성자 소멸자 지워주세요)
### ![image](https://user-images.githubusercontent.com/87273590/154510683-b307b93e-ed58-448f-bbe5-05519b03ce19.png)
### SCeneMgr.h에서도 생성자, 소멸자 지워주세요
### ![image](https://user-images.githubusercontent.com/87273590/154511419-cbf1907e-b6ce-434f-b454-bf0bb1b6b52f.png)
### 구조를 완전 바꿔줍니다.
### ![image](https://user-images.githubusercontent.com/87273590/154515320-52f23d9a-beca-4286-9e02-685f77110191.png)
### 그에 맞는 함수를 선언하고 구현해 줄겁니다.
### ![image](https://user-images.githubusercontent.com/87273590/154515544-7d1c0b6c-073d-41a1-9d85-5dbd939f507b.png)
### 그럼 결국엔 udate쪽에서는 SCene을 지속해서 업데이트 해줘야 할테고
### render쪽에서도 현재 SCene을 계속 그려야 겠져
### ![image](https://user-images.githubusercontent.com/87273590/154515815-27fb10e7-5c1c-4f0e-96db-672365b6f376.png)
### 이 DC인자는, 일단 다른곳에 그렸다가 내부 윈도우에 복사하기 위함이라고 생각하시면 됩니다.
### ![image](https://user-images.githubusercontent.com/87273590/154516306-98ff434f-fabb-4767-b850-af0130afe008.png)
### 각자 다른 Scene들에서 start함수가 있을겁니다. 이걸 상속을 활용하면
### ![image](https://user-images.githubusercontent.com/87273590/154516273-df39586a-b8e2-46bf-93e6-511d342cba54.png)
### 각 start함수가 실행되려면 virtual함수가 되어야 하지 않을까요?
### 그리고 start함수는 각각에서 만들어야 하는 의무가 있어야 하죠
### 그래서 순수가상 함수로 만들겁니다. 추상클래스로 말이죠
### CScene.h에서
### ![image](https://user-images.githubusercontent.com/87273590/154517400-21f5048d-5ffe-4cc9-a928-f39c8e754793.png)
### ![image](https://user-images.githubusercontent.com/87273590/154517619-d950394a-7d76-4bb6-936d-82373631c653.png)
### 부모로부터 상속 받았다 하더라도, 모르기도 하고, 각자 만들어 줘야 하기떄문에 선언은 해줘야 합니다
### ![image](https://user-images.githubusercontent.com/87273590/154517791-e47b08ee-93e8-464b-ba7e-e89cc4dc70a2.png)
### ![image](https://user-images.githubusercontent.com/87273590/154518960-adcb5444-0480-4735-afbc-5509207325d5.png)
### 본격적으로 설정을 해주고요
### ![image](https://user-images.githubusercontent.com/87273590/154519221-7b1b4470-2ef2-4dda-a9e9-f78c87ba2ad9.png)
### STart함수 구현하려 했는데, 아무리 상속을 받아도 자식이 부모쪽에 접근을 못합니다. 해결 방법은 protected쓰면 되는데 다른 방식으로 하겠습니다.
### 왜냐면 원래 private을 protected로 바꾸면 원래 의미가 바뀌지 않을까요?
### SCene.h부모쪽에서
### ![image](https://user-images.githubusercontent.com/87273590/154519561-5475b48c-90f1-4b0a-9b0b-26ab2ed6bcff.png)
### protected로 함수 따로 구현합니다.
### ![image](https://user-images.githubusercontent.com/87273590/154519753-36046300-3ee3-4eef-ab34-bdcb8f639aa9.png)
### 이제 이런식으로 할 수 있습니다.
### ![image](https://user-images.githubusercontent.com/87273590/154519933-093b6bec-54af-4f59-8e92-c685f802d306.png)
### 구현은 해주고요
### ![image](https://user-images.githubusercontent.com/87273590/154520397-9c23e475-b36a-4fc4-a02a-cdce5c42338a.png)
### 오브젝트가 얼마나 많을지 모르니, 삭제해 줍니다.
### ![image](https://user-images.githubusercontent.com/87273590/154520853-a637116c-945f-4905-af06-349b57813f6c.png)
### 객체도 어느정도 만져줍시다
### ![image](https://user-images.githubusercontent.com/87273590/154521077-74a7eeb0-1a1d-43ad-aea1-2e0f18127ec1.png)
### update, redenr도 새로 또 만들어 줍니다.
### ![image](https://user-images.githubusercontent.com/87273590/154522179-34a16336-0cd5-4d79-9f72-df7b9bf6bcd7.png)
### 이렇게 만들고 나니, Object 단에서도 updte와, render가 필요해 보이네요
### ![image](https://user-images.githubusercontent.com/87273590/154522434-d21f038f-86e8-4857-aa61-ed2d0418d327.png)
### 선언까지 합니다
### ![image](https://user-images.githubusercontent.com/87273590/154522865-c5a06e2c-bf20-4699-b663-05af922f30c8.png)
### 어떻게 보면 코드를 그냥 복붙한 것입니다.
### ![image](https://user-images.githubusercontent.com/87273590/154523822-76914235-16d8-45f0-998f-314f8d62c0f8.png)
### render쪽에서는 그냥 그려주기만 하면 되겠죠
### 이번엔 오브젝트에 대해 좀 깊숙히 들어갑시다.
### 현재 구조로 오브젝트를 만들게 된다면, 하나가 여러 오브젝트를 조종하는 그러한 것들이 되어버립니다
### 오브젝트마다 속도, 몸집, 크기 등등이 있을텐데 하나로 통합하기엔 그렇지 않나요? 아니, 그러면 안되겠죠
### ![image](https://user-images.githubusercontent.com/87273590/154689168-e1540ced-30ca-4b96-9279-26b85944bcc1.png)
### 오브젝트를 관리하는 부모가 있을테고, 각각 오브젝트마다에 특성이랑 기능이 있기때문에 상속과 다형성을 통해 구현해야 할것입니다
### ![image](https://user-images.githubusercontent.com/87273590/154689284-30673b5c-c26c-42d5-b05e-01f70da5bacd.png)
### 그럼 virtual로 하는게 맞겠죠
### ![image](https://user-images.githubusercontent.com/87273590/154689542-2ae6c634-5113-4788-81ca-b378050c8ea2.png)
### 플레이어 오브젝트 파일을 만들겠습니다.
### ![image](https://user-images.githubusercontent.com/87273590/154689699-7331c906-b1d4-4b30-9a2f-db6386f17f35.png)
### 플레이어만에 update와, render함수가 생겼습니다.
### ![image](https://user-images.githubusercontent.com/87273590/154689943-1ae62b9e-b9f5-4827-b72b-8764a18aaf96.png)
### 대충 이런거죠
### 그럼, Scene에다가는 Player오브젝트를 넣어줘야 할겁니다.
### ![image](https://user-images.githubusercontent.com/87273590/154690051-379504b1-4c8f-430e-bcba-da3b00238522.png)
### 그래야 씬에서 저희가 원하는 오브젝트들이 배치될겁니다.
### ![image](https://user-images.githubusercontent.com/87273590/154690135-455fc667-9190-4b79-8fba-8b273f1f80d5.png)
### 그리고 이렇게 오브젝트를 부모로 하고 각각 다른 기능을 가지도록 하는 오브젝트 형식으로 설계하면 좋은 점이, Player오브젝트가 움직이면 이 오브젝트만 움지이고
### 다른 오브젝트에는 영향을 전혀 주지 않기 떄문에, 이 또한 장점이라고 볼 수 있겠습니다.
### ![image](https://user-images.githubusercontent.com/87273590/154690484-4a8d2548-5cbf-497a-be8d-b44830decee7.png)
### 이것들은, 부모 객체의 멤버이긴 하지만 protected로 개방하지 않았기 떄문에 접근할 수 없습니다. 대신 v_pos를 얻어오는 함수가 있으므로 그걸 사용해서 받아오면 됩니다.
### ![image](https://user-images.githubusercontent.com/87273590/154690690-e09c30e7-33ed-497c-9985-44c63b50709f.png)
### 이렇게 바꿔줄수가 있겠고, 현재 지역변수이기 떄문에 전역에서 접근을 못하므로 SetPos함수를 사용하여 바꿔줍니다.
### ![image](https://user-images.githubusercontent.com/87273590/154693756-6b1c07a1-362e-4ea9-ade6-2d46ce77a92f.png)
### CObject.h에서 update는 순수가상 함수로 만들겁니다. 어느 오브젝트든 update함수는 무조건 만들어야 하니깐요
### ![image](https://user-images.githubusercontent.com/87273590/154693858-4c91c419-4283-4932-9c12-936305ce7dcd.png)
### 이제 앞으로 모두 상속받는 오브젝트들은 update()를 구현해야 합니다.
### 암튼 저희는 몬스터 오브젝트를 한번 만들어 볼게요.
### ![image](https://user-images.githubusercontent.com/87273590/154694970-4286a3d7-1d90-460c-8a3f-890591e5cb54.png)
### ![image](https://user-images.githubusercontent.com/87273590/154695113-c0ebe8e3-51f0-42d1-8a8a-3a0b41c20613.png)
### 몬스터에게는 스피드라는 변수도 만들어 주겠습니다.
### 간단하게 몬스터가 좌,우 로 움직이게 할겁니다
### ![image](https://user-images.githubusercontent.com/87273590/154697341-9af9e911-b045-4561-9949-2eaf99f1ceb5.png)
### 변수는 이렇게 될 거 같습니다. 각 변수가 무슨 역할을 하는지 구체적인건 만들면서 알게 됩니다.
### ![image](https://user-images.githubusercontent.com/87273590/154697407-97f83fb8-e0f5-4fdf-9465-33750f29782a.png)
### 초기값은 이렇게 하고, 방향은 처음에 양수로 시작할 것입니다.
### ![image](https://user-images.githubusercontent.com/87273590/154697521-2eccca93-c035-42ed-bedb-929827468352.png)
### 센터값은 수정할 수 있기에, 함수하나 만들어 주고요
### ![image](https://user-images.githubusercontent.com/87273590/154698027-393e9648-834c-42d6-9c98-7aca84e01f57.png)
### 일단 이동을 해줘야 겠죠?
### ![image](https://user-images.githubusercontent.com/87273590/154698169-ac33b9cf-0d65-4246-a201-4b65d21b6aa8.png)
### MAxDistance까지 왔으면 부호를 바꿔서 이동하는게 맞겠지만, 시간으로 현재 보고 있으므로 최악일 경우를 대비해야 합니다.
### 살짝에 오차가 날수도 있다는 거죠
### ![image](https://user-images.githubusercontent.com/87273590/154698558-b3059953-4f93-4bae-8643-a612fcc70eaf.png)
### 그럼 이 오차가 난 만큼, 부호가 바뀔떄 다시 그 만큼 이동시켜주어야 할겁니다
### ![image](https://user-images.githubusercontent.com/87273590/154699096-817896ff-9ffb-4350-99c4-85443bc34ae6.png)
### 그 조건문은, 현재 위치에서 MAxdistance를 계속해서 빼다가 음수가 나온다면 범위를 넘어섰다는 것이고 이 거리가 오차가 된 거리가 된다고 볼 수 있겠습니다.
### ![image](https://user-images.githubusercontent.com/87273590/154699452-fdc8d680-9da1-46bb-ae54-b46e8ffc42b6.png)
### 좋습니다. 이제 확인해볼까요?
### ![image](https://user-images.githubusercontent.com/87273590/154701056-69d092b5-d69e-470e-ae20-fae5fed6c43e.png)
### 그 전에 비교문 위 코드처럼 수정 해주세요.
###![image](https://user-images.githubusercontent.com/87273590/154700825-336e28da-9132-42b4-859c-8ae5e4a59d44.png)
### 아마 좌, 우로 이동하는 물체를 보실 수 있을겁니다.
### 오브젝트가 하나만 생성된다면?
### ![image](https://user-images.githubusercontent.com/87273590/154701707-4ed3d4c9-8561-4953-be47-57649e832905.png)
### 오브젝트를 삭제하거나 추가하는 코드 부분에서 생길걸겁니다. 저 같은 경우 j반복문에서 i++을 하고 있어가지고, 그랬습니다. j++로 고쳐주니 정상 작동합니다
### 오브젝트를 이제 막 여러개 설치해 주고 싶다면 for문 써서 배치해 주면 되는데, 마음대로 해버리면 겹쳐지고 난리나겠죠
### 해상도에 따라서 배치를 해야 하기 떄문에 해상도값을 받겠습니다.
### 근데 해상도값은 있는데, 받아오질 못하죠
### ![image](https://user-images.githubusercontent.com/87273590/154703645-74757070-b3c5-4cb0-abdf-b58d1ab03ab7.png)
### ![image](https://user-images.githubusercontent.com/87273590/154703744-fdd81e56-55e9-4289-85ff-898465be36e8.png)
### 하지만, 포인터 구조체라서 Vec2구조체에 담을수가 없네요.
### 오퍼레이터로 해결합시다
### ![image](https://user-images.githubusercontent.com/87273590/154704043-5da0f67f-37f1-4d86-8af1-e641d430d19b.png)
### 래퍼랜스로 가져올게요
### ![image](https://user-images.githubusercontent.com/87273590/154704470-f905c8b0-4f3e-4561-bc16-cf3f73793a03.png)
### 복사생성자가 돼버렸는데, Vec2생성자가 호출되지 않고 넣어지고 있기에 형변환이 이루어지지 않고 float에 POINT을 넣는것과 같은 모습입니다.
### 그래서 따로 이러한 다른 외부 객체를 복사받을떄는 그에 맞는 오버로딩을 따로 해줘야 합니다.
### Vec2랑, POINT랑은 완전히 다른 형이기 떄문에 Vec2생성자에서 따로 float x와, float y에 넣어줘야 합니다.
### ![image](https://user-images.githubusercontent.com/87273590/154705434-12fbdfc9-abfc-4153-9bc8-41f2dfe642f4.png)
### 생성자 오버로딩해줘서 넣습니다.
### 즉, 현재 POINT를 받되, 생성자에서 호출될 떄 해당 POINT에 맞는게 없으니 저희가 구현해 준겁니다
### ![image](https://user-images.githubusercontent.com/87273590/154707160-05d9aebb-6b02-4a2f-925f-a1b1bd41e625.png)
### 근데 생각해 봐야 할게 있습니다. 그냥 배치하면 안된다고 했죠?
### ![image](https://user-images.githubusercontent.com/87273590/154707310-22ef9822-a8fb-406c-b824-da54e93603d6.png)
### 해상도에서 양쪽을 100px만큼 뺄게요. 그래야 맨 왼쪽에 있는 몬스터가 100px단위로 움직일 떄 보일 거 아니에요
### ![image](https://user-images.githubusercontent.com/87273590/154707540-de54a17f-5b0f-47ec-a0a5-2f4bbd078d29.png)
### 몬스터 5마리를 배치한다고 할 떄, 남은 해상도에서 나누기 4를 해야
### ![image](https://user-images.githubusercontent.com/87273590/154707668-9c0731cd-aa0a-43b1-8d39-648d9a817498.png)
### 이 배치할 거리가 딱 균등하게 나오겠죠
### ![image](https://user-images.githubusercontent.com/87273590/154708208-6a09e8e5-a10a-487c-88c2-5e6b6c73b4b8.png)
### ![image](https://user-images.githubusercontent.com/87273590/154708245-219ef1d9-bd69-4206-be3d-6d098ae78d42.png)
### i씩 하면, 1 x fTerm, 2 x fTerm, fTerm배수만큼 배치될겁니다.
### ![image](https://user-images.githubusercontent.com/87273590/154710776-ae93a297-e29b-4bd6-aeea-11f42b69cab8.png)
### 그 전에 맥스 거리가 너무 길어서, 50으로 설정합니다.
### 근데 막상 실행하면 자신의 절반만큼 빠져 나갈거에요
### ![image](https://user-images.githubusercontent.com/87273590/154708775-5e1b0303-32f7-4516-a2a3-22376abee0ee.png)
### 맨 왼쪽이 벗어난 해상도입니다.
### 잘 보시면 100만큼 배회하는데, 내 몸 반이 삐죽 나오죠?
### 스케일도 생각해야 한다는 겁니다.
### ![image](https://user-images.githubusercontent.com/87273590/154710852-8a6d1ffa-54c4-48be-a1f9-a013f4cb7d21.png)
### 이를 개선한 코드입니다. 이제 딱딱 균등하게 좌우로 움직입니다.
### ![image](https://user-images.githubusercontent.com/87273590/154711125-281b1687-130f-4cd5-bc3f-2c2d6a628782.png)
### 좀 더 개선하면 이렇게 바꿀 수도 있겠습니다. 나누는 곳에서 -1을 하는 이유는 몬스터 5마리 배치했을 떄 4로 나눴죠?
### 몬스터가 n마리 라면 배치하는 공간(거리)는 n - 1만큼 생기기 떄문입니다.
### 자 이제 몬스터를 배치했는데 움직이기만 하면 재미가 없어요. 몬스터도 어떠한 공격을 하고, 플레이어도 공격을 하는 그런 코드를 짜봅시다.
### ![image](https://user-images.githubusercontent.com/87273590/154712127-561c2ba2-afc5-42f0-ad36-d7e98cec2b68.png)
### 미사일 파일 만들어 주시고
### ![image](https://user-images.githubusercontent.com/87273590/154712271-d66168ee-efcf-4edd-b1ec-9240fd920196.png)
### ![image](https://user-images.githubusercontent.com/87273590/154712663-a701158c-9f25-4ab5-a526-565921d68553.png)
### 그리고 총알 방향이 있겠죠. 방향이.
### ![image](https://user-images.githubusercontent.com/87273590/154712711-cef41110-fdab-400d-b21c-c50826e12243.png)
### 당연히 y값에다가 이제 좌표값을 올려야 겠습니다. 속도는 200.f할겁니다
### ![image](https://user-images.githubusercontent.com/87273590/154713322-9a781dad-bea0-48ea-9a5d-a46a43f560bd.png)
### 위로 할지, 아래로 할지는 이 함수를 통해 결정하겠습니다
### 이 미사일은 플레이어가 특정 키를 누를떄 발사돼야 합니다. 그럼으로 플레이어 코드로 이동하겠습니다.
### ![image](https://user-images.githubusercontent.com/87273590/154713735-847157db-8c73-419a-ad98-cebc3bbb4c47.png)
### ![image](https://user-images.githubusercontent.com/87273590/154713863-b8b49dad-0e56-4a8d-8212-f84e0fd9e132.png)
### ![image](https://user-images.githubusercontent.com/87273590/154713937-9527e565-82a1-4c3c-88ab-696eda6f0b37.png)
### 여기에다가 구현하겠습니다
### ![image](https://user-images.githubusercontent.com/87273590/154714352-fe596308-829b-4f20-9297-ae530397d6d2.png)
### 미사일이 제 캐릭터 정중앙에서 나오면 안되겠죠
### ![image](https://user-images.githubusercontent.com/87273590/154714572-b040a475-a7bd-4e69-a850-14e43ef30950.png)
### 기본적인 세팅은 끝났습니다.
### 이걸 보여주려면 현재 씬에다가 오브젝트를 추가해줘야 겠죠?
### 씬을 얻어와야 하는데 못하니까,,만들죠
### ![image](https://user-images.githubusercontent.com/87273590/154715966-28422001-8744-45f1-bcfa-e1c3c764539b.png)
### ![image](https://user-images.githubusercontent.com/87273590/154716254-47864c3a-6621-4fc4-8414-4488364c9a62.png)
### protected되어 있어서, 못 받아옵니다. 일단은 그냥 public으로 고친 후 다시 불러오면
### ![image](https://user-images.githubusercontent.com/87273590/154716700-67e1e0f6-ed3c-456b-a8d6-f5bbc21241ba.png)
### 근데 총알이 사각형보단, 원이 더 이쁘고 더 알맞다고 볼 수 있겠습니다
### ![image](https://user-images.githubusercontent.com/87273590/154716939-19c06285-0b3f-4b23-bd22-1585d51f0ccc.png)
### 이렇게 되면 미사일만 동그라미가 되는게 아니라, 적도 동그라미가 되어 버립니다.
### ![image](https://user-images.githubusercontent.com/87273590/154717090-1bcc12b8-bfb2-4013-9eac-709382857e97.png)
### 그럼 미사일 오브젝트에서 랜더링을 오버라이딩 받아야 겠죠
### ![image](https://user-images.githubusercontent.com/87273590/154717312-7e6bbc3e-51d3-45fc-8e23-3ecf065e6aeb.png)
### 이제 저희가 원하는대로 나올겁니다
### 
