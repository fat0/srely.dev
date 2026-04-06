---
title: "> resume"
layout: "resume"
---

## > summary

Senior Site Reliability Engineer focused on building and maintaining scalable, resilient infrastructure that allows developers to move fast without breaking things. I advocate for eliminating operational toil through IaC and observability. Expert in the HashiCorp stack (Nomad, Consul, Vault) and cloud-native technologies with over 10 years of experience in platform resiliency.

## > skills

- **Infrastructure & Orchestration:** Terraform, Ansible, Nomad, Kubernetes, Docker, Consul, Vault, Traefik
- **Cloud Platforms:** AWS, OCI, GCP
- **Databases:** Aurora / RDS, Cassandra, CockroachDB, PostgreSQL
- **Programming:** Go, Python, Bash
- **Monitoring & Observability:** Datadog, Prometheus, Grafana

## > experience

### HashiCorp / IBM | Senior Site Reliability Engineer | *Dec 2021 -- Present*

- Designing and implementing Blue/Green deployment architecture for Traefik, eliminating downtime during load balancer configuration changes.
- Led DR initiative delivering automated failover/failback for Aurora Global and Replicated Vault across two AWS regions, significantly reducing RTO for critical platform infrastructure.
- Overhauled observability for Nomad, Consul, and Vault -- built Datadog dashboards, closed monitoring gaps, and defined SLOs that materially reduced MTTR and improved on-call response times.
- Contributed to a custom Go-based cluster lifecycle tool automating rolling node replacement for Vault, using autopilot state and health APIs to safely quiesce nodes before ASG termination for zero-downtime maintenance.
- Migrated legacy Bash configuration to modular Ansible, eliminating toil and reducing operational overhead across the platform team.

### Capital One | Principal Software Engineer | *Jun 2019 -- Dec 2021*

- Led infrastructure automation for DataStax Cassandra and Ops Center. Built reusable automation frameworks using AWS, Terraform, Ansible, and Python that simplified Cassandra cluster provisioning, recovery, and self-healing, reducing manual operational work for multiple teams. Drove adoption of infrastructure automation standards across engineering organization.

### Capital One | Senior Software Engineer | *Mar 2018 -- Jun 2019*

- Built infrastructure automation for multi-region self-hosted CockroachDB on AWS.
- Developed container deployment automation for Nomad, standardizing release processes and reducing manual deployment overhead.

### AddThis / Oracle Data Cloud | Senior Systems Engineer | *Jan 2016 -- Mar 2018*

- Managed infra automation for hundreds of servers in our datacenter in two regions, using Chef, test kitchen, kickstart, cobbler, and custom Python tooling.
- Administered and built automation for database systems like MySQL and Cassandra.
- Built automation for migrating our services out of legacy datacenters and into Oracle Cloud.

### Amazon Web Services | Systems Engineer | *Mar 2015 -- Jan 2016*

- Automated provisioning and scaling of DNS resolver fleets for AWS EC2 using Ruby and CloudFormation.
- Deployed canary monitoring to track resolver health from customer perspective, enabling proactive issue detection.
- Fulfilled high-severity on-call rotations for critical DNS infrastructure.

### MicroStrategy | Systems Engineer | *Mar 2014 -- Mar 2015*

- Built infrastructure automation using Puppet and Bash to support two engineering teams.
- Provisioned and maintained customer environments across AWS and on-premises datacenters.
- Automated release deployment pipelines across testing and production environments.
- Managed Linux web servers (Tomcat, Apache) and MySQL databases.

### Pixar Animation Studios | Unix System Administrator | *May 2010 -- Jul 2013*

- Led migration of production data from NetApp to Isilon OneFS, coordinating across multiple teams to ensure service continuity.
- Managed high-performance Isilon storage clusters supporting visual effects production workflows. Scaled storage infrastructure from terabytes to petabytes and performed operating system upgrades with zero downtime.

### Hammerhead Productions | Unix System Administrator | *Nov 2005 -- Apr 2010*

- Provisioned fleets of Linux servers for 2D and 3D rendering pipelines, managed HPC storage infrastructure (Isilon, SGI, custom RAID) supporting visual effects and CGI rendering workflows.
- Scripted automation for job submission to visual effects and 3D rendering pipelines.

## > education

**Florida State University** -- Bachelor of Fine Arts (BFA) in Film Production
