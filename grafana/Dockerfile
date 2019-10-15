FROM grafana/grafana:6.3.0-beta2

USER root

RUN apt-get update && apt-get install -y gettext-base && rm -rf /var/lib/apt/lists/*

WORKDIR /etc/grafana

COPY datasources ./datasources
COPY dashboard/dashboards.yaml /etc/grafana/provisioning/dashboards
COPY dashboard/gatling-dashboard.json /etc/grafana/provisioning/dashboards
COPY dashboard/gatling-report-dashboard.json /etc/grafana/provisioning/dashboards

WORKDIR /app
COPY entrypoint.sh ./
RUN chmod u+x entrypoint.sh

ENTRYPOINT ["/app/entrypoint.sh"]
