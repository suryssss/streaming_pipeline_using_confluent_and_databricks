# SmartSense IoT — Real-Time Industrial IoT Monitoring & Analytics

A real-time IoT data engineering project that simulates industrial machine sensor readings, streams events through Confluent Cloud (Apache Kafka), detects abnormal machine conditions, and processes sensor data in Databricks using PySpark and Delta Lake.

The project demonstrates how streaming infrastructure and a modern data lakehouse can be combined to build an industrial machine monitoring pipeline.

---

## Overview

Industrial machines continuously generate sensor data such as temperature, vibration, and pressure. Analyzing this data in real time helps identify abnormal operating conditions and supports predictive maintenance.

SmartSense IoT simulates this environment by generating sensor events, publishing them to Kafka, detecting anomalies, and processing the incoming data through a Bronze–Silver–Gold architecture.

### Key Objectives

- Simulate real-time industrial IoT sensor data.
- Stream JSON events using Confluent Cloud.
- Implement real-time anomaly detection using Python.
- Publish abnormal-condition alerts to a separate Kafka topic.
- Ingest streaming events into Databricks using Spark Structured Streaming.
- Store raw events in Delta Lake.
- Clean, validate, and deduplicate sensor data.
- Build analytical datasets for machine health monitoring.
- Prepare data for visualization through Databricks SQL dashboards.

---

## Architecture

```text
                INDUSTRIAL IoT SIMULATION
                           |
                           v
                    Google Colab
                  Python Sensor Generator
                           |
                           v
                    Confluent Cloud
                     Apache Kafka
                           |
                +----------+----------+
                |                     |
                v                     v
       thermostat_readings      Python Consumer
          Raw Sensor Data             |
                                      | Anomaly Detection
                                      v
                                machine_alerts
                                      |
                                      v
                              Alert Events


                    DATA ENGINEERING PIPELINE
                           |
                           v
                    Confluent Cloud
                           |
                           v
                  thermostat_readings
                           |
                           v
                  Spark Structured Streaming
                           |
                           v
                     BRONZE LAYER
                  Raw Events in Delta Lake
                           |
                           v
                     SILVER LAYER
               Parsing, Validation, Cleaning
                    and Deduplication
                           |
                           v
                      GOLD LAYER
                Machine Health Aggregations
                           |
                           v
                   Databricks SQL
                  Monitoring Dashboard
