# Use the official PostgreSQL 16 image as a base
FROM postgres:16.3-bookworm

# Install required dependencies
RUN apt-get update && apt-get install -y \
    build-essential \
    wget \
    git \
    postgresql-server-dev-16 \
    && rm -rf /var/lib/apt/lists/*

RUN apt-get install -y openssl libssl-dev 
    # curl
# Install pgvector extension
RUN git clone --branch v0.7.0 https://github.com/pgvector/pgvector.git \
    && cd pgvector \
    && make \
    && make install \
    && cd .. \
    && rm -rf pgvector

RUN apt update && apt install -y curl \
    libcurl4-openssl-dev \
    libssl-dev 

# Install pgsql-http extension
RUN git clone --branch v1.6.0 https://github.com/pramsey/pgsql-http.git \
    && cd pgsql-http \
    && make \
    && make install \
    && cd .. \
    && rm -rf pgsql-http

# Set the default command to run PostgreSQL
CMD ["postgres"]

# Expose the default PostgreSQL port
EXPOSE 5432