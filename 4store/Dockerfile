FROM debian:jessie

MAINTAINER Yiannis Mouchakis <gmouchakis@iit.demokritos.gr>

# Install packages.
RUN apt-get update && apt-get install -y \
            git \
            make \
            autoconf \
            libtool \
	    pkg-config \ 
	    libncurses5-dev \ 
	    libreadline6-dev \
	    zlib1g-dev \
	    uuid-dev \
	    libxml2-dev \
	    libglib2.0-dev \ 
	    libraptor2-dev \ 
	    librasqal3-dev \ 
    && apt-get clean \ 
    && rm -rf /var/lib/apt/lists/*

# Install 4store and clean up
RUN git clone https://github.com/garlik/4store.git \
    && cd 4store \
    && ./autogen.sh \
    && ./configure \
    && make \
    && make install \
    && make clean \
    && cd .. \
    && rm -rf 4store

# create directory for 4store logs
RUN mkdir /var/log/4store

#Expose 4s-boss default port
EXPOSE 6733

# Define default command.
CMD /usr/local/bin/4s-boss -D 
