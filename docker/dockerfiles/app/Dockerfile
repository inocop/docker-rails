FROM ruby:2.5-slim-stretch


RUN apt update \
&&  apt install -y supervisor \
                   rsyslog \
                   cron \
                   vim \
# for rails \
&&  apt install -y build-essential \
                   zlib1g-dev \
                   default-libmysqlclient-dev \
# disk clean \
&&  apt clean \
&&  rm -rf /var/lib/apt/lists/*


# global gem
RUN bash -l -c 'gem install --no-document nokogiri -v "1.10.0"' \


# edit /etc/*.conf
RUN sed -i -e "s/#cron\.\*/cron\.\*/" /etc/rsyslog.conf


ADD ./myapp.conf /etc/supervisor/conf.d/myapp.conf
CMD /usr/bin/supervisord -c /etc/supervisor/supervisord.conf

WORKDIR /var/www/app
