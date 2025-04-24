FROM ubuntu:24.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update \
    && apt-get install -y make python3 python3-pil python3-webpy python3-mysqldb python3-psycopg2 \
    && apt-get install -y imagemagick \
    && apt-get install -y wkhtmltopdf \
    && apt-get install -y python3-reportlab \
    && apt-get install -y python3-requests \
    && apt-get install -y python3-boto3 \
    && apt-get install -y wget


WORKDIR /tmp
RUN wget https://public.sheltermanager.com/deb/sheltermanager3_49_all.deb

# COPY ./entrypoint.sh /entrypoint.sh
# RUN chmod +x /entrypoint.sh

RUN apt install -y ./sheltermanager3_49_all.deb
RUN apt install -y apache2 libapache2-mod-wsgi-py3

COPY ./http-asm3.conf /etc/apache2/sites-available/asm3.conf

RUN a2enmod wsgi
RUN a2ensite asm3

COPY ./asm3.conf /etc/

# Script to run both services
COPY entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh

# Use the script as the entrypoint
ENTRYPOINT ["/entrypoint.sh"]

# RUN systemctl enable apache2
#
#
# EXPOSE 5000
#
# # Use custom entrypoint
# ENTRYPOINT ["/entrypoint.sh"]
#
# # Default command
# CMD ["apache2ctl", "-D", "FOREGROUND"]
