# Practical 2: Privacy Impact Assessment of an Online Food Delivery System

## Aim

To conduct a **Privacy Impact Assessment (PIA)** of an **Online Food Delivery System** and identify potential privacy risks associated with the collection, use, storage, and sharing of customer information, along with suitable measures to mitigate these risks.

---

## System Selected

### Online Food Delivery System

An Online Food Delivery System is a web or mobile-based platform that allows customers to browse restaurants, order food, make payments, and track their deliveries.

The system collects personal information such as customer details, delivery addresses, contact information, order history, and payment-related information to provide its services.

---

## Requirements

- Internet connection
- Web browser or smartphone
- Basic knowledge of data privacy
- Basic understanding of online food delivery applications

---

## Introduction

A **Privacy Impact Assessment (PIA)** is a process used to identify and evaluate privacy risks associated with a system that collects or processes personal information.

An Online Food Delivery System handles different types of customer information, including **name, phone number, delivery address, order details, location information, and payment-related data**.

The purpose of this assessment is to identify possible privacy risks and recommend suitable measures to protect customer information.

---

## Procedure

1. Identify the personal data collected by the system.
2. Identify the purpose of collecting the data.
3. Determine who can access the collected information.
4. Identify where the information is stored and processed.
5. Identify possible privacy risks.
6. Assess the likelihood and impact of each risk.
7. Develop suitable measures to reduce the identified risks.
8. Establish appropriate data retention and deletion practices.
9. Review the system for privacy improvements.

---

## Data Collected

### The system may collect:

- Customer name
- Email address
- Mobile number
- Delivery address
- Location information
- Order history
- Restaurant preferences
- Payment transaction information
- Account login information
- Device and IP address
- Customer reviews and feedback

---

## Purpose of Data Collection

| Data Type | Purpose |
|---|---|
| **Name** | Customer identification |
| **Mobile Number** | Order communication and delivery updates |
| **Email Address** | Account management and notifications |
| **Delivery Address** | Delivering food to the customer |
| **Location Information** | Showing nearby restaurants and tracking delivery |
| **Order History** | Managing previous and current orders |
| **Payment Information** | Processing online payments |
| **Account Information** | Managing customer accounts |
| **Device Information** | Security and application functionality |
| **Reviews and Feedback** | Improving services and customer experience |

---

# Privacy Risk Assessment

| Data/Risk | Likelihood | Impact | Risk Level | Mitigation |
|---|---|---|---|---|
| **Unauthorized access to customer accounts** | Medium | High | **High** | Strong passwords and multi-factor authentication |
| **Leakage of delivery addresses** | Medium | High | **High** | Encryption and access control |
| **Misuse of customer phone numbers** | Medium | Medium | **Medium** | Restrict access and avoid unnecessary sharing |
| **Unauthorized access to order history** | Medium | Medium | **Medium** | Authentication and role-based access |
| **Exposure of payment information** | Low | High | **Medium** | Secure payment gateway and encryption |
| **Excessive location tracking** | Medium | High | **High** | Collect location only when required |
| **Unnecessary collection of personal data** | Medium | Medium | **Medium** | Data minimization |
| **Data stored for too long** | Medium | Medium | **Medium** | Define and enforce retention periods |
| **Third-party data sharing** | Medium | High | **High** | Review third-party access and permissions |
| **Incorrect customer information** | Medium | Medium | **Medium** | Allow users to review and update their information |

---

# Major Privacy Risks Identified

## 1. Exposure of Delivery Address

The system requires a customer's address to complete a food delivery.

### Risk

Unauthorized access to delivery addresses could expose a customer's residential or workplace location.

### Mitigation

- Encrypt address information.
- Restrict access to authorized employees and delivery personnel.
- Delete outdated addresses when they are no longer required.
- Avoid displaying full addresses unnecessarily.

---

## 2. Location Tracking

The application may use location information to identify nearby restaurants or track an active delivery.

### Risk

Continuous location tracking may reveal information about a customer's movements and frequently visited places.

### Mitigation

- Request location permission only when necessary.
- Avoid continuous background tracking.
- Allow users to disable location access.
- Delete unnecessary location history.

---

## 3. Payment Information

Customers may make payments through debit cards, credit cards, wallets, or other online payment methods.

### Risk

Improper handling of payment information could result in financial or personal data exposure.

### Mitigation

- Use a trusted payment gateway.
- Encrypt payment-related communication.
- Avoid storing complete card details unnecessarily.
- Follow appropriate payment security standards.

---

## 4. Customer Account Security

Customer accounts may contain names, contact details, addresses, and order history.

### Risk

A compromised account could expose several categories of personal information.

### Mitigation

- Use strong passwords.
- Provide multi-factor authentication.
- Implement account lockout or suspicious-login detection.
- Notify users about unusual account activity.

---

