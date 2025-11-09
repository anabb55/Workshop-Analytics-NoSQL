#  Workshop Analytics Microservice with Cassandra & Neo4j

**Workshop Analytics Microservice** is  part of a larger system developed for managing workshops within a psychological clinic.  
This system demonstrates how **NoSQL databases** — Cassandra and Neo4j — can be combined to handle large-scale analytics, manage relationships between entities, and maintain data consistency through transactional processing.

---

##  Technologies Used

### Backend
- **Java Spring Boot** – Framework for developing backend microservices.  
- **Apache Cassandra** – Columnar NoSQL database used for storing and analyzing workshop analytics data.  
- **Neo4j** – Graph database used for modeling relationships between participants, sessions, and categories.  
- **Apache Kafka** – Message broker used for implementing the **Saga pattern** and ensuring data consistency across microservices.  

---

##  Microservice Architecture

The project follows a **microservice architecture**, enabling independent development, deployment, and scaling.  
Two complementary microservices were developed:
- **Cassandra Microservice** – Handles analytical data, report generation, and aggregation queries.  
- **Neo4j Microservice** – Manages relationships between participants, sessions, and workshop categories.

Kafka acts as a communication bridge between these services, ensuring synchronized updates across both databases.

---

##  Features

###  Data Management & Analytics (Cassandra)
- **Columnar Storage**: Efficiently stores workshop analytics data (participant counts, feedback statistics, session summaries).  
- **Aggregation Queries**: Supports analytical queries for insights such as:
  - Top 10 most attended workshop categories.  
  - Sessions with the highest feedback ratings.  
  - Yearly participant trends and attendance summaries.  
- **Optimized Schema Design**: Cassandra tables modeled for fast writes and aggregated reads.

### Relationship Management (Neo4j)
- **Graph Modeling**: Represents participants, sessions, and categories as nodes, connected with edges such as `ATTENDED`, `BELONGS_TO`, and `PROVIDED_FEEDBACK`.  
- **Complex Queries**: Enables recommendations and network-based analysis (e.g., suggesting sessions based on previous attendance patterns).

### Transactional Data Processing (Saga Pattern)
- **Kafka Integration**: Ensures consistency between Cassandra and Neo4j through event-based synchronization.  
- **Example Workflow**:  
  When a participant is added to a session in Neo4j, Cassandra automatically updates the participant count for that workshop category.

###  Report Generation
- **Automated Reports**: Generates documents summarizing analytical results directly from Cassandra data.  
- **Report Examples**:
  - List of workshops held in a given year with participant counts.  
  - Top categories by attendance and feedback scores.  
  - Session participation trends across time periods.  

---


##  Usage

Once the microservices are running:
- Kafka synchronizes data between Cassandra and Neo4j.  
- Cassandra handles analytical storage, aggregation, and report generation.  
- Reports can be generated automatically or on demand.

Example scenario:
> When a participant attends a new workshop, Neo4j stores the relationship between the participant and the session, while Cassandra increments the total count for that workshop category and updates analytics accordingly.

---


