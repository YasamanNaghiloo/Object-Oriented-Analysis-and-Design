# Stuff-lending-system-design
Domain modeling for stuff lending system to:

- grasp the use of conceptual classes in domain modeling
- know how to use attributes in conceptual classes
- know how to relate conceptual classes with each other
- know the difference between analysis and design
- know the difference between a UML design class diagram and a UML domain model class diagram
- can create a model for a basic problem

## Domain model
![image](https://github.com/user-attachments/assets/dbdcc2f3-1318-44ef-94af-fda4fe72d4e7)


This is our diagram representing the lending system described in our grade two task. This diagram
contains five classes: Admin, DayCount, Contract, Customer, and Item. These are all the essential
parts of the lending system, covering the primary components in the system. These parts are the item
itself, the customers borrowing and owning items, contracts containing terms for the borrowing of the
items including the day count, and admin who controls the entire system (ex. the advance day count
command).

## Classes:

● Admin: The Admin class represents the system's administrative user, responsible for managing
overall system operations. This includes overseeing item listings and general application
oversight, membership records, and handling specific tasks such as advancing the system's day
count.


● Customer: The customer class represents any member of the site with intentions to participate in
transactions through the means of the contract, by either lending an item to another customer, or
being lent items from another customer.


○ Attribute in Customer → credit (Integer): Customers are to use credits to perform
transactions, gaining them with every item they list to to be lent on the site, and using them
to be lent items.


● DayCount: The day count is used as the means to track how long an item has been lended, and
when it should be returned in accordance with its contract.


● Contract: The contract is required in any transaction for both customers to participate in,
stipulating precise terms for the lending of whatever item or items it applies to, including but not
limited to day count which determines when each item should be returned to its owner.


○ Attribute in Contract → expiryDate (Date): This is a Date type attribute in order to
formalize and clarify the clauses of contract between two parties.


● Item: The item class represents the physical items which are to be lent using the stuff lending
system.


○ Attribute in Item → availability (Boolean): This attribute tracks whether or not an item is
available to be lent, and will be updated in real time to display an accurate status of the
item for practical usage.


## Associations:

Admin — DayCount:
● Association: The day count advancement is triggered by the admin, who uses an “advance day
count command.” All day counts require an admin to advance them.


● Multiplicity:


○ An Admin can advance zero or many (0..*) DayCounts.


○ Each DayCount is advanced by exactly one (1) Admin.


● Rationale: There is only one admin (not directly stated but logically implied), who advances zero
to many day counts depending on how many items are currently lent out.
DayCount — Contract


● Association: A contract is validated by the day count. Every contract is required to have a day
count, but not all day counts require a contract.


● Multiplicity:


○ A DayCount can validate zero or many (0..*) Contracts.


○ Each contract is validated by exactly one (1) day count.


● Rationale: Each contract has only one set day count, but multiple contracts (with different
stipulations) may share the same day count. Therefore, the same day count can apply to zero or
many contracts, depending on the items borrowed.


Customer — Contract
● Association: Customers must participate in a contract outlining the details and terms of the
transaction.


● Multiplicity:

○ Two (2) Customers participate in each Contract.

○ Each Customer can participate in zero or many (0..*) Contracts.

● Rationale: Each transaction involves two customers—the one borrowing and the one lending the
item. A customer can be involved in lending or borrowing multiple items at the same time,
meaning they may participate in zero or many contracts, depending on the number of items they
are lending or borrowing.


Contract — Item

● Association: A contract must contain one or more items, as it outlines the terms and conditions
governing their lending. All items listed for borrowing must be contained within a contract.

● Multiplicity:

○ A Contract contains one or many (1..*) Items.

○ Each Item is contained in exactly one (1) Contract.

● Rationale: Every item available for lending must be governed by a specific contract, preventing
an item from being bound to more than one contract (or none), ensuring that terms are clear and
enforceable.


Customer — Item

● Association(1): The customer borrows an item(s).

● Multiplicity:

○ A Customer can borrow zero or many (0..*) Items.

○ Each Item can be borrowed by zero or one (0..1) Customer.

● Rationale: Every item listed on the site can be borrowed by only one customer (or none if it
remains listed), and each customer may borrow many items.

● Association(2): Customer owns item(s).

● Multiplicity:

○ A Customer can own zero or many (0..*) Items.

○ Each Item can be owned by one (1) Customer.

● Rationale: Each item listed on the site will only have one owner, and each user can either own as
many as items that they want or no items at all.

