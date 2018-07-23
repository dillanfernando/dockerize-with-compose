FROM jboss/wildfly



ADD --chown=jboss:root config-files.tar.gz /opt/jboss/wildfly/

ENV NTRUST_CONFIG_DIR /opt/jboss/wildfly/NTRUST_CONFIG_DIR_WF
COPY admincenter.war /opt/jboss/wildfly/standalone/deployments/admincenter.war
COPY customercenter.war /opt/jboss/wildfly/standalone/deployments/customercenter.war
USER root
RUN chown jboss:jboss /opt/jboss/wildfly/NTRUST_CONFIG_DIR_WF
RUN chown jboss:jboss -R /opt/jboss/wildfly/NTRUST_CONFIG_DIR_WF/
COPY java.security /usr/lib/jvm/java-1.8.0-openjdk-1.8.0.161-0.b14.el7_4.x86_64/jre/lib/security/java.security
COPY bcpg-jdk16-1.46.jar /usr/lib/jvm/java-1.8.0-openjdk-1.8.0.161-0.b14.el7_4.x86_64/jre/lib/ext/bcpg-jdk16-1.46
COPY bcprov-jdk16-146.jar /usr/lib/jvm/java-1.8.0-openjdk-1.8.0.161-0.b14.el7_4.x86_64/jre/lib/ext/bcprov-jdk16-146.jar
RUN chmod 776 /opt/jboss/wildfly/NTRUST_CONFIG_DIR_WF

USER jboss

EXPOSE 8080 9990
