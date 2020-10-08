FROM swift:5.3

# Install system packages
RUN apt-get update -y && apt-get install -y \
  wget rubygems ruby-dev && \
  rm -r /var/lib/apt/lists/*

# Install bundler
RUN gem install bundler
