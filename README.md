# Object-Oriented Design based on system requirements

A step-by-step thought process that outlines how to convert system requirements into an object-oriented design (OOD). 

## 1. Identifying Entities and Attributes
  1. Requirement Analysis: Begin by thoroughly reviewing the system requirements document. Look for nouns and noun phrases, as they often suggest potential objects or entities within the system.
  2. Domain Knowledge: Use your understanding of the domain to recognize common entities that are typically involved in similar systems. This might include both tangible items (e.g., 'Car', 'User') and intangible concepts (e.g., 'Order', 'Invoice').
  3. Abstraction: Abstract these nouns to determine whether they represent distinct objects or if they should be generalized. For instance, 'Admin User' and 'Regular User' might both be generalized into a 'User' entity.
#### Considerations:
   - Ensure the identified entities are relevant to the system’s goals.
   - Strike a balance between too granular (too many small objects) and too broad (overly generalized objects).
   - Maintain a consistent level of abstraction across all entities.

## Step 2: Defining Attributes and Behaviors

- Attribute Identification: Identify properties of each entity by looking for adjectives or descriptive phrases in the requirements. For example, a 'User' might have attributes like 'username', 'password', and 'email'.
- Behavior Identification: Determine what actions or operations each entity can perform, often indicated by verbs in the requirements. For instance, a 'User' might 'log in', 'register', or 'update profile'.
- Encapsulation: Group related attributes and behaviors together within the same entity. This ensures that an object encapsulates all the necessary data and functionality related to it.

#### Key Considerations:
  - Necessity: Ensure each attribute and behavior is necessary for fulfilling the requirements.
  - Encapsulation: Keep attributes private and expose behaviors (methods) to interact with those attributes.
  - Clarity: Behaviors should be clearly defined and aligned with the entity’s role.

## Step 3: Establishing Relationships

- Functional Analysis: Examine the system functionalities to identify how entities interact. This helps in establishing relationships such as associations, dependencies, and collaborations.
- Relationship Types: Determine the nature of these relationships:
- Association: A general connection between two entities (e.g., 'User' and 'Order').
- Aggregation/Composition: A whole-part relationship where one entity is composed of one or more other entities (e.g., 'Library' contains 'Books').
- Inheritance: A hierarchical relationship where one entity is a specialized form of another (e.g., 'AdminUser' inherits from 'User').

#### Key Considerations:

- Cardinality: Define the multiplicity of relationships (e.g., one-to-one, one-to-many).
- Directionality: Determine if the relationship is bidirectional or unidirectional.
- Dependence: Ensure that dependent objects are appropriately managed to avoid orphaned instances or memory leaks.

## Step 4: Refining the Object Model

- Validation: Cross-check the initial object model with the system requirements to ensure all functionalities are covered and the model is coherent.
- Feedback: Gather feedback from stakeholders, including developers, domain experts, and end-users to refine the model.
- Iteration: Iterate over the model to incorporate feedback and address any inconsistencies or gaps.

#### Key Considerations:

- Redundancy: Remove redundant entities or attributes.
- Consistency: Ensure consistency across the model, particularly in naming conventions and relationships.
- Complexity: Avoid unnecessary complexity; keep the model as simple as possible while meeting all requirements.

Potential Issues and Solutions:

- Ambiguities: Resolve ambiguities in requirements through discussions with stakeholders.
- Over-generalization: Avoid making entities too broad; ensure they are specific enough to handle distinct responsibilities.
- Under-specification: Ensure entities and relationships are sufficiently detailed to support all required functionalities.
- Scalability: Consider future changes and scalability in the design to avoid major refactoring.

By following these steps and considerations, you can systematically convert system requirements into an object-oriented design that accurately represents the problem domain and supports the desired system functionalities.

---

## Step-by-Step Journey of an OOD Detective: Designing a Parking Lot System

## Step 1: Identifying Entities and Attributes

To uncover real-world entities, I closely examine the requirements. I look for nouns and key concepts, and ask myself questions such as:

- Who are the main actors?
- What objects are being manipulated or used?
- What are the tangible and intangible items mentioned?

#### Entities Identification:

