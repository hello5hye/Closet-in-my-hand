# project_closet
앱으로 나만의 옷장을 관리하고 날씨에 따라 사용자가 가지고 있는 옷을 활용해 추천해주는 기능

### 1.1 프로젝트 목적
매일 아침 오늘 기온에는 어떤 종류의 옷을 입어야 할까 고민하는 사람들에게 정보를 제공하기 위한 어플리케이션이다.

### 1.2 프로젝트 추진 배경
다수의 사람들은 외출 시 실시간으로 제공되는 날씨 정보를 참고하여 입고 나갈 옷을 선택한다. 그러나 날씨에 관한 정보만을 이용하여 옷을 입고 나가기에는 사람마다 다르게 느끼는 체감 온도로 인하여 어려움이 존재한다. 이러한 어려움을 해결하기 위하여 날씨 정보에 따른 옷 종류 추천 시스템과 사용자 맞춤형 스마트 옷장 기능을 제공하고자 한다.

### 1.3 프로젝트 기능
- **날씨를 알려주는 기능**<br>가장 기본 기능으로 날씨 정보를 제공한다.
- **나만의 옷장 기능**<br>현재 내가 가지고 있는 옷들을 사진으로 찍어 등록하여 나만의 옷장이 생성된다.
- **온도에 걸맞는 사용자 옷 추천** <br>날씨에 적합한 옷의 종류를 추천. 처음은 통계청 기준으로 잡고 추천되도록 한다.
- **사용자만의 기준을 통해 조정되는 추천 옷**<br>추천한 옷에 대한 사용자 평가를 통해 사용자가 불만족스러웠을 때 카테고리별로 설정을 하면 똑같은 온도일때는 기존에 추천했던 옷이 아닌 사용자 평가를 반영하여 조금 더 사용자에게 맞추어진 옷 추천을 제공한다.

### 2.1 시스템 구성
<img width="413" alt="image" src="https://github.com/hello5hye/Closet-in-my-hand/assets/139055996/16ec5aff-39fb-446d-8e9c-5c4c0dc9c415">

<br/>
<br/>

#### 기능적 요구사항, 비기능적 요구사항 등 생략

<br/>


### 3.1 시스템 설계
<img width="435" alt="image" src="https://user-images.githubusercontent.com/90433342/220085122-d1c396a5-8020-4544-b6d0-e362fa7053b4.png">

### 데이터베이스 구조
<img width="419" alt="image" src="https://user-images.githubusercontent.com/90433342/220085181-f41cc10d-b750-4611-852d-8688fc28571f.png">
- 파이어베이스 사용

[^1]: - 파이어베이스는 2011년 파이어베이스사가 개발하고, 2014년 구글에 인수된 모바일 웹 애플리케이션 개발 플랫폼이며, 구글 에널리틱스와 구글 패브릭에서 제공하는 기능들을 포함한 다양한 기능들을 제공한다.

[^1]: - SQL 형식이 아니라 NoSQL 형식의 DB이다. 실시간 데이터베이스는 구글 클라우드에 호스팅된 데이터베이스로써 데이터들이 JSON 형태로 저장된다. 저장된 데이터들을 불러올 때는 JSON 형태로 불러오는 것이 아니라 DataSnapshot 객체 형태로 가져오게 된다. 그래서 기존에 사용하던 방법(JSON 형태의 데이터를 가져와 사용하던 DB)과는 조금 다른 방식으로 데이터베이스를 사용해야 한다.



### 사용자 맞춤화 알고리즘
<img width="612" alt="image" src="https://user-images.githubusercontent.com/90433342/220088237-50dcdd46-723d-415c-be30-328a6bc5a219.png">

### 시스템 구현 (화면 이미지)
<img width="579" alt="image" src="https://user-images.githubusercontent.com/90433342/220088370-c8fff3c4-6258-4383-ad54-2564c3da7db8.png">
<img width="581" alt="image" src="https://user-images.githubusercontent.com/90433342/220088887-e3725f74-6357-4ff6-a008-3d16066768e0.png">
<img width="281" alt="image" src="https://user-images.githubusercontent.com/90433342/220090634-3d47453f-0ede-4a59-bcb1-7b38968f1a74.png">

···

### 문제 및 해결과정
- 옷장을 불러오는 리스트 화면(RecyclerView)에서개별적으로 추천 스티커를 붙이려 했으나, 문제가 해결되지 않음. 다른 방안으로 추천된 옷장만 선별될 수 있도록 Activity 클래스를 다시 추가하여 새로운 화면페이지에 DB를 불러오도록 변경
- 날씨 데이터가 소수점이 붙은 string으로 저장되어 추천 설정을 위해 숫자로 형변환을 진행. 하지만 이진법으로 변환되어 정확하지 않고 오차 발생. 길어진 숫자를 자르기 위해 반올림 형태로 바꾸어 저장하고, 사용자 맞춤화 부분에 적용.
- ···
