FROM python:stretch
RUN wget https://dl.google.com/go/go1.12.7.linux-amd64.tar.gz
RUN tar -C /usr/local -xzf go1.12.7.linux-amd64.tar.gz

RUN wget https://nodejs.org/dist/v12.7.0/node-v12.7.0-linux-x64.tar.xz
RUN tar -C /usr/local -xf node-v12.7.0-linux-x64.tar.xz

ENV PATH="${PATH}:/usr/local/go/bin"
ENV PATH="${PATH}:/usr/local/node-v12.7.0-linux-x64/bin"
# docker run --rm -it -p9876:9876 -v `pwd`:/src ps/prefab-scripts
CMD ["bash"]