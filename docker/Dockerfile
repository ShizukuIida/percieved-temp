FROM sonoisa/deep-learning-coding:pytorch1.6.0_tensorflow2.3.0

WORKDIR /workspace

COPY requirements.txt ./

RUN pip install --upgrade pip
RUN pip install --upgrade setuptools
RUN pip install -r requirements.txt

#Unidic for MeCab
#RUN python3 -m unidic download
USER root
#Neologd for MeCab
RUN sudo apt-get update \
 && sudo apt-get -y install mecab \
    libmecab-dev \
    mecab-ipadic-utf8 \
    file

#RUN apt install mecab libmecab-dev mecab-ipadic-utf8
RUN git clone --depth 1 https://github.com/neologd/mecab-ipadic-neologd.git
RUN cd mecab-ipadic-neologd && ./bin/install-mecab-ipadic-neologd -n -y
RUN python -m unidic download

#install IPAexGothic for wordcloud in japanese URL:https://self-development.info/ipaexgothic%e3%81%ab%e3%82%88%e3%82%8bmatplotlib%e3%81%ae%e6%97%a5%e6%9c%ac%e8%aa%9e%e5%8c%96%e3%80%90python%e3%80%91/
RUN sudo apt-get -y install fontconfig \
 && sudo apt-get -y install fonts-ipaexfont

EXPOSE 8888