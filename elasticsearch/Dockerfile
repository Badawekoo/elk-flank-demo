
# Use the official Elasticsearch image
FROM docker.elastic.co/elasticsearch/elasticsearch:8.9.0

# Set environment variables for Elasticsearch configuration
ENV discovery.type=single-node \
    ES_JAVA_OPTS="-Xms1024m -Xmx1024m"

# Set the working directory
WORKDIR /usr/share/elasticsearch

# Expose the default Elasticsearch ports
EXPOSE 9200 9300
RUN pwd
RUN ls -ltr
RUN ls -ltr /etc/.ci-agent/workspace/*/*

# Copy custom configuration files (if needed)
# Uncomment the line below if you have a custom configuration file
COPY /etc/.ci-agent/workspace/elasticsearch/elasticsearch.yml /usr/share/elasticsearch/config/elasticsearch.yml
COPY /etc/.ci-agent/workspace/elasticsearch/log4j2.properties /usr/share/elasticsearch/config/log4j2.docker.properties

# Install plugins (if needed)
# Uncomment the lines below to install specific plugins
# RUN bin/elasticsearch-plugin install analysis-icu
# RUN bin/elasticsearch-plugin install analysis-phonetic

# Set permissions (Elasticsearch requires certain permissions)
RUN chmod -R 0775 /usr/share/elasticsearch && \
    chown -R elasticsearch:elasticsearch /usr/share/elasticsearch

# Run Elasticsearch as the default command
CMD ["bin/elasticsearch"]
