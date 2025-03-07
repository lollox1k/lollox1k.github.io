# Operation on sets
Strarting from fondamental $\in$ relation and the axiomns of ZFC [[Axioms of set theory]] we have defined some relation/operation on sets.
Our goal here is to find the useful relations beetween them.

Siano $A,B,C$ insiemi.

#### Unions and intersections are associative:
$$
(A\cup B) \cup C = A \cup (B \cup C)
$$
$$
(A\cap B) \cap C = A \cap (B \cap C)
$$
#### They are mutually distributive:
$$
(A \cup B) \cap C = (A \cap C) \cup (B \cap C)
$$
$$
(A \cap B) \cup C = (A \cup C) \cap (B \cup C)
$$

Here we define an operation usefull in mesure theory, the _symmetric difference_
$$
A \Delta B := (A \setminus B) \cup (B \setminus A)
$$
### Equivalences
$$
A\cup B = (A\Delta B) \Delta (A \cap B)
$$
$$
A\setminus B = A \Delta (A \cap B)
$$
