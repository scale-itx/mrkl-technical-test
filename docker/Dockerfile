FROM apache/airflow:2.2.0

USER root
# Install openjdk required for Spark and distutils required for joblib
RUN apt update && apt install -y python3.7-distutils openjdk-11-jdk && rm -rf /var/lib/apt/lists/*
COPY --chown=airflow:root Pipfile.lock /opt/mirakl/
COPY --chown=airflow:root Pipfile /opt/mirakl/

USER airflow
RUN pip install pipenv
ENV PIPENV_VENV_IN_PROJECT=1
RUN  cd /opt/mirakl && pipenv sync

COPY categories_classification /opt/airflow/mirakl/
