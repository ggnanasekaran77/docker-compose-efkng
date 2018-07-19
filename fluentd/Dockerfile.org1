FROM fluent/fluentd:v0.12-debian
RUN  apt-get update && apt-get install -y \
build-essential \
libgeoip-dev \
zlib1g-dev \
libssl-dev \
libreadline-dev
RUN apt-get -qq -y install curl
# Download the ruby-build code
RUN \curl -L https://github.com/sstephenson/ruby-build/archive/v20180601.tar.gz | tar -zxvf - -C /tmp/
# Install ruby-build
RUN cd /tmp/ruby-build-* && ./install.sh && cd / && rm -rfv /tmp/ruby-build-master
# Install ruby
RUN ruby-build -v 2.5.1 /usr/local
# Install gems
RUN gem install bundler rubygems-bundler --no-rdoc --no-ri
# Regenerate binstubs
RUN gem regenerate_binstubs
RUN gem install fluent-plugin-geoip -v 0.8.0 --no-ri --no-rdoc
RUN gem install fluent-plugin-elasticsearch --no-rdoc --no-ri
