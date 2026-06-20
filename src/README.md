# Guitars & Gear Inventory Management System

## Overview

Guitars & Gear is a Java Spring Framework inventory management application customized for a guitar shop that sells completed guitar products made from individual parts. The application allows users to manage inventory for guitar-related products and parts, track stock levels, define minimum and maximum inventory limits, and purchase products through a simple HTML user interface.

This project was originally developed for WGU D287: Java Frameworks. The application began as a provided Spring Framework template and was customized to meet specific business requirements for a fictional guitar retail store.

## Project Purpose

The purpose of this project is to demonstrate the ability to customize and maintain a Spring Framework application with a Java backend and an HTML frontend. The system was adapted for a customer that sells products composed of parts.

For this version, the chosen customer is a guitar and music gear shop. Example products include complete guitar packages, while example parts include guitar bodies, necks, fretboards, tuners, bridges, pickups, strings, or related components.

## Competencies Demonstrated

This project demonstrates the following competencies:

### Implements User Interfaces

The application includes customized HTML pages for the store inventory system, including a main inventory screen and an About page. The interface displays the shop name, product names, part names, inventory data, and user actions.

### Implements Frameworks

The application uses Java and the Spring Framework to manage backend logic, object-oriented domain models, controllers, validation, persistence, and MVC-style page routing.

## Scenario

A company licenses and customizes inventory software for different types of stores. This project customizes the provided inventory management application for a guitar shop that sells products made from parts.

In this scenario:

* A completed guitar or gear bundle is treated as a product.
* Individual guitar components are treated as parts.
* The application allows the store to manage products, parts, inventory levels, and customer purchases.

## Features

* Customized store branding for Guitars & Gear
* HTML frontend for viewing and managing inventory
* About page with navigation to and from the main screen
* Sample inventory for guitar-related products and parts
* Product purchase functionality with a Buy Now button
* Inventory decrement after successful product purchase
* Success and failure messages for purchase attempts
* Minimum and maximum inventory tracking for parts
* Validation for inventory below minimum levels
* Validation for inventory above maximum levels
* Validation to prevent product updates from reducing part inventory below the minimum
* Unit tests for minimum and maximum inventory fields
* Cleaned up unused validator classes
* Maven-based Java project structure

## Technologies Used

* Java
* Spring Framework
* Spring Boot
* Spring MVC
* Thymeleaf
* Maven
* HTML
* CSS
* H2 database
* JUnit
* IntelliJ IDEA
* Git
* GitHub

## Project Structure

```text
guitars-and-gear/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── .../
│   │   │       ├── controllers/
│   │   │       ├── domain/
│   │   │       ├── repositories/
│   │   │       ├── service/
│   │   │       └── validators/
│   │   │
│   │   └── resources/
│   │       ├── templates/
│   │       │   ├── mainscreen.html
│   │       │   ├── about.html
│   │       │   ├── InhousePartForm.html
│   │       │   └── OutsourcedPartForm.html
│   │       └── application.properties
│   │
│   └── test/
│       └── java/
│           └── .../
│               └── PartTest.java
│
├── pom.xml
├── mvnw
├── mvnw.cmd
└── README.md
```

## Main Application Pages

### Main Screen

The main screen displays the customized shop name, available parts, available products, and inventory management actions. Users can add, update, delete, and purchase products.

### About Page

The About page describes the Guitars & Gear shop and includes navigation back to the main inventory screen.

### In-House Part Form

The in-house part form allows users to create or update parts produced internally by the shop. It includes fields for inventory, minimum inventory, and maximum inventory.

### Outsourced Part Form

The outsourced part form allows users to create or update parts supplied by outside vendors. It includes fields for inventory, minimum inventory, and maximum inventory.

## Inventory Model

The application manages two primary inventory categories:

### Parts

Parts are individual components that can be associated with products. Examples may include:

* Guitar body
* Guitar neck
* Fretboard
* Tuners
* Bridge
* Pickups
* Strings

### Products

Products are completed items or packages made from parts. Examples may include:

* Beginner electric guitar package
* Acoustic guitar starter kit
* Blues guitar upgrade bundle
* Recording-ready guitar setup
* Stage performance guitar package

## Inventory Rules

The application enforces several inventory rules:

1. A part must have an inventory value.
2. A part must have a minimum inventory value.
3. A part must have a maximum inventory value.
4. A part's inventory must be greater than or equal to the minimum inventory value.
5. A part's inventory must be less than or equal to the maximum inventory value.
6. Product purchases decrement the product inventory by one.
7. Product purchases do not decrement the inventory of associated parts.
8. A product purchase fails if the product inventory is zero.
9. Product updates cannot reduce associated part inventory below the required minimum.

## Buy Now Functionality

The product list includes a Buy Now button next to the update and delete buttons.

When a user selects Buy Now:

* If the product has available inventory, the product inventory is reduced by one.
* A success message is displayed.
* If the product inventory is zero, the inventory is not changed.
* A failure message is displayed.

## Validation

The application includes validation for part inventory limits.

Validation messages are displayed when:

* The part inventory is below the minimum value.
* The part inventory is above the maximum value.
* A product update would reduce associated part inventory below the minimum required level.

## Unit Testing

The project includes unit tests for the minimum and maximum inventory fields in the `PartTest` class.

The tests verify that:

* The minimum inventory field can be set and retrieved correctly.
* The maximum inventory field can be set and retrieved correctly.

## Running the Application

### Prerequisites

Make sure the following are installed:

* Java JDK
* Maven
* IntelliJ IDEA or another Java IDE

### Run with Maven

From the project root directory, run:

```bash
./mvnw spring-boot:run
```

On Windows, use:

