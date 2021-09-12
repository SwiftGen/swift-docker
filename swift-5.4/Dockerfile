FROM swift:5.4

# Install system packages
RUN apt-get update -y && \
  apt-get install -y curl wget && \
  rm -r /var/lib/apt/lists/*

# install RVM, Ruby, and Bundler
RUN gpg --keyserver keyserver.ubuntu.com --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB
RUN \curl -sSL https://get.rvm.io | bash -s stable
SHELL ["/bin/bash", "-l", "-c"]
RUN rvm requirements
RUN source /etc/profile.d/rvm.sh
RUN rvm install 2.6
RUN gem install bundler --no-document -f -v "~> 2.2.27"

# configure env
ENV rvm_path="/usr/local/rvm"
ENV PATH="${rvm_path}/bin:${rvm_path}/gems/default/bin:${rvm_path}/rubies/default/bin:${PATH}"
ENV GEM_HOME="${rvm_path}/gems/default"
ENV GEM_PATH="${rvm_path}/gems/default"

# ensure we use login bash
ENTRYPOINT ["/bin/bash", "-l", "-c"]
