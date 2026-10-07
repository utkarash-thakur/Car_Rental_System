# Car Rental System

A console app in Java for renting cars. Customers search for cars and make, change or cancel reservations; administrators manage the fleet and customers and see usage and revenue reports.

**Portfolio:** [utkarash-thakur.vercel.app](https://utkarash-thakur.vercel.app)

## Highlights

- Built on Hibernate (JPA) and MySQL with `Car`, `Customer`, `Reservation` and `Transaction` entities and their one-to-many and many-to-one relations.
- DAO and service layers: every write runs in a transaction, and JPQL queries power search and the revenue report.
- Soft delete: removed cars and customers are flagged, not erased, so history stays intact and a car can be restored.
- Custom exceptions (`NoRecordException`, `DuplicateRecordException`, `RecordDeletedException`, …) keep the console flow clean.

## Features

**Customers**
- Register with a unique username and log in.
- Search available cars by rental price and mileage.
- Reserve a car for a rental period, then view, change or cancel reservations.

**Administrators**
- View all customers and cars.
- Add, update, soft-delete and restore cars.
- Soft-delete customers.
- Generate a car usage and revenue report.

## Tech stack

Java 17 · Hibernate (JPA) · MySQL · Maven

## Database design

![ER diagram](ER.png)

## Project structure

```
pleasant-summer-812/src/main/java/com/rental/main
├── Main.java, AdminUI.java, CustomerUI.java   console menus
├── entities/     Car, Customer, Reservation, Transaction
├── DAO/          AdminDAO, CustomerDAO (+Impl): queries and transactions
├── services/     AdminServices, CustomerServices (+Impl)
├── exceptions/   custom exceptions
└── Util/DbUtils.java   EntityManager factory
```

## Run it locally

1. Install Java 17, Maven and MySQL, then create the database:
   ```sql
   CREATE DATABASE cars;
   ```
   `cars.sql` has sample data if you want some to start with.
2. Set your MySQL username and password in `pleasant-summer-812/src/main/resources/META-INF/persistence.xml`. Tables are created on first start.
3. Open `pleasant-summer-812` in your IDE and run `com.rental.main.Main`.

## Author

**Utkarash Thakur**, Backend Engineer · [Portfolio](https://utkarash-thakur.vercel.app) · [LinkedIn](https://www.linkedin.com/in/utkarash-thakur/)
