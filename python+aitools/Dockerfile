FROM centos

# Install elementary libs
RUN yum groups mark convert
RUN yum groupinstall -y "Development Tools"
RUN yum install -y which wget zlib-devel openssl-devel bzip2-devel libffi-devel sqlite-devel

# Install Python3
RUN wget https://www.python.org/ftp/python/3.7.4/Python-3.7.4.tar.xz
RUN tar -xf Python-3.7.4.tar.xz
WORKDIR Python-3.7.4
RUN ./configure --prefix=/usr
RUN make
RUN make install
WORKDIR /
RUN rm -rf Python-3.7.4.tar.xz Python-3.7.4

# Install NeuralNetworks tools
## Install TensorFlow
RUN pip3 install --upgrade pip
RUN pip3 install tensorflow==2.0.0-rc0

## Install PyTorch
RUN pip3 install numpy
RUN pip3 install torch torchvision

# Install NLP tools
## Install spaCy
RUN pip3 install -U spacy
RUN python3 -m spacy download en
RUN python3 -m spacy download de
RUN python3 -m spacy download fr
RUN python3 -m spacy download es
RUN python3 -m spacy download pt
RUN python3 -m spacy download it
RUN python3 -m spacy download nl
RUN python3 -m spacy download el
RUN python3 -m spacy download xx

## Install NLTK 
RUN pip3 install --user -U nltk
RUN python3 -m nltk.downloader -d /usr/local/share/nltk_data all

