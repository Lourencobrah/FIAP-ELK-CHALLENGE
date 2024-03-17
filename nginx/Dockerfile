FROM nginx:latest

#Apaga os arquivos de log padrão
RUN rm -f /var/log/nginx/access.log && rm -f /var/log/nginx/error.log 

#Instala o FileBeat
RUN curl -L -O https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-7.13.0-amd64.deb && \
    dpkg -i filebeat-7.13.0-amd64.deb

#Copia a configuração do FileBeat do container
COPY filebeat.yml /etc/filebeat/filebeat.yml
#Copia o entrypoint
COPY entrypoint.sh /entrypoint.sh

#Da permissão de execução e executa
RUN chmod +x /entrypoint.sh
ENTRYPOINT [ "/entrypoint.sh" ]