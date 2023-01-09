FROM sonarqube:8.9-community
RUN /sbin/apk  add git   # Install Git
RUN /sbin/apk  add unzip  # unzip


# Wget Sonar Scanner
wget https://binaries.sonarsource.com/Distribution/sonar-scanner-cli/sonar-scanner-cli-4.7.0.2747-linux.zip

WORKDIR /opt/sonarqube

# COPY sonar-custom-plugin-1.0.jar /opt/sonarqube/extensions/