## 5. Third-Party Data Sharing

The system may share required information with restaurants, delivery partners, payment providers, cloud providers, or other service providers.

### Risk

Personal information may be accessed by organizations outside the direct control of the customer.

### Mitigation

- Share only necessary information.
- Limit third-party access.
- Review third-party privacy and security practices.
- Establish appropriate data-processing agreements.

---

# Privacy Protection Measures

1. Use **strong authentication** for customer and administrator accounts.

2. Encrypt sensitive information during **transmission and storage**.

3. Implement **Role-Based Access Control (RBAC)**.

4. Collect only the information required to provide the service.

5. Request location access only when necessary.

6. Do not store complete payment card information unless required and appropriately protected.

7. Establish a clear **data retention and deletion policy**.

8. Allow customers to review and update their personal information.

9. Restrict access to customer addresses and contact information.

10. Regularly review third-party applications and service providers.

11. Maintain security logs to detect unauthorized access.

12. Provide users with a clear privacy notice explaining how their information is used.

---

# Privacy-by-Design Measures

Privacy should be considered during the development of the food delivery system.

The following measures should be implemented:

- **Data minimization**
- **Privacy-friendly default settings**
- **Secure authentication**
- **Encryption**
- **Limited location tracking**
- **Restricted access to customer information**
- **Automatic deletion of unnecessary data**
- **Clear privacy notices**
- **Secure payment processing**

---

# Data Retention

The system should define appropriate retention periods for different types of information.

| Data Type | Suggested Retention | Purpose |
|---|---|---|
| **Account Information** | While account is active | Account management |
| **Delivery Address** | While required by the customer | Food delivery |
| **Order History** | Limited period | Order management and customer support |
| **Payment Records** | As legally required | Financial records |
| **Location Data** | Only as long as necessary | Delivery and restaurant search |
| **Customer Reviews** | While required for service | Service improvement |
| **Security Logs** | Defined security period | Security monitoring |

> **Note:** Actual retention periods should be determined according to business requirements and applicable privacy laws.

---

# User Privacy Controls

Customers should be provided with options to:

- View their personal information.
- Update their name and contact details.
- Manage saved delivery addresses.
- Control location permissions.
- Review their order history.
- Manage account security settings.
- Request deletion of their account where applicable.
- Manage communication and notification preferences.
- Raise privacy-related concerns.

---

# Overall Risk Summary

| Privacy Area | Risk Level | Primary Mitigation |
|---|---|---|
| **Customer Account** | Medium | Strong authentication |
| **Delivery Address** | High | Encryption and access control |
| **Location Data** | High | Limited location collection |
| **Payment Information** | Medium | Secure payment processing |
| **Order History** | Medium | Access control and retention policy |
| **Third-Party Sharing** | High | Limited data sharing |
| **Customer Reviews** | Low | Privacy controls |
| **Data Retention** | Medium | Defined deletion policy |

---

# Result

The **Privacy Impact Assessment of the Online Food Delivery System** was successfully performed.

The assessment identified potential privacy risks related to **customer accounts, delivery addresses, location information, payment information, order history, and third-party data sharing**.

Suitable privacy and security measures were recommended to reduce these risks and protect customer information.

---

# Conclusion

The PIA shows that an **Online Food Delivery System** collects several types of personal information to provide ordering and delivery services.

The major privacy risks include **unauthorized access to customer accounts, exposure of delivery addresses, excessive location tracking, payment information exposure, and third-party data sharing**.

These risks can be reduced through **strong authentication, encryption, access control, data minimization, limited location tracking, secure payment processing, and proper data retention policies**.

Therefore, applying **Privacy-by-Design principles** can help the system provide convenient food delivery services while maintaining the privacy and security of customer information.

---

# Final Assessment

**PIA Status:** Completed

**Overall Privacy Risk:** Medium

### Primary Privacy Concerns

- Customer account security
- Delivery address exposure
- Location tracking
- Payment information
- Order history
- Third-party data sharing
- Data retention

### Primary Mitigation Measures

- Strong authentication
- Encryption
- Role-Based Access Control
- Data minimization
- Limited location tracking
- Secure payment processing
- Data retention and deletion policies
- Regular privacy and security reviews

---

# References

1. **NIST Privacy Framework**  
   https://www.nist.gov/privacy-framework

2. **NIST Cybersecurity Framework**  
   https://www.nist.gov/cyberframework

3. **ISO/IEC 27701 – Privacy Information Management**  
   https://www.iso.org/standard/71670.html

4. **ICO – Data Protection Impact Assessments**  
   https://ico.org.uk/for-organisations/uk-gdpr-guidance-and-resources/accountability-and-governance/data-protection-impact-assessments-dpias/

5. **European Commission – Data Protection**  
   https://commission.europa.eu/law/law-topic/data-protection_en
