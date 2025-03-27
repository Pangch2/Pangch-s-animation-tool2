# Pangch-s-animation-tool2
팽치류2 소스임

팽치류에서 BDE파일을 사용하기 위해서는
파일이름 f(숫자)
가 필요합니다(필수임)

f1 f2 f3이런식으로 매 프레임마다 저장을 해줘야 하는데
여기서 이런 질문이 올 수도 있겠죠?
Q : f1 f10 f20 f23 f29순서로 있어도 애니메이션은 정상적으로 생성되나요? 
A : 네 잘 생성됩니다 
하지만 f1에서f10 이 된다 하여도 중간을 건너뛰는것이 아닌 f1  f2  f3  f4  f5판정으로 생성됩니다

Chapter.3
애니메이션을 뽑아내봅시다
프레임을 다 만들었으면, 애니메이션으로 동작할 수 있도록 만들어 봅시다
팽치따띠온~
작성자


폴더 하나를 생성 후 그 안에 팽치류를 넣어준 다음 한번 실행해줍니다


result폴더
frame.txt
setting.txt
가 생성 되는데요
이미지
이것들의 기능은 중요한 순서대로 설명드리겠습니다 
가장 중요한 setting.txt에는
생성모드 :1
임시플레이어(선택) :
스코어 이름(선택) :
기본 보간값(선택) :
기본 스코어증가값(기본값 1) :
시작 스코어 값(선택) :1
네임스페이스 :
score저장이름(기본값frame) :
frame저장위치(선택) :
score저장위치(선택) :
기본적으로 이렇게 작성 되어있는데
생성모드 :1 아니면 0 입력이 가능합니다
1의 기능 : 오직 한 모델에만 애니메이션을 적용할 수 있도록 생성합니다.(UUID는 생성모드가 0이더라도 1상태로 생성되어집니다)
0의 기능 : 한 모델이 여럿 존재하더라도 각기 다른 타이밍이나 다른 애니메이션을 적용할 수 있도록 생성합니다. 
임시플레이어(선택) :원하시는 이름 작성하시면 됩니다
스코어보드의 players위치에 넣어지는 값입니다(생성모드 :0일떄는 @s로 변경하셔야 합니다) 

스코어 이름(선택) :현재 생성되어 있는 스코어보드의 이름을 넣으셔야 합니다.
스코어보드의 objectives위치에 넣어져있는 값입니다 

기본 보간값(선택) :원하시는 숫자 넣으시면 됩니다(마크의 최대값 99)
작성하지 않을시 start_interpolation , interpolation_duration 를 생성하지 않습니다 
기본 스코어증가값(기본값 1) :원하시는 숫자 넣으시면 됩니다
작성하지 않을시 스코어보드가 1씩 증가합니다
시작 스코어 값(선택) :원하시는 숫자 넣으시면 됩니다
가장 먼저 있는 프레임의 스코어를 설정합니다. 

네임스페이스 : 데이터 팩에서 어떤 파일을 실행할 때 어디에서 불러와야 하는지 지정해 줍니다
예시 : pending:pend4/가 입력된 상태라면 
function pending:pend4/f5 가 출력됩니다 
score저장이름(기본값frame) :원하시는 이름 넣으시면 됩니다
스코어를 저장하는 mcfunction의 이름을 지정할 수 있습니다.
frame저장위치(선택) :원하시는 경로 입력하시면 됩니다(만약 입력이 안되어 있다 해도 reuslt폴더안에 저장됩니다)
data merge entity~ 가 작성되어있는 파일을 저장할 위치를 지정합니다
지정 예시 : C:\PrismLauncher-Windows-MinGW-w64-Portable-8.4\instances\1.21.4.minecraft\saves발렌타인\datapacks\planetpangch\data\planetpangch\function\planetpangch
팽치류에는 실행마다 이 폴더에 있는 f(숫자).mcfunction을 제거하고 다시 생성합니다. 다른 애니메이션 .mcfunction이 사라질 수도 있으니 명심하세요. 

score저장위치(선택) :원하시는 경로 입력하시면 됩니다(만약 입력이 안되어 있다 해도 reuslt폴더안에 저장됩니다)
execute if score ~ run function 네임스페이스/f(숫자) 가 작성되어있는 파일을 저장할 위치를 지정합니다
지정 예시 : C:\PrismLauncher-Windows-MinGW-w64-Portable-8.4\instances\1.21.4.minecraft\saves발렌타인\datapacks\planetpangch\data\planetpangch\function\planetpangch
팽치류에는 실행마다 이 폴더에 있는 score저장이름(기본값frame).mcfunction을 제거하고 다시 생성합니다. 다른 애니메이션 .mcfunction이 사라질 수도 있으니 명심하세요. 
ㅤ
ㅤ
자 이제 frame.txt에 대해 설명하겠습니다 
frame.txt에서는 기본 보간값이나 기본 스코어 증가값 외에도 원하는 보간값과 스코어 증가값을 설정할 수 있습니다.
작성방법
f숫자 i숫자 s숫자
i값이나 s값이 없을경우에는 setting.txt에 있는 기본값을 불러옵니다 

ㅤ
ㅤ
자 이제 result폴더에 대해 설명드리겠습니다
setting.txt에 frame저장위치 , score저장위치 가 작성되어있지 않다면 .mcfunction파일을 result폴더에 저장시킵니다
Chapter.4
마크로 애니메이션 불러오기
모델 소환은 알아서 하시고
(score저장위치)에 저장된 score저장이름(기본값frame).mcfunction을 tick.json이나 반복형 커맨드 블록에 넣어 반복시키고 
스코어를 증가시키는 커맨드를 넣어두면 애니메이션이 출력됩니다
끝
