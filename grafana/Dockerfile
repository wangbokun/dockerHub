FROM grafana/grafana:6.2.5
USER root
RUN grafana-cli plugins install grafana-piechart-panel
RUN grafana-cli plugins install michaeldmoore-annunciator-panel

COPY ./etc/ldap.toml /etc/grafana/ldap.toml
COPY ./etc/grafana.ini  /etc/grafana/grafana.ini
#COPY ./etc/home.json /usr/share/grafana/public/dashboards/home.json
