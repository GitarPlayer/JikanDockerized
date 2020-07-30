FROM ubuntu:19.10

# author
MAINTAINER Gitarplayer
# set a directory for the app
WORKDIR /usr/src/

# copy all the files to the container
COPY app .

# install dependencies
RUN apt-get update
RUN apt-get install software-properties-common -y
RUN apt-add-repository universe
RUN apt-get install python-dev libxml2-dev libxslt1-dev libffi-dev -y 
RUN apt-get install python-pip -y
RUN pip install scrapy
# cleanup
RUN apt-get -qy autoremove
WORKDIR /usr/src/scrape-anilist/spiders/

# you need to set at least SPIDER_END or the script will fail!
# setting network to localhost makes it work with scraproxy!
CMD ["scrapy", "crawl","mangas","-o", "mangas.csv"]

