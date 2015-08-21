FROM ipython/scipystack

MAINTAINER ASI <info@theasi.co>

VOLUME /notebooks
WORKDIR /notebooks

EXPOSE 8888

# Update the sources list
RUN apt-get update

# Install postgres dependencies
RUN apt-get -y install libpq-dev

# You can mount your own SSL certs as necessary here
ENV PEM_FILE /key.pem
# $PASSWORD will get `unset` within notebook.sh, turned into an IPython style hash
ENV PASSWORD Dont make this your default
ENV USE_HTTP 0

# Get pip to download and install requirements:
ADD requirements.txt /
RUN pip install -r /requirements.txt

ADD notebook.sh /
RUN chmod u+x /notebook.sh

CMD ["/notebook.sh"]
