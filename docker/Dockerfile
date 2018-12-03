FROM tensorflow/tensorflow:1.10.0-gpu-py3

RUN pip install --upgrade pip
RUN pip install jupyter_http_over_ws
RUN jupyter serverextension enable --py jupyter_http_over_ws

# gcloud
RUN apt-get update && apt-get -qq install wget
RUN wget -q https://dl.google.com/dl/cloudsdk/channels/rapid/downloads/google-cloud-sdk-226.0.0-linux-x86_64.tar.gz
RUN tar zxf google-cloud-sdk-226.0.0-linux-x86_64.tar.gz google-cloud-sdk && rm google-cloud-sdk-226.0.0-linux-x86_64.tar.gz
RUN mv google-cloud-sdk / && /google-cloud-sdk/install.sh
ENV PATH="${PATH}:/google-cloud-sdk/bin"

# gcloud requires python2
RUN apt-get -qq install python2.7
ENV CLOUDSDK_PYTHON=/usr/bin/python2.7

# for korean
RUN apt-get install -y locales locales-all
ENV LC_ALL en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US.UTF-8

CMD jupyter notebook --notebook-dir=/notebooks --ip 0.0.0.0 --allow-root --no-browser \
  --NotebookApp.allow_origin='https://colab.research.google.com'