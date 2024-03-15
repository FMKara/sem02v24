FROM ubuntu:24.04
RUN apt-get update \
&& apt-get dist-upgrade -y \
&& apt-get autoremove -y \
&& apt-get autoclean -y \
&& apt-get install -y \
sudo \
nano \
wget \
curl \
git 
RUN useradd -G sudo -m -d /home/furkan -s /bin/bash -p "$(openssl passwd -1 besiktas)" furkan
USER furkan
WORKDIR /home/furkan
RUN mkdir hacking \
&& cd hacking \
&& curl -SL https://raw.githubusercontent.com/uia-worker/is105misc/master/sem01v24/pawned.sh > pawned.sh \
&& chmod 764 pawned.sh \
&& cd ..
RUN git config --global user.email "furkanmk@uia.no" \
&& git config --global user.name "FMKara" \
&& git config --global url."https://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:@github.com/".insteadOf "https://github.com" \
&& mkdir -p github.com/FMKara
USER root
RUN curl -SL https://go.dev/dl/go1.21.7.linux-amd64.tar.gz \
| tar xvz -C /usr/local
USER furkan
SHELL ["/bin/bash", "-c"]
RUN mkdir -p $HOME/go/{src,bin}
ENV GOPATH="/home/furkan/go"
ENV PATH="${PATH}:${GOPATH}/bin:/usr/local/go/bin"



