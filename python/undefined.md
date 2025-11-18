# 환경설정

## miniconda 운영설정

* 무료 저장소를 사용하기 위해 채널 변경 (default -> conda-forge)

```
conda config --show channels 
conda config --add channels conda-forge
conda config --set channel_priority strict
conda config --show channels
```

* conda 가상환경 설정

```
conda create -n pystudy_env python=3.13
conda info --envs  
conda activate pystudy_env 
```

## jupyter 설치

* conda 환경에서 간편히 python을 실행할 수 있는 jupyter 설치

```
pip install jupyter
```



## dotenv

```
pip install python-dotenv
```



## request

```
pip install request
```



## mysql connector

```
pip install mysql-connector-python
```



## Static scraping - beautifulsoup4

```python
pip install beautifulsoup4
```



## Dynamic scraping - selenium

```
pip install selenium
```

## Data Analysis

```
pip install jupyter numpy pandas matplotlib 
```
