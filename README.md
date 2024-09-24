# Prison Management System

This project is a **Prison Management System** built using **Object-Oriented Programming (OOP)** principles, Python, SQLAlchemy, and SQLite. The system models various aspects of a prison, such as inmates, cells, behavior records, medical records, and parole status, utilizing OOP concepts like **classes**, **inheritance**, and **relationships** between objects. It also supports populating the database with random data, exporting inmate data to CSV, and provides functionality for guards and wardens to interact with the system.

## Object-Oriented Design

This project follows an **OOP** approach, which makes it scalable, modular, and easy to maintain. Here’s how OOP principles are applied:

- **Encapsulation**: Each entity like `Inmate`, `Cell`, `Warden`, and `Guard` is encapsulated within a class, containing both data (attributes) and behavior (methods).
  
- **Abstraction**: Complex prison operations, such as behavior tracking, medical status checks, and parole approvals, are abstracted into simple methods like `get_parole_eligibility()` and `check_medical_status()`, hiding internal logic from the end user.

- **Relationships**: The relationships between entities (e.g., inmates, cells, and behavior records) are managed using SQLAlchemy’s ORM, allowing the system to reflect real-world dependencies and associations (e.g., one-to-many, many-to-one).

- **Modularity**: Classes like `Inmate`, `Cell`, `Guard`, and `Warden` are modular, allowing new functionality to be added or changed without affecting other parts of the system. The database structure is designed around the relationships between these classes.

- **Reusability**: Common actions (like assigning cells or adding behavior records) are encapsulated within classes and methods, allowing code reuse. For example, `Warden` and `Guard` classes can perform overlapping tasks, such as monitoring inmates or managing cell assignments, without duplicating code.

## Key Classes and Their Responsibilities

### Inmate Class
Represents an inmate and their behavior, medical records, sentence information, and parole status.

- **Attributes**: `name`, `age`, `crime`, `sentence_duration`, `time_served`, `medical_records`, `parole_status`, and `behavior_records`.
- **Methods**:
  - `get_parole_eligibility()`: Checks if the inmate is eligible for parole based on behavior and time served.
  - `add_behavior_record()`: Adds behavior records (good or bad) to the inmate’s profile.
  - `check_medical_status()`: Retrieves the inmate’s medical condition.
  - `transfer_cell()`: Transfers the inmate to a new cell.

### Cell Class
Represents a prison cell, containing inmates and tracking its capacity.

- **Attributes**: `cell_number`, `capacity`, `current_inmates`.
- **Methods**:
  - `add_inmate()`: Adds an inmate to the cell.
  - `remove_inmate()`: Removes an inmate from the cell.

### Warden and Guard Classes
Both represent prison staff members who interact with inmates and cells. The **Warden** class has special authority to approve parole, while the **Guard** class is responsible for monitoring behavior.

- **Warden Methods**:
  - `approve_parole()`: Determines whether an inmate is eligible for parole based on behavior records and sentence duration.
  
- **Guard Methods**:
  - `monitor_inmate()`: Logs that the guard is monitoring a specific inmate.
  - `report_behavior()`: Adds a behavior record to an inmate’s file.

### WorkAssignment Class
Manages inmate assignments to work tasks within the prison.

- **Attributes**: `assignment_name`, `assigned_inmates`.
- **Methods**:
  - `assign_inmate()`: Assigns an inmate to a specific work assignment.
  - `remove_inmate()`: Removes an inmate from the work assignment.
  - `track_progress()`: Tracks progress on the assigned work task.

---

### Why OOP?
The **OOP-based design** offers several advantages in this project:

1. **Scalability**: New features or classes can be added easily. For example, adding a `RehabilitationProgram` class would be straightforward, as it could follow the same pattern as `WorkAssignment`.

2. **Maintainability**: Changes in one class do not affect others due to clear boundaries between different modules.

3. **Code Reuse**: Shared functionality (e.g., inmate monitoring by guards or cell assignments by wardens) can be reused across multiple classes without rewriting the logic.

4. **Real-World Representation**: OOP naturally fits the prison system, where entities like `Inmate`, `Warden`, `Guard`, and `Cell` have distinct roles and relationships.
