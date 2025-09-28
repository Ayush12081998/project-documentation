Welcome to the project-documentation wiki!

# 🛫 Flight Booking System (Microservices)

## 🎯 Core Microservices
- **User Service** – registration, authentication (JWT/OAuth2).  
- **Flight Search Service** – provides flights, schedules, and availability.  
- **Booking Service** – handles seat reservation, booking confirmation, cancellations.  
- **Payment Service** – processes payments.  
- **Notification Service** – sends email/SMS when booking/payment succeeds.  

---

## ⚡ Flow Example
1. User searches for flights → **Flight Search Service** queries DB.  
2. User selects a flight → **Booking Service** tries to lock a seat.  
   - ✅ If seat lock successful → proceed.  
   - ❌ If not → reject with *“Seat Unavailable.”*  
3. Payment initiated → **Payment Service**.  
   - ✅ If success → booking confirmed, event → **Notification Service**.  
   - ❌ If failure → rollback seat reservation (**Saga pattern**).  
4. User gets e-ticket notification.  

---

## 🔑 Patterns You’ll Learn Here
- **Saga Pattern** (Orchestration/Choreography) → rollback seat reservation if payment fails.  
- **Distributed Locking** → to avoid overbooking seats.  
- **CQRS** → search queries separated from booking commands.  
- **Circuit Breaker & Retry** → for Payment Service.  
- **API Gateway** → single entry point for clients.  
- **Service Registry** → dynamic service discovery (Eureka/Consul).  
- **Asynchronous Messaging** → events (Kafka/RabbitMQ) for Booking → Payment → Notification.  

---

## 🛠 Tech Stack
- **Backend**: Java (Spring Boot + Spring Cloud)  
- **Databases**:  
  - Flights: Relational DB (Postgres/MySQL)  
  - Bookings: Strong consistency (Postgres)  
  - Payments: Relational  
- **Message Broker**: Kafka / RabbitMQ  
- **Infrastructure**: Docker + Kubernetes  
- **Observability**: ELK/EFK, Prometheus + Grafana, Zipkin/Jaeger  

---

## ✈️ Real-World Analogy
- Searching flights → like **browsing products on Amazon** → high read load.  
- Booking → like **placing an order** → must ensure consistency (no double seat booking).  
- Payment → like **checkout flow** → needs reliability + rollback if things go wrong.  

---

## 📈 Learning Path (Step by Step)
- **Phase 1**: Implement REST microservices (User, Flight Search, Booking, Payment).  
- **Phase 2**: Introduce async messaging (Kafka) between Booking → Payment → Notification.  
- **Phase 3**: Add Saga pattern for rollback handling.  
- **Phase 4**: Deploy all services with Docker Compose.  
- **Phase 5**: Scale on Kubernetes + add observability (logging, metrics, tracing).  

---

👉 This project will cover both **core microservice basics** and **advanced distributed systems problems** (consistency, resilience, event-driven design).

- [Tech Designs](./Design.md)
- [Ops design choices](./Devops.md)


