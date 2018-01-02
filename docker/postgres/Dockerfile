FROM postgres:10

MAINTAINER Mimoja <git@mimoja.de>

RUN  export DEBIAN_FRONTEND=noninteractive
ENV  DEBIAN_FRONTEND noninteractive
RUN  dpkg-divert --local --rename --add /sbin/initctl

RUN apt-get -y update
RUN apt-get -y dist-upgrade
RUN apt-get -y install gnupg2 wget ca-certificates rpl pwgen

RUN sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt/ stretch-pgdg main" > /etc/apt/sources.list.d/pgdg.list'
RUN wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | apt-key add -
RUN apt-get -y update

RUN apt-get install -y postgresql-10-postgis-2.4

EXPOSE 5432

ADD postgres-initdb.sh /docker-entrypoint-initdb.d/initdb.sh
