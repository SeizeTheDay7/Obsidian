- [[#ChatGPT 북마크|ChatGPT 북마크]]
- [[#윈도우 단축키|윈도우 단축키]]
- [[#파일 경로 표기법|파일 경로 표기법]]
- [[#Github Copilot|Github Copilot]]
	- [[#Github Copilot#단축키|단축키]]
	- [[#Github Copilot#명령어|명령어]]
- [[#옵시디언|옵시디언]]


Ctrl+D : 한 줄 전부 삭제

## Youtube Download.py
---

### mp3
```python
import yt_dlp

playlist_url = 'https://www.youtube.com/playlist?list=PLQjAgLjV4MYasYxTdq1JuCGC1Dj--Hteb&si=HYdhUV8316Qb7NLc'

ydl_opts = {
    'format': 'bestaudio/best',
    'ffmpeg_location': r'C:\Users\bioma\Documents\ffmpeg\bin',
    'outtmpl': 'downloads/%(title)s.%(ext)s',
    'writethumbnail': True, 
    'postprocessors': [
        {
            'key': 'FFmpegExtractAudio',
            'preferredcodec': 'mp3',
            'preferredquality': '192',
        },
        {
            'key': 'EmbedThumbnail',
            'already_have_thumbnail': False,
        },
        {
            'key': 'FFmpegMetadata',
        }
    ]
}

with yt_dlp.YoutubeDL(ydl_opts) as ydl:
    ydl.download([playlist_url])
```

### mp4
```python
import yt_dlp

playlist_url = 'https://www.youtube.com/playlist?list=PLQjAgLjV4MYasYxTdq1JuCGC1Dj--Hteb&si=HYdhUV8316Qb7NLc'

ydl_opts = {
    'format': 'bestvideo[ext=mp4]+bestaudio[ext=m4a]/mp4',
    'ffmpeg_location': r'C:\Users\bioma\Documents\ffmpeg\bin',
    'outtmpl': 'downloads/%(title)s.%(ext)s',
    'merge_output_format': 'mp4',
    'postprocessors': [
        {
            'key': 'FFmpegMetadata',
        }
    ]
}

with yt_dlp.YoutubeDL(ydl_opts) as ydl:
    ydl.download([playlist_url])
```

## mhtml 이미지 추출
---
```python
import base64
from email import message_from_file
from pathlib import Path
from PIL import Image
from io import BytesIO

# 설정
source_dir = Path(r"C:\Users\bioma\Downloads\mhtmls")
output_root = Path(r"C:\Users\bioma\Downloads\extracted")
min_width = 500
min_height = 500
images_per_folder = 200

output_root.mkdir(parents=True, exist_ok=True)

# 전역 카운터
global_img_count = 1

# 수정 시간 기준 정렬 (오래된 순)
mhtml_files = sorted(source_dir.glob("*.mhtml"), key=lambda f: f.stat().st_mtime)

for mhtml_path in mhtml_files:
    print(f"처리 중: {mhtml_path.name}")
    try:
        with open(mhtml_path, 'r', encoding='utf-8', errors='ignore') as f:
            msg = message_from_file(f)
    except Exception as e:
        print(f"{mhtml_path.name} 열기 실패:", e)
        continue

    images = []

    for part in msg.walk():
        content_type = part.get_content_type()
        if content_type == "image/jpeg" and "base64" in str(part.get("Content-Transfer-Encoding")):
            try:
                payload = part.get_payload(decode=True)
                if not payload:
                    continue

                with Image.open(BytesIO(payload)) as img:
                    width, height = img.size
                    if width >= min_width and height >= min_height:
                        images.append(img.copy())
            except Exception as e:
                print(f"{mhtml_path.name} 이미지 처리 오류:", e)

    # 역순 저장
    for img in reversed(images):
        # 폴더 이름 계산
        folder_start = ((global_img_count - 1) // images_per_folder) * images_per_folder + 1
        folder_end = folder_start + images_per_folder - 1
        folder_name = f"{folder_start}-{folder_end}"

        folder_path = output_root / folder_name
        folder_path.mkdir(parents=True, exist_ok=True)

        # 파일 저장
        output_file = folder_path / f"{global_img_count}.webp"
        img.save(output_file, "WEBP")
        print(f"{output_file} 저장됨")

        global_img_count += 1

print("모든 이미지 추출 및 저장 완료.")
```


## 윈도우 단축키
---

Ctrl+Shift+V : 서식 없이 붙여넣기
win+D : 바탕화면 바로가기
win+방향키 : 화면 절반으로 정리
Shift+Ins : 붙여넣기


## 파일 경로 표기법
---

**.** : 현재 웹페이지가 소속된 폴더
**..** : 현재 웹페이지의 부모 폴더


## Github Copilot
---

### 단축키
- `Ctrl + I` : 명령 내리기
- `Ctrl + 우측 방향키` : 단어 단위 선택
- `Alt + [, ]` : 코드 추천 고르기
- `Ctrl + Enter` : 한 번에 제안 확인

| 명령어              | Keybinding   |
| ---------------- | ------------ |
| Copilot 활성화/비활성화 | Shift + Q    |
| 설명 요청            | Shift + E    |
| 고치기 요청           | Shift + F    |
| 테스트 생성           | Shift + T    |
| 코드 생성            | Shift + G    |
| 다음 제안으로          | Shift + D    |
| 이전 제안으로          | Shift + A    |
| 제안 전체 보기         | Ctrl + Enter |
| 인라인 제안 생성        | Shift + V    |

### 명령어
- `@workspace /explain` : 이 코드가 어떻게 작동하는지 설명
- 그냥 코드 긁고 `/explain` : 해당 코드 설명
- `@workspace /new` : 새로운 프로젝트를 위해 폴더, 파일 생성
- `/doc` : 설명문 주석으로 달아줌
- `/fix` : 버그 해결책 제안해줌