```bash
mvnw.cmd spring-boot:run
```

### Run in IntelliJ IDEA

1. Open the project in IntelliJ IDEA.
2. Allow Maven to import project dependencies.
3. Locate the main Spring Boot application class.
4. Click Run.
5. Open the local application URL in a web browser.

The application usually runs at:

```text
http://localhost:8080
```

## WGU Requirement Change Log

The table below maps the project requirements to the files where changes were made. Line numbers should be updated after opening the project in IntelliJ IDEA or VS Code and checking the current file locations.

| Requirement | Prompt Summary                                                                 | File Name                                                                                    | Line Number(s)     | Change Summary                                                                                                                  |
| ----------- | ------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------- | ------------------ | ------------------------------------------------------------------------------------------------------------------------------- |
| C           | Customize the HTML user interface for the customer application.                | `src/main/resources/templates/mainscreen.html`                                               | Update line number | Customized the main screen for the Guitars & Gear shop, including shop branding, product names, part names, and interface text. |
| D           | Add an About page with navigation to and from the main screen.                 | `src/main/resources/templates/about.html`                                                    | Update line number | Added an About page describing the guitar shop.                                                                                 |
| D           | Add navigation to the About page and back to the main screen.                  | `src/main/resources/templates/mainscreen.html` and `src/main/resources/templates/about.html` | Update line number | Added navigation links between the main inventory page and the About page.                                                      |
| D           | Add controller support for the About page.                                     | `src/main/java/.../controllers/AboutController.java`                                         | Update line number | Added routing logic for the About page.                                                                                         |
| E           | Add sample inventory appropriate for the selected store.                       | `src/main/java/.../bootstrap/BootStrapData.java` or sample data loader file                  | Update line number | Added five guitar-related parts and five guitar-related products.                                                               |
| E           | Ensure sample inventory only loads when part and product lists are empty.      | `src/main/java/.../bootstrap/BootStrapData.java` or sample data loader file                  | Update line number | Added conditional logic to prevent duplicate sample inventory from loading.                                                     |
| F           | Add a Buy Now button to the product list.                                      | `src/main/resources/templates/mainscreen.html`                                               | Update line number | Added a Buy Now button next to the product update and delete buttons.                                                           |
| F           | Decrement product inventory after purchase.                                    | `src/main/java/.../controllers/BuyProductController.java` or product controller file         | Update line number | Added purchase logic that reduces product inventory by one when inventory is available.                                         |
| F           | Display success or failure purchase messages.                                  | `src/main/resources/templates/mainscreen.html` and product controller file                   | Update line number | Added user messages for successful and failed purchase attempts.                                                                |
| G           | Add minimum and maximum inventory fields to the part entity.                   | `src/main/java/.../domain/Part.java`                                                         | Update line number | Added `minInv` and `maxInv` fields with getters and setters.                                                                    |
| G           | Modify sample inventory to include minimum and maximum values.                 | `src/main/java/.../bootstrap/BootStrapData.java` or sample data loader file                  | Update line number | Updated sample parts to include minimum and maximum inventory values.                                                           |
| G           | Add minimum and maximum inventory inputs to the in-house part form.            | `src/main/resources/templates/InhousePartForm.html`                                          | Update line number | Added form fields for minimum and maximum inventory.                                                                            |
| G           | Add minimum and maximum inventory inputs to the outsourced part form.          | `src/main/resources/templates/OutsourcedPartForm.html`                                       | Update line number | Added form fields for minimum and maximum inventory.                                                                            |
| G           | Rename the persistent storage file.                                            | `src/main/resources/application.properties`                                                  | Update line number | Updated the database or storage file name.                                                                                      |
| G           | Enforce inventory between minimum and maximum values.                          | `src/main/java/.../validators/` and/or controller files                                      | Update line number | Added validation logic to enforce inventory limits.                                                                             |
| H           | Display error message when inventory is below minimum.                         | Part form templates and validation files                                                     | Update line number | Added validation messages for inventory below the minimum value.                                                                |
| H           | Display error message when product updates lower part inventory below minimum. | Product controller and/or validator files                                                    | Update line number | Added validation to prevent product changes from reducing part inventory below minimum.                                         |
| H           | Display error message when inventory is above maximum.                         | Part form templates and validation files                                                     | Update line number | Added validation messages for inventory above the maximum value.                                                                |
| I           | Add at least two unit tests for minimum and maximum fields.                    | `src/test/java/.../PartTest.java`                                                            | Update line number | Added unit tests for minimum and maximum inventory fields.                                                                      |
| J           | Remove unused validator classes.                                               | `src/main/java/.../validators/`                                                              | Update line number | Removed unused validator classes to clean up the project.                                                                       |

## Future Enhancements

Possible improvements for this project include:

* Modernize the frontend with React, Angular, or a more polished Thymeleaf design
* Add product images
* Add search and filtering for parts and products
* Add customer-facing product package pages
* Add shopping cart functionality
* Add role-based admin access
* Add REST API endpoints
* Replace the H2 database with PostgreSQL or MySQL
* Add Docker support
* Add expanded test coverage
* Add deployment configuration
* Add inventory reports and low-stock alerts

## Portfolio Notes

This project demonstrates experience with:

* Java backend development
* Spring Framework application customization
* MVC architecture
* Object-oriented programming
* HTML frontend customization
* Form validation
* Inventory management logic
* Maven project structure
* Unit testing
* Git and GitHub version control

## Academic Note

This project was originally completed for academic purposes and intended for personal learning, portfolio development, and future project expansion.

## Author

Drum Holliday

## License

This project is currently for educational and portfolio purposes. A formal license can be added later if the project is prepared for public reuse.
