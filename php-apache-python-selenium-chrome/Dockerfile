FROM php:apache
RUN a2enmod rewrite

RUN apt-get update && apt-get install -y python \
    python-dev\
    python-pip \
    wget \
    gnupg \
    unzip
    
ARG CHROME_VERSION="google-chrome-stable"    

RUN wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add - \
  && echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google-chrome.list \
  && apt-get update -qqy \
  && apt-get -qqy install \
    ${CHROME_VERSION:-google-chrome-stable} \
  && rm /etc/apt/sources.list.d/google-chrome.list \
  && rm -rf /var/lib/apt/lists/* /var/cache/apt/*

# RUN apt-get update && apt-get install -y google-chrome-stable


    
RUN pip install selenium requests \
                 && wget https://chromedriver.storage.googleapis.com/87.0.4280.88/chromedriver_linux64.zip \
                 && unzip chromedriver_linux64.zip \
                 && chmod +x chromedriver \
                 && mv chromedriver /usr/local/bin/
