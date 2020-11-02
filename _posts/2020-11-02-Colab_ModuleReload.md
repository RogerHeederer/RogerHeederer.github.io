---
title : "파이썬 파일, 모듈을 다시 불러오기(Reload) in Colab"
tag : 
 - Colab
 - import from
 - module reload
 - python file reload
---

## How to reload modules in Colab ? ##

이번 포스팅에서는 colab에서 작업 중에 .py로부터 불러오는 모듈들을 reload하는 방법에 대해 포스팅 하겠습니다. 저 같은 경우는 언어 전처리를 위해 preprocess.py를 구현하고, colab의 .ipynb 파일에서 해당 .py 파일을 import 합니다. 

from preprocess import *

위 코드를 통해 preprocess.py를 colab 환경에서 가져다 쓸 수 있게 가져온 후 .py 파일 안에 있는 모듈(함수)들을 활용합니다. 이런 과정에서 .py의 오류를 수정해야 할 때도 있고, 내용을 수정해야 할 경우도 있는 등, 소스 변경을 해야할 경우가 생깁니다. 그래서 저는 google drive와 연결해서 바로 실행시킬 수 있는 text editor를 통해 바로 preprocess.py를 수정한 후 저장을 합니다.

여기서 문제가 나타납니다. colab에서 from preprocess import * 쉘을 다시 실행시켜도 수정된 사항이 반영이 되지 않습니다. 정확히 말하면, .py 파일을 열어보면 변경한 코드는 반영이 되어 있는데 실제 런타임중에는 변경한 내용이 반영이 되지 않은 채 이전과 같은 결과만을 리턴합니다.

비슷한 문제가 있는지 구글에 검색해 본 결과 이런 답변이 있었습니다.

I suspect what's happening is you have .py files stored in Google Drive, which you're importing in your notebook, and you want to see changes to the .py files reflected in your runtime, but they're not because python's import system is idempotent (an import statement is ignored if python thinks it's already loaded a module by that name, even if the underlying file has changed).

런 타임중에 변경된 .py의 내용들은 반영이 되지 않는다. python 파일이 이미 해당 이름으로 모듈을 로드했다고 생각하면 추가적으로 import를 재실행해도 파이썬 시스템이 무시한다라고 합니다.

위 문제를 해결하기 위해 스택 오버플로에서 제공하는 답변 중에는

from importlib import reload<br/>
reload(preprocess)

위와 같은 방식으로 해결이 된다고 하는데, 저는 잘 되지 않아 다른 방법을 찾았습니다.

![image](/assets/img/2020-11-02_reload.jpg)

위 사진처럼 두 쉘을 나눠서 실행시킵니다. 그리고 .py이 변경되었으면

%reload_ext autoreload<br/>
from preprocess import *

이 쉘을 실행시키면, 모듈의 변경된 사항이 런타임에서도 반영이 됩니다.