- ParkingLot: Manages the overall structure and operations.
- ParkingFloor: Represents each level of the parking lot.
- ParkingSpot: Individual parking spaces within floors.
- Vehicle: Represents cars, motorcycles, trucks, etc.
- Customer: Users who park their vehicles.
- Ticket: Issued to customers upon entry.
- Payment: Handles payment transactions.
- ParkingAttendant: Assists customers with payment and other services.
- EntrancePanel: Issues tickets and manages entry.
- ExitPanel: Manages payment and exit processes.
- DisplayBoard: Shows available spots and messages.
- Admin: Manages the system configuration and attendants.

#### Attributes:

For each entity, I determine relevant attributes by considering the properties needed to fulfill the requirements.

- ParkingLot: name, location, totalCapacity, floors, entrancePanels, exitPanels, displayBoards
- ParkingFloor: floorNumber, spots, displayBoard
- ParkingSpot: spotId, spotType, isOccupied, vehicle
- Vehicle: vehicleId, vehicleType, licensePlate
- Customer: customerId, name, contactInfo
- Ticket: ticketId, issueTime, paidTime, payment, vehicle
- Payment: paymentId, amount, method, status
- ParkingAttendant: attendantId, name, shift
- EntrancePanel: panelId, location
- ExitPanel: panelId, location
- DisplayBoard: boardId, location, messages
- Admin: adminId, name, permissions

## Step 2: Defining Attributes and Behaviors

To define behaviors, I look at the actions described in the requirements and consider what each entity must do to support these actions. I ask:

- What operations does each entity need to perform?
- What interactions are described in the use cases?

#### Behaviors:

- ParkingLot:
addFloor(), removeFloor(), addEntrancePanel(), addExitPanel(), displayAvailability()
- ParkingFloor:
addSpot(), removeSpot(), findAvailableSpot(), displayAvailableSpots()
- ParkingSpot:
assignVehicle(), removeVehicle()
- Vehicle:
enterLot(), exitLot()
- Customer:
takeTicket(), payTicket()
- Ticket:
calculateFee(), markPaid()
- Payment:
processPayment(), generateReceipt()
- ParkingAttendant:
assistCustomer(), processCashPayment()
- EntrancePanel:
issueTicket(), displayMessage()
- ExitPanel:
scanTicket(), processPayment()
- DisplayBoard:
updateMessage(), showAvailability()
- Admin:
configureSystem(), manageAttendants()

## Step 3: Establishing Relationships

I consider how entities need to interact to fulfill the system's functionalities. I translate system functionalities into interactions between entities, asking:

- How do entities collaborate to complete tasks?
- What kinds of relationships (association, aggregation, composition, inheritance) are appropriate?

#### Relationships:

- ParkingLot and ParkingFloor: Composition (ParkingLot contains multiple ParkingFloors).
- ParkingFloor and ParkingSpot: Composition (ParkingFloor contains multiple ParkingSpots).
- ParkingSpot and Vehicle: Association (a ParkingSpot can be occupied by a Vehicle).
- Customer and Ticket: Association (a Customer has one Ticket).
- Ticket and Payment: Association (a Ticket can have one Payment).
- ParkingLot and EntrancePanel/ExitPanel: Aggregation (a ParkingLot has multiple EntrancePanels and ExitPanels).
- ParkingFloor and DisplayBoard: Aggregation (each ParkingFloor has one DisplayBoard).
- ParkingLot and Admin: Association (an Admin configures the ParkingLot).

#### Inheritance:

- Vehicle: Base class with derived classes Car, Truck, Motorcycle, etc.
- Payment: Base class with derived classes CashPayment and CardPayment.

## Step 4: Refining the Object Model

I validate the initial model against the requirements, seeking feedback, and iterating to refine the model. I look for:

- Consistency with requirements.
- Redundancy or missing elements.
- Complexity and maintainability.

#### Validation and Refinement:

- Review Requirements: Ensure all use cases are covered.
- Feedback: Get input from stakeholders.
- Iteration: Adjust the model based on feedback.

#### Potential Issues and Solutions:

- Ambiguities: Clarify requirements with stakeholders.
- Over-generalization: Ensure entities are specific enough for their roles.
- Under-specification: Add necessary details to attributes and behaviors.
- Scalability: Design the system to handle future expansion (e.g., adding more floors or spot types).

## Final Object Model:

The final model includes well-defined entities, attributes, behaviors, and relationships, ensuring a robust and scalable design for the parking lot management system. The model is validated against the requirements, ensuring all functionalities are supported efficiently.
