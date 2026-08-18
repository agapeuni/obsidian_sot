---
title: Easy Diffusion - Linux 버전 설치, 기본적인 환경설정
type: blog-archive
status: active
created: '2026-05-09'
updated: '2026-08-16'
published: '2026-05-09T11:31:30+09:00'
source: https://agapeuni.tistory.com/809
source_blog: agapeuni.tistory.com
post_id: 809
category: 🎨 이미지 생성 AI/Easy Diffusion
tags:
- AI이미지생성도구
- EasyDiffusion리눅스설치
- EasyDiffusion모델적용방법
- EasyDiffusion사용법
- EasyDiffusion설치방법
- EasyDiffusion시스템요구사항
- EasyDiffusion환경설정
- HuggingFace모델다운로드
- StableDiffusion로컬설치
- StableDiffusion프롬프트가이드
body_hash: 372df2054aefe8b60188ea6573549a050ddec3ebf29ac1eccd571eea3b9282b3
visibility: private
rag: exclude
---

# Easy Diffusion - Linux 버전 설치, 기본적인 환경설정

- 원문: https://agapeuni.tistory.com/809
- 게시일: 2026-05-09T11:31:30+09:00
- 분류: 🎨 이미지 생성 AI/Easy Diffusion

## 본문

![[03 Attachments/티스토리 Vento AI Lab/809/809-001-img1.daumcdn.png]]

## 1. Easy Diffusion 개요

Easy Diffusion은 고품질의 AI 생성 이미지를 만들기 위해 확산 모델(diffusion model)을 사용하는 오픈소스 도구이다. 이 도구는 로컬 또는 클라우드에서 쉽게 실행할 수 있도록 설계되어 개발자들도 쉽게 접근할 수 있다. 이미지 생성, 이미지 편집, 스타일 전환 등의 다양한 작업을 지원하며, 스타일, 프롬프트, 출력 해상도 등을 조정하여 사용자가 원하는 이미지를 맞춤 제작할 수 있는 기능을 제공한다.

## 2. Easy Diffusion 특징

**1) 사용자 친화적인 인터페이스**

복잡한 AI 모델을 쉽게 사용할 수 있도록 직관적이고 간단한 UI를 제공하여 초보자도 쉽게 이미지를 생성하고 편집할 수 있다.

**2) 다양한 모델 지원**

여러 가지 확산 모델(diffusion model)을 지원하여, 사용자가 원하는 스타일이나 목적에 맞는 모델을 선택할 수 있다.

**3) 로컬 및 클라우드 실행**

Easy Diffusion은 로컬 PC에서 실행할 수 있으며, 클라우드에서의 실행도 가능해 성능이나 환경에 구애받지 않고 사용할 수 있다.

**4) 이미지 생성 및 편집**

단순히 이미지를 생성하는 것뿐만 아니라, 이미지를 편집하고, 스타일 전환을 할 수 있어 창의적인 작업에 적합하다.

**5) 프롬프트 기반 생성**

텍스트 프롬프트를 입력하면 해당 설명에 맞는 이미지를 생성해 주는 기능이 있어, 아이디어를 빠르게 시각화할 수 있다.

**6) 고해상도 출력**

고품질의 이미지를 생성할 수 있으며, 출력 해상도를 사용자가 설정할 수 있어 다양한 용도로 활용 가능하다.

**7) 오픈소스**

누구나 무료로 사용할 수 있으며, GitHub 등을 통해 코드와 기능을 수정하거나 개선할 수 있다.

## 3. 하드웨어 요구 사항

NVIDIA 그래픽 카드 (최소 2GB RAM) 또는 CPU에서 실행할 수 있다. CPU로 실행이 가능하지만 GPU로 실행하는 것이 성능이 좋다. 최소 8GB의 시스템 RAM이 필요하고 하드 디스크에 최소 25GB의 공간이 있어야 한다. 여러가지 모델을 적용하는 경우에는 보다 많은 공간을 필요로 한다.

필요한 시스템 자원은 다음과 같다.

- 시스템 메모리(RAM) 최소 8GB 이상

- 하드디스크 여유 공간 최소 25GB 이상

## 4. Easy Diffusion 설치

