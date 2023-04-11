FROM ubuntu:20.04

# Install git & cron & dependencies required to build Ruby
RUN apt-get update && \
    apt-get -y install git && \
    apt-get -y install curl && \
    apt-get -y install cron && \
    apt-get -y install build-essential curl wget git libssl-dev libreadline-dev zlib1g-dev

# Install Ruby 2.7.1 using rbenv
RUN git clone https://github.com/rbenv/rbenv.git ~/.rbenv && \
    echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc && \
    echo 'eval "$(rbenv init -)"' >> ~/.bashrc && \
    exec $SHELL && \
    git clone https://github.com/rbenv/ruby-build.git ~/.rbenv/plugins/ruby-build && \
    ~/.rbenv/bin/rbenv install 2.7.1 && \
    ~/.rbenv/bin/rbenv global 2.7.1

# Create symlinks for Ruby
RUN cd /usr/bin && \
    ln -s ~/.rbenv/bin/rbenv rbenv && \
    ln -s ~/.rbenv/shims/ruby ruby && \
    ln -s ~/.rbenv/shims/irb irb

# Create the log file to be able to run tail
RUN touch /var/log/cron.log
