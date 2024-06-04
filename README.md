# Spring JPA and Inheritance: Dungeons and Dragons Edition

In this exercise, you will practice different strategies of inheritance using Spring JPA in the context of a Dungeons and Dragons game. You will work with entities representing characters and items in the game.

## Instructions

1. Set up a new Spring Boot project with the necessary dependencies for Spring JPA and a database of your choice (e.g., H2, MySQL).

2. Create the following entity classes:
   - `Character` (abstract base class)
     - `id` (Long)
     - `name` (String)
     - `level` (int)
     - `attack()` (abstract method)
   - `Player` (extends `Character`)
     - `characterClass` (String)
     - `race` (String)
     - Implement the `attack()` method specific to players
   - `Monster` (extends `Character`)
     - `monsterType` (String)
     - `hitPoints` (int)
     - Implement the `attack()` method specific to monsters
   - `Item` (abstract base class)
     - `id` (Long)
     - `name` (String)
     - `use()` (abstract method)
   - `Weapon` (extends `Item`)
     - `damage` (int)
     - `weaponType` (String)
     - Implement the `use()` method specific to weapons
   - `Armor` (extends `Item`)
     - `defense` (int)
     - `armorType` (String)
     - Implement the `use()` method specific to armor

3. Implement the following inheritance strategies:
   - Use the joined table strategy for the `Character` entity hierarchy (`Player` and `Monster`).
   - Use the single table strategy for the `Item` entity hierarchy (`Weapon` and `Armor`).

4. Create repository interfaces for each entity using Spring Data JPA.

5. Create a `CharacterService` class with the following methods:
   - `createPlayer(String name, String characterClass, String race, int level)`: Creates a new player character.
   - `createMonster(String name, String monsterType, int hitPoints, int level)`: Creates a new monster character.
   - `equipWeapon(Long characterId, Long weaponId)`: Equips a weapon to a character. This method should only log a message saying "Weapon equipped" without modifying the database.
   - `equipArmor(Long characterId, Long armorId)`: Equips armor to a character. This method should only log a message saying "Armor equipped" without modifying the database.
   - `attackWithCharacter(Long characterId)`: Invokes the `attack()` method of a character.

   The `CharacterService` class should use the repository interfaces to persist and retrieve data from the database.

6. Create a `DataLoader` class that implements the `CommandLineRunner` interface. In the `run()` method, use the `CharacterService` to perform the following actions:
   - Create a few player characters and monster characters.
   - Create a few weapons and armor pieces.
   - Equip weapons and armor to characters. This should only result in logging messages.
   - Invoke the `attack()` method of characters.

## Additional Tasks

- Implement a `SpecialAbility` abstract class with a `perform()` method, and create subclasses `MagicSpell` and `PhysicalAbility` that extend `SpecialAbility`. Use the table-per-class strategy for this hierarchy.
- Extend the `CharacterService` to include methods for assigning special abilities to characters and invoking their `perform()` methods.

## Submission

- Create a GitHub repository for your project and push your code.
- Provide a README file with instructions on how to run the application and test the functionality.
- Submit the link to your GitHub repository.

Embark on this coding adventure and may your inheritance strategies be victorious!
