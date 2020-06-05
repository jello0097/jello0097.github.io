---
title: "[github] readme.md에 이미지 첨부하기"
toc: true
toc_sticky: true
description: |-
  github의 README.md 작성 시
  이미지 리소스를 따로 git에 추가하지 않고 이미지 파일을 첨부하는 방법이다.
categories:
- github
- devops
tags:
- github
- devops
---

사전에 개인 github의 repository가 생성되어 있어야 한다. 

* * *

### 1. `repository > issues` 페이지 진입  
 ![iusse-page](https://user-images.githubusercontent.com/24672300/83899185-f4a8fa00-a792-11ea-9dbe-1878cda710b4.png)

### 2. New Iusse 버튼 클릭하기 
좌측에 위치함 -> ![newissue](https://user-images.githubusercontent.com/24672300/83899147-e6f37480-a792-11ea-8f29-64968a47b026.png) 

### 3.` Leave a comment` 란에 이미지를 파일을 Drag and Drop 하기 
![스크린샷 2020-06-06 오전 12 11 21](https://user-images.githubusercontent.com/24672300/83895170-4c446700-a78d-11ea-869a-b9dc31bc2b72.png)

* 이미지를 Drag and Drop 하면 이미지 업로드 진행중 표시
```markdown
[Uploading shop.png…]()
``` 
* 이미지 업로드 완료 후** url 생성 시 아래처럼 변경
```markdown
![shop](https://user-images.githubusercontent.com/24672300/83892813-249fcf80-a78a-11ea-9169-53b21bf87b64.png)
```

### 4. `README.md`에 이미지 삽입
생성된 이미지 url을 이용하여 `README.md`에 이미지 삽입함 

![스크린샷 2020-06-06 오전 1 22 11](https://user-images.githubusercontent.com/24672300/83899912-2d959e80-a794-11ea-9e81-29bc6f965841.png)

#### 원본 사이즈로 업로드하는 경우  
`생성된 url`을 붙여넣기를 통한 이미지 삽입 
```markdown
![shop](https://user-images.githubusercontent.com/24672300/83892813-249fcf80-a78a-11ea-9169-53b21bf87b64.png)
```

![shop](https://user-images.githubusercontent.com/24672300/83892813-249fcf80-a78a-11ea-9169-53b21bf87b64.png)
#### 이미지의 사이즈 변경이 필요한 경우 
`<img>` 태그를 이용하여 이미지 삽입 
```markdown
<img src="https://user-images.githubusercontent.com/24672300/83892813-249fcf80-a78a-11ea-9169-53b21bf87b64.png" width="40%" height="30%" title="px(픽셀) 크기 설정" alt="shop"/>
```

<img src="https://user-images.githubusercontent.com/24672300/83892813-249fcf80-a78a-11ea-9169-53b21bf87b64.png" width="40%" height="30%" title="px(픽셀) 크기 설정" alt="shop"/>
### 5. README.md에 이미지 넣기 완료 
![스크린샷 2020-06-06 오전 1 23 02](https://user-images.githubusercontent.com/24672300/83900009-587ff280-a794-11ea-8ab4-f9ede7cfc745.png)
