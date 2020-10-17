FROM postgres:11

ARG DB_LANG=en_US

RUN apt-get update \
    && apt-get -y upgrade \
    && apt-get -y install locales-all \
    && locale-gen ${DB_LANG}.UTF-8 \
    && localedef -f UTF-8 -i ${DB_LANG} ${DB_LANG}.utf8 \
    && apt-get -y install bash curl file vim binutils groff less unzip \
    && curl -sL https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip -o awscliv2.zip \
    && unzip awscliv2.zip \
    && aws/install \
    && rm -rf \
        awscliv2.zip \
        aws \
        /usr/local/aws-cli/v2/*/dist/aws_completer \
        /usr/local/aws-cli/v2/*/dist/awscli/data/ac.index \
        /usr/local/aws-cli/v2/*/dist/awscli/examples

ENV LANG $DB_LANG.UTF-8
ENV LC_CTYPE $DB_LANG.UTF-8

