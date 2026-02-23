---
layout: post
title: Threat Intelligence - OpenCTI
description: >
  Installing and configuration of a threat intelligence platform called OpenCTI for up to date vulnerability / threat information.
sitemap: false
hide_last_modified: true
---
![800x400](/assets/img/blog/OpenCTI.png "OpenCTI")

# Threat Intelligence Platform Deployment & Vulnerability Intelligence Integration

As part of my personal cybersecurity lab, I designed and deployed a self-hosted instance of OpenCTI to simulate how a security team operationalises external threat intelligence within an internal environment. The objective was not merely to install a tool, but to build a working intelligence capability that mirrors real-world SOC and vulnerability management workflows.

## Architecture & Secure Deployment

I deployed OpenCTI using a containerised architecture (Docker Compose), replicating a production-style stack consisting of:

- OpenCTI backend and frontend services

- Elasticsearch for indexed intelligence search

- RabbitMQ for task distribution

- Redis for caching

- MinIO for object storage

- Dedicated workers for asynchronous processing

During deployment, I:

- Configured secure environment variables and unique service credentials

- Generated and managed API tokens for connector authentication

- Tuned Linux kernel parameters required by Elasticsearch

- Diagnosed and resolved container health and dependency issues

- Validated inter-service communication within an isolated Docker network

This ensured a stable, resilient intelligence platform rather than a basic lab install.

## Integration of NVD Vulnerability Intelligence

To operationalise vulnerability intelligence, I integrated the National Vulnerability Database feed from the National Institute of Standards and Technology using the official CVE external import connector.

Key implementation steps included:

- Obtaining and configuring an NVD API key to handle rate limits efficiently

- Generating a dedicated OpenCTI platform token for secure API authentication

- Deploying the connector as a separate container within the platform network

- Monitoring ingestion logs to validate synchronisation and error handling

- Verifying structured CVE objects within the OpenCTI knowledge graph

The connector continuously imports CVEs as structured Vulnerability entities, enabling correlation with intrusion sets, malware families, techniques, and reports.

## Analyst-Oriented Application

From a security analyst’s perspective, this environment enables me to prioritise vulnerabilities based not only on severity scores, but also on exploitation likelihood and contextual threat relevance. By integrating CVE data into OpenCTI, I am able to correlate vulnerabilities with known adversary tradecraft, linking specific CVEs to intrusion sets, malware families, and attack techniques. This supports contextual analysis rather than treating vulnerabilities as isolated technical identifiers.

The platform also allows me to produce structured intelligence reports that connect vulnerabilities to threat actors and ongoing campaigns, mirroring how intelligence is communicated within a SOC or vulnerability management team. Through this setup, I can simulate intelligence-driven patch prioritisation by assessing which vulnerabilities pose realistic risk to an organisation based on threat activity and exposure. Instead of viewing CVEs as static references, I analyse them within a broader threat landscape, supporting risk-informed security decision-making.

## Competencies Demonstrated

This project demonstrates my ability to deploy and operationalise a practical threat intelligence platform within a secure, containerised environment. I implemented secure API integration and connector configuration to ingest external intelligence feeds, ensuring reliable authentication and service communication. I managed structured data ingestion and validation, confirming that vulnerability records were correctly integrated into the platform’s knowledge graph.

In addition, I applied intelligence correlation techniques to connect vulnerabilities with adversary behaviours and threat entities, leveraging the platform’s graph-based architecture. Throughout the process, I troubleshot distributed service dependencies and container health issues, reinforcing my understanding of service orchestration and system reliability. Most importantly, I translated vulnerability intelligence into operational insight, demonstrating the ability to support evidence-based security decisions rather than simply collecting threat data.