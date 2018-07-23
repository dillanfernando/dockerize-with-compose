FROM httpd

ADD --chown=root:www-data admin-center.tar.gz /usr/local/apache2/htdocs/
ADD --chown=root:www-data ncrypt.tar.gz /usr/local/apache2/htdocs/

COPY httpd.conf /usr/local/apache2/conf/httpd.conf.orig
USER root
ENV LOCAL_IP=10.54.150.70
#RUN export LOCAL_IP=`ip add | grep global | awk -F/ '{print $1}' | awk -Finet '{print $2}' | xargs` && sed 's/127.0.0.1/'$LOCAL_IP'/g' /usr/local/apache2/conf/httpd.conf.orig >/usr/local/apache2/conf/httpd.conf
RUN sed 's/127.0.0.1/'$LOCAL_IP'/g' /usr/local/apache2/conf/httpd.conf.orig >/usr/local/apache2/conf/httpd.conf
RUN chown root:www-data /usr/local/apache2/conf/httpd.conf
RUN chmod 776 /usr/local/apache2/conf/httpd.conf

RUN chown root:src /usr/local/apache2/htdocs/admincenter-frontend
RUN chown root:src -R /usr/local/apache2/htdocs/admincenter-frontend/
RUN chmod -R 777 /usr/local/apache2/htdocs/admincenter-frontend/

RUN chown root:src /usr/local/apache2/htdocs/ncrypt
RUN chown root:src -R /usr/local/apache2/htdocs/ncrypt/
RUN chmod -R 777 /usr/local/apache2/htdocs/ncrypt/
