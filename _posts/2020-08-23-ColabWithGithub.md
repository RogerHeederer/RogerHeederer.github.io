---
title : "Import image from Colab to Github"
tag : 
 - Colab
 - Github
 - Image import
 - ipynb
---

## Colab Image Upload Setting ##

이번 포스팅에서는 Colab에서 이미지 세팅하는 방법에 대해 포스팅하고자 합니다. 저는 머신러닝 코드 리뷰를 주로 구글에서 제공하는 Colab에서 진행하는데요, Colab을 통해 작성한 ipynb 파일을 바로 깃허브로 commit합니다.

근데 여기서 문제는 Colab에서 이미지 첨부를 하였는데, 해당 이미지가 github에서는 보이지 않는 문제가 있습니다. 우선 제가 처음에 Colab에서 이미지를 넣은 방법부터 살펴보겠습니다.<br/>

![image](/assets/img/2020-08-23_ColabImageUpload.png)
![image](/assets/img/2020-08-23_ColabImageUpload2.png)

위 그림처럼 Colab은 이미지를 업로드 할 수 있는 UI를 제공합니다. 저는 처음에 이 아이콘을 통해 업로드를 하였으며, Colab에서 문제없이 작동하는 것을 확인한 후 Github로 커밋하였습니다. 하지만 위 방법으로는 깃허브에서 이미지를 표시할 수 없습니다.

그래서 다음과 같은 방법을 소개해드리겠습니다. 뭐 깃허브에서 이미지를 직접 업로드하는 방법도 있을테고, 여러가지가 있겠지만 저는 Colab과 Github의 연동성을 가장 중요시 생각합니다. 즉 서로의 데이터 상태가 일관성을 가지고 연동되어 있는 상태를 추구합니다.

1. 구글드라이버에 원하는 이미지를 업로드한다.
2. 업로드한 이미지를 우클릭하여 공유가능한 링크 가져오기를 클릭
3. 권한을 링크가 있는 모든 사용자에게 공개로 변환(정보 공유의 목적이니까요!)
4. 저의 예시 링크는 다음과 같습니다.
https://drive.google.com/file/d/1XFzIyYYhWyUV3dFUspDn4dB9v5LcpDEj/view?usp=sharing
5. 여기서 img id를 가져옵니다. 1XFzIyYYhWyUV3dFUspDn4dB9v5LcpDEj 이게 이미지 아이디입니다.
6. https://drive.google.com/uc?export=view&id=이미지아이디
7. Colab으로 돌아가 html 문법으로 해당 링크를 걸어줍니다.<br/>

예시) img src='https://drive.google.com/uc?export=view&id=1iPT0REq-6ZIAqWPQ9hvukCcmteZjPHqW' align="left"

마크다운 이미지 삽입 문법으로 사용해도 됩니다.