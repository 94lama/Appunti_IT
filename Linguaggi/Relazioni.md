Le relazioni tra #tabelle sono metodi di collegamento dei #database. Si possono dividere in base al numero di collegamenti 
## #1-1
un record è in relazione con un solo record di un'altra tabella
## #1-n - Uno a molti
Un record di una tabella è in relazione con più record di un'altra tabella
**users

|id|nome|mail|
|-|-|-|
|1|mario|mario@mail|

**movies**

|id|nome|regista|user_id|
|-|-|-|-|
|1|nome_film|nome_regista|1->|

## #n-n - Molti a molti
Uno o più record di una tabella è/sono in relazione con uno o più record di un'altra tabella
es. i tag 
