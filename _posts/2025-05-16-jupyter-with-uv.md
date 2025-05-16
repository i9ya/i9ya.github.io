---
layout: single 
title: "Jupyter 노트북과 UV를 함께 사용하는 효율적인 방법" 
---

# Jupyter 노트북과 UV를 함께 사용하는 효율적인 방법

Jupyter 노트북을 여러 Python 프로젝트에서 사용할 때, 매번 가상환경마다 Jupyter를 설치하는 번거로움을 겪으셨나요?  
이번 포스트에서는 **UV**와 **Jupyter**를 효율적으로 연동하는 방법을 소개합니다.  
이 방법을 활용하면 가상환경은 깔끔하게 유지하면서도, 프로젝트별로 독립적인 Jupyter 환경을 사용할 수 있습니다.

---

## UV와 Jupyter, 왜 함께 사용할까?

- **가상환경마다 Jupyter를 중복 설치할 필요 없음**  
  Jupyter를 한 번만 설치하고, 각 프로젝트의 가상환경에서 해당 환경을 인식하도록 커널만 등록하면 됩니다.
- **가상환경이 더 가볍고 관리가 쉬워짐**  
  불필요한 패키지 설치 없이, 필요한 라이브러리만 포함된 환경을 유지할 수 있습니다.
- **프로젝트별 의존성 충돌 방지**  
  각 프로젝트는 자신만의 패키지와 설정을 유지하면서, Jupyter 노트북 작업도 자유롭게 할 수 있습니다.

---

## 실전 적용 방법

### 1. Jupyter를 전역(혹은 별도의 환경)에 설치

Jupyter는 한 번만 설치하면 됩니다.

```bash
uv pip install jupyterlab
```

---

### 2. 프로젝트 가상환경 생성 및 필요한 패키지 설치

`uv`로 가상환경을 만들고, 프로젝트에 필요한 패키지만 설치합니다.
```bash
uv venv --seed
uv pip install numpy pandas matplotlib
```

---

### 3. ipykernel 설치 및 커널 등록

`ipykernel`을 프로젝트 가상환경에 설치한 뒤, 커널을 등록하면 Jupyter에서 해당 가상환경을 선택할 수 있습니다.
```bash
uv pip install ipykernel
uv run python -m ipykernel install --user --name=프로젝트이름
```

---

### 4. Jupyter Lab/Notebook 실행

이제 Jupyter를 실행하면, 등록한 커널(프로젝트 환경)을 선택해 작업할 수 있습니다.
```bash
jupyter lab
```

---

## 요약 및 장점

- Jupyter를 한 번만 설치해도, 여러 프로젝트의 가상환경을 독립적으로 관리할 수 있습니다.
- 커널 등록만으로 각 프로젝트의 패키지 환경을 그대로 사용할 수 있습니다.
- **uv**를 활용하면 가상환경 생성과 패키지 설치가 훨씬 빠르고 간편해집니다.

---

**참고:**  
원문: [Using UV with Jupyter Notebooks by Alan Jones](https://medium.com/@alan-jones/using-uv-with-jupyter-notebooks-56d964244d6e)
