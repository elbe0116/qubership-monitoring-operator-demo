FROM ghcr.io/elbe0116/qubership-docker-integration-tests:PSUPATPOS-86

# Switch to root for installation
USER root

ENV ROBOT_OUTPUT=${ROBOT_HOME}/output \
    SERVICE_CHECKER_SCRIPT=${ROBOT_HOME}/monitoring_pods_checker.py \
    SERVICE_CHECKER_SCRIPT_TIMEOUT=500

RUN mkdir -p ${ROBOT_HOME} \
    && mkdir -p ${ROBOT_OUTPUT} \
    && mkdir -p /home/robot \
    && chmod -R 777 /home/robot

COPY requirements.txt ${ROBOT_HOME}/requirements.txt
COPY src/ ${ROBOT_HOME}/

RUN set -x \
    && pip3 install -r ${ROBOT_HOME}/requirements.txt \
    && rm -rf /var/cache/apk/*

USER 1000:0

EXPOSE 8080
VOLUME ["${ROBOT_OUTPUT}"]