[https://github.com/cmdr2/](https://github.com/cmdr2/)

다음의 명령어로 Easy-Diffusion-Linux.zip 파일을 내려받는다.

$ wget [https://github.com/cmdr2/stable-diffusion-ui/releases/latest/download/Easy-Diffusion-Linux.zip](https://github.com/cmdr2/stable-diffusion-ui/releases/latest/download/Easy-Diffusion-Linux.zip)

```
$ wget https://github.com/cmdr2/stable-diffusion-ui/releases/latest/download/Easy-Diffusion-Linux.zip
--2024-10-03 01:16:49--  https://github.com/cmdr2/stable-diffusion-ui/releases/latest/download/Easy-Diffusion-Linux.zip
Resolving github.com (github.com)... 20.200.245.247
Connecting to github.com (github.com)|20.200.245.247|:443... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: https://github.com/easydiffusion/easydiffusion/releases/latest/download/Easy-Diffusion-Linux.zip [following]
--2024-10-03 01:16:50--  https://github.com/easydiffusion/easydiffusion/releases/latest/download/Easy-Diffusion-Linux.zip
Reusing existing connection to github.com:443.
HTTP request sent, awaiting response... 302 Found
Location: https://github.com/easydiffusion/easydiffusion/releases/download/v3.0.9/Easy-Diffusion-Linux.zip [following]
--2024-10-03 01:16:50--  https://github.com/easydiffusion/easydiffusion/releases/download/v3.0.9/Easy-Diffusion-Linux.zip
Reusing existing connection to github.com:443.
HTTP request sent, awaiting response... 302 Found
Location: https://objects.githubusercontent.com/github-production-release-asset-2e65be/528152092/9dd3b42c-cb2b-483b-8aa2-079bc37a6412?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=releaseassetproduction%2F20241002%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20241002T161650Z&X-Amz-Expires=300&X-Amz-Signature=c5ab9b2143e42e09ed38e546bfa130e19e44d13774c45ca947e437c2537d8de1&X-Amz-SignedHeaders=host&response-content-disposition=attachment%3B%20filename%3DEasy-Diffusion-Linux.zip&response-content-type=application%2Foctet-stream [following]
--2024-10-03 01:16:50--  https://objects.githubusercontent.com/github-production-release-asset-2e65be/528152092/9dd3b42c-cb2b-483b-8aa2-079bc37a6412?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=releaseassetproduction%2F20241002%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20241002T161650Z&X-Amz-Expires=300&X-Amz-Signature=c5ab9b2143e42e09ed38e546bfa130e19e44d13774c45ca947e437c2537d8de1&X-Amz-SignedHeaders=host&response-content-disposition=attachment%3B%20filename%3DEasy-Diffusion-Linux.zip&response-content-type=application%2Foctet-stream
Resolving objects.githubusercontent.com (objects.githubusercontent.com)... 185.199.108.133, 185.199.111.133, 185.199.110.133, ...
Connecting to objects.githubusercontent.com (objects.githubusercontent.com)|185.199.108.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 12925 (13K) [application/octet-stream]
Saving to: ‘Easy-Diffusion-Linux.zip’

Easy-Diffusion-Linux.zip      100%[==============================================>]  12.62K  --.-KB/s    in 0.002s
```

그리고 압축을 풀면 easy-diffusion 폴더와 파일이 생긴다.

$ unzip Easy-Diffusion-Linux.zip

```
Archive:  Easy-Diffusion-Linux.zip
   creating: easy-diffusion/
  inflating: easy-diffusion/CreativeML Open RAIL-M License
  inflating: easy-diffusion/How to install and run.txt
  inflating: easy-diffusion/start.sh
  inflating: easy-diffusion/LICENSE
   creating: easy-diffusion/scripts/
  inflating: easy-diffusion/scripts/install_status.txt
  inflating: easy-diffusion/scripts/functions.sh
  inflating: easy-diffusion/scripts/bootstrap.sh
  inflating: easy-diffusion/scripts/on_env_start.sh
```

easy-diffusion 디렉터리로 이동하고 "start.sh"을 실행한다.

처음 실행하면 많은 패키지 설치와 모델 다운로드로 시간이 좀 걸린다.

![[03 Attachments/티스토리 Vento AI Lab/809/809-002-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/809/809-003-img.png]]

## 5. 환경 설정

디폴트로 실행하면 http://localhost:9000으로 접근은 가능하다. 다른 장비나 외부에서 IP로 접속하려면 별도의 설정을 해줘야 한다. easy-diffusion 디렉터리 아래 config.yaml 파일을 생성하여 네트워크 설정을 한다. 참고로 scripts 디렉토리에 "config.yaml.sample" 파일이 있으니 복사해서 사용하면 편리하다.

```
GNU nano 7.2                                       config.yaml
# Change listen_port if port 9000 is already in use on your system
# Set listen_to_network to true to make Easy Diffusion accessibble on your local network
net:
  listen_port: 17850
  listen_to_network: true

# Multi GPU setup
render_devices: auto

# Set open_browser_on_start to false to disable opening a new browser tab on each restart
ui:
  open_browser_on_start: false

# set update_branch to main to use the stable version, or to beta to use the experimental
# beta version.
update_branch: main

# Advanced backend overrides (optional)
# These are applied at startup by `scripts/check_modules.py` and exported as environment variables.
#
# backend_config:
#   # Extra backend flags (example: cross-attention optimizations)
#   COMMANDLINE_ARGS: "--opt-split-attention"
#   # Force full precision (float32). Can help if you see corrupted/black outputs on some GPUs/backends.
#   FORCE_FULL_PRECISION: "1"
#
# Set force_save_path to enforce an auto save path. Clients will not be able to change or
# disable auto save when this option is set. Please adapt the path in the examples to your
# needs.
# Windows:
# force_save_path: C:\\Easy Diffusion Images\\
# Linux:
# force_save_path: /data/easy-diffusion-images/
force_save_path: /home/sgkim/Easy-Diffusion/output/
vram_usage_level: balanced

model:
  stable-diffusion: chilloutmix_NiPrunedFp32Fix
  vae: vae-ft-mse-840000-ema-pruned
```

## 6. Easy Diffusion 실행

먼저 Prompt와 Negative Prompt를 입력한다. 테스트를 위해 이전에 사용하던 프롬프트를 사용했다.

Image Settings에 값을 설정하고 "Make Images" 버튼을 클릭하여 이미지를 생성한다.

![[03 Attachments/티스토리 Vento AI Lab/809/809-004-img1.daumcdn.png]]

## 7. 다른 Model 적용

Easy Diffusion을 설치하면 sd-v1-4 모델을 기본적으로 사용할 수 있다. 허깅페이스에서 다른 모델을 내려받아 Easy Diffution에 적용해 보자. 허깅페이스에서 모델 메뉴를 클릭한다.

[https://huggingface.co/models](https://huggingface.co/models)

[Models – Hugging Face

Explore machine learning models.

huggingface.co](https://huggingface.co/models)

화면 좌측 Task에서 "Computer Vision >> Text-to-image"를 선택한다. 그러면 선택한 조건으로 필터되어 출력한다. 그리고 우측 상단에 Sorting을 "Most Likes"나 "Most Downloads"를 선택한다. 그러면 사람들이 많이 내려받은 모델들을 볼 수 있다.

![[03 Attachments/티스토리 Vento AI Lab/809/809-005-img1.daumcdn.png]]

제일 위에 표시되는 "stable-diffusion-v1-5/stable-diffusion-v1-5"을 선택하고 "Files" 탭을 클릭한다.

![[03 Attachments/티스토리 Vento AI Lab/809/809-006-img1.daumcdn.png]]

v1-5-pruned.safetensors 파일명에 마우스 우클릭을 하고 "링크 주소 복사"를 클릭하거나 v1-5-pruned.safetensors 파일 클릭한 뒤 "Copy download link"를 클릭하면 내려받기 주소가 복사된다.

![[03 Attachments/티스토리 Vento AI Lab/809/809-007-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/809/809-008-img.png]]

Easy Diffusion이 설치된 디렉토리에서 /models/stable-diffution 디렉토리로 이동한 뒤, 아래의 명령어로 모델을 내려받는다. 다른 곳에서 내려받았다면, "v1-5-pruned.safetensors" 파일을 /easy-diffusion/models/stable-diffusion 디렉터리에 옮긴다.

$ wget [https://h](https://huggingface.co/stable-diffusion-v1-5/stable-diffusion-v1-5/resolve/main/v1-5-pruned.safetensors)[uggingface.co/stable-diffusion-v1-5/stable-diffusion-v1-5/resolve/main/v1-5-pruned.safetensors](https://huggingface.co/stable-diffusion-v1-5/stable-diffusion-v1-5/resolve/main/v1-5-pruned.safetensors)

![[03 Attachments/티스토리 Vento AI Lab/809/809-009-img1.daumcdn.png]]

"Image Settings"의 Model 섹션에서 리프레시 버튼을 클릭하여 모델 목록을 새로 고치면 내려받은 모델을 사용할 수 있다.

![[03 Attachments/티스토리 Vento AI Lab/809/809-010-img1.daumcdn.png]]

![[03 Attachments/티스토리 Vento AI Lab/809/809-011-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/809/809-012-img.png]]

![[03 Attachments/티스토리 Vento AI Lab/809/809-013-주한길.png]]
