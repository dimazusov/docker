FROM amd64/ubuntu

RUN apt-get update
RUN apt-get install -y nginx
RUN apt-get install -y mysql-server
ENV TZ=Europe/Moscow
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN apt-get install -y php7.2-cli php7.2-fpm php7.2-curl php7.2-gd php7.2-mysql php7.2-mbstring zip unzip

RUN rm /etc/nginx/sites-available/default
RUN rm /etc/nginx/sites-enabled/default

COPY ./conf/nginx/site.com /etc/nginx/sites-available/site.com
COPY ./conf/nginx/site.com /etc/nginx/sites-enabled/site.com

#RUN mkdir /app
#ADD . /app

CMD service nginx start && \
    service php7.2-fpm start && \
    tail -f /dev/null
