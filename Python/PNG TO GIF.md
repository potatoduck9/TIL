# 정적 이미지(PNG) -> 그래픽 포맷(GIF) 이미지 변환하기 
> 일반 사진을 움짤(?)로 바꾸는 코드를 작성해보자! <br>
> 사진 선정은 내가 정말 좋아하고 응원하는 축구 클럽 맨체스터 유나이티드의 현역 선수들의 사진을 선정하였다!👹👹 <br>

```python
import glob # glob은 사용자가 제시한 조건에 맞는 파일명을 리스트 형태로 반환한다.
from PIL import Image # PIL은 Python Image Library을 줄인 말이고 필로우(pillow)라고 불리며 이 라이브러리를 통해서 이미지를 처리할 수 있다.

# 이미지, 결과 생성 경로
image_in = "./project/images/*.png"
image_result = "./project/image_out/result.gif" 

# 첫 번째 이미지와 모든 이미지 리스트 팩킹 
img, *images = [Image.open(f).resize((320, 240), Image.ANTIALIAS) for f in sorted(glob.glob(image_in))] # resize(320,240) 사진 크기 

# 이미지 저장
img.save(fp = image_result,
         format = 'GIF'.
         append_images = images,
         save_all = True,
         duration = 500, # 다음 사진 나오는 시간 
         loop = 0
        )
```





                
