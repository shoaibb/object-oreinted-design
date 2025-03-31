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
