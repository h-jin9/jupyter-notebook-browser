## 주피터 노트북 - 브라우저가 자동으로 실행되지 않는 경우

해당 문서는 Windows 7 OS 기준입니다. 우선 기본적으로 아나콘다를 통하여 파일을 모두 설치 완료하고 환경 변수 설정까지 완료하였는데 주피터 노트북 실행 시 서버는 실행되지만 브라우저가 자동으로 실행되지 않는 경우의 해결 방법입니다. 

### 1. jupyter_notebook_config.py 파일 생성하기

프로그램 및 파일 검색에서 `cmd.exe` 혹은 `명령 프롬프트`라고 검색한 후에 검은 색 창을 실행합니다.

![1](https://raw.githubusercontent.com/h-jin9/jupyter-notebook-browser/master/1.jpg)

위와 같은 창이 나타나면 해당 창에 아래와 같은 문구를 입력한 후 엔터키를 눌러 해당 문구를 실행합니다.

```
jupyter notebook --generate-config
```

![3](https://raw.githubusercontent.com/h-jin9/jupyter-notebook-browser/master/3.jpg)

잘 실행되었다면 위와 같이 결과가 나타나고 `.jupyter` 폴더 안에 `jupyter_notebook_config.py` 파일이 생성됩니다. `.jupyter` 폴더는 보통 위의 결과와 같이 `C:/Users/{계정명}/.jupyter`와 같은 경로에 위치합니다. 

![4](https://raw.githubusercontent.com/h-jin9/jupyter-notebook-browser/master/4.jpg)



### 2. jupyter_notebook_config.py 파일 수정하기

`.jupyter` 폴더 안의 `jupyter_notebook_config.py`을 찾아 메모장으로 파일을 엽니다. 메모장을 먼저 실행한 후 **파일 > 열기** 클릭 후 **모든 파일**로 변경한 후에 해당 파일을 열거나 **<u>빈 메모장에 해당 파일을 드래그</u>**하는 방식으로 파일을 수정할 수 있습니다. 

#### 2.1 c.NotebookApp.Browser 수정

`Ctrl + f`를 이용하여 `# c.NotebookApp.browser = '/'`를 찾아 `c.NotebookApp.browser = '{chrome.exe가 위치한 경로}/chrome.exe %s'`로 수정합니다.  `chrome.exe`가 위치한 경로는 프로그램 및 파일 검색에서`chrome.exe`를 검색하여 우클릭 후 해당 파일이 위치한 폴더를 연 후 해당 폴더의 경로를 입력해주면 됩니다. 기본 설정대로 설치하였다면 보통 아래의 위치와 같습니다.

```
c.NotebookApp.browser = 'C:/Program Files (x86)/Google/Chrome/Application/chrome.exe %s'
```

![5](https://raw.githubusercontent.com/h-jin9/jupyter-notebook-browser/master/5.jpg)

![6](https://raw.githubusercontent.com/h-jin9/jupyter-notebook-browser/master/6.jpg)

인터넷 익스플로러로 주피터 노트북을 실행하고 싶다면 인터넷 익스플로러 실행 파일인 `iexplore.exe`가 위치한 경로로 설정하는 것도 가능하지만 주피터 노트북이 크롬에 더 최적화되어있어 인터넷 익스플로러 상에서는 오류가 잦으니 크롬이 없으시더라도 설치하신 후에 크롬 브라우저에서 진행하는 것을 추천드립니다.

#### 2.2 c.NotebookApp.open_browser 변경

`#c.NotebookApp.open_browser = True`를 `c.NotebookApp.open_browser = True`로 수정합니다. 

`Ctrl + S`를 통하여 파일을 저장한 후 파일을 닫아줍니다. 


### 3. 주피터 노트북 실행

`Jupyter Notebook (Anaconda3)` 파일을 실행하시거나 `cmd.exe`에서 jupyter notebook을 입력하여 주피터 노트북을 실행합니다. 브라우저가 자동으로 실행되는 것을 확인합니다.
