FROM centos

# Install elementary libs
RUN yum groupinstall -y "Development Tools"
RUN yum install -y cmake swig boost boost-regex libicu boost-system boost-program-options boost-thread zlib
RUN yum install -y bzip2-devel libffi-devel sqlite-devel zlib-devel openssl-devel boost-devel libicu-devel zlib-devel
RUN yum install -y which wget zsh vim

# Install Python3
RUN wget https://www.python.org/ftp/python/3.9.1/Python-3.9.1.tar.xz
RUN tar -xf Python-3.9.1.tar.xz
WORKDIR Python-3.9.1
RUN ./configure --enable-optimizations
RUN make
RUN make install
WORKDIR /
RUN rm -rf Python-3.9.1.tar.xz Python-3.9.1

## Python tools
RUN pip3 install black
RUN pip3 install ipython

# Install NeuralNetworks tools
## Install TensorFlow
RUN pip3 install --upgrade pip
RUN pip3 install tensorflow

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

## FreelingNLP
RUN wget https://github.com/TALP-UPC/FreeLing/releases/download/4.1/FreeLing-4.1.tar.gz
RUN tar -xf FreeLing-4.1.tar.gz
WORKDIR FreeLing-4.1/build
RUN sed "s/3.5/3.8/" <<< $(cat ../APIs/python3/Makefile) > ../APIs/python3/Makefile
RUN sed "s/\/usr\/include\//\/usr\/local\/include\//" <<< $(cat ../APIs/python3/Makefile) > ../APIs/python3/Makefile
RUN (echo "set(Python_ADDITIONAL_VERSIONS 3.8)" && cat ../APIs/python3/CMakeLists.txt) > cmp8.tmp && mv cmp8.tmp ../APIs/python3/CMakeLists.txt
RUN cmake .. -DPYTHON3_API=ON
RUN make -j 4 install
WORKDIR /FreeLing-4.1/APIs/python3
RUN make
RUN cp _freeling.so /usr/local/lib/_pyfreeling.so
RUN echo /usr/local/lib/ > /etc/ld.so.conf.d/freeling.conf
RUN ldconfig
WORKDIR /
#RUN rm -rf FreeLing-4.1.tar.gz FreeLing-4.1/

# Additional tools
## 
RUN sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

