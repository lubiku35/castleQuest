<br>

# CastleQuest | 2D RPG Game 


> **Author** | Ľuboslav Motošický, @lubiku35
>
> **Subject** | Programming in Java
>
> **Project Name** | CastleQuest 

## Introduction

Welcome to the enchanting world of Castle Quest, a captivating 2D RPG adventure that will immerse you in a thrilling quest. In this extraordinary journey, you take on the role of a courageous hero, destined to conquer the challenges that lie ahead.

Your mission is to find the elusive exit gate, hidden deep within the mystical castle. But beware, for the path is not an easy one. Fierce monsters, from lumbering zombies to mischievous slimes, guard the castle's corridors, waiting to test your mettle. With each encounter, your skills and strategic prowess will be put to the ultimate test.

Are you ready to embark on an unforgettable adventure? Prepare to be captivated by the allure of Castle Quest, where bravery, strategy, and quick thinking will guide you towards the ultimate triumph. The fate of the castle rests in your hands. Will you emerge victorious and uncover the secrets of the exit gate? The journey begins now!

- [CastleQuest | 2D RPG Game](#castlequest--2d-rpg-game)
  - [Introduction](#introduction)
  - [About Application](#about-application)
  - [Application Architecture](#application-architecture)
  - [Project Structure](#project-structure)
  - [Essential game features and methods](#essential-game-features-and-methods)
    - [Acummulator method](#acummulator-method)
    - [performGameLoop](#performgameloop)
    - [keyPressed](#keypressed)
    - [Collision Detection and Movement Handling Code Snippets](#collision-detection-and-movement-handling-code-snippets)
      - [Between Entity and Monster](#between-entity-and-monster)
      - [Between Entity and Entity](#between-entity-and-entity)
      - [Between Entity and Object](#between-entity-and-object)
      - [Between Entity and Tiles](#between-entity-and-tiles)


## About Application

The CastleQuest application follows architectural pattern known as Model-View-Controller (MVC), ensuring a clear separation of concerns and promoting modular development practices. This architecture provides a solid foundation for managing complex game logic, user interactions, and data flow.

## Application Architecture

At the core of CastleQuest's architecture is the **Model layer**, which encapsulates the game's data and business logic. The Model layer consists of various entities, such as the Hero, NPCs, monsters, and objects, each represented by a corresponding class. These classes encapsulate the state and behavior of their respective entities, allowing for efficient data management and manipulation.

The **View layer** is responsible for rendering the game's visuals and providing a responsive user interface. It includes components such as the application frame, game frame, various panels and other UI elements. The View layer interacts with the Model layer to retrieve and display data, ensuring that the user interface remains synchronized with the underlying game state. Additionally, the View layer communicates user interactions back to the Controller layer, initiating appropriate actions and updates.

The **Controller layer** acts as the intermediary between the Model and View layers, facilitating the flow of data and orchestrating the game's behavior. It receives user input from the View layer, processes it, and updates the Model accordingly. The Controller layer also communicates with the Model layer to retrieve data and perform necessary calculations, ensuring that the game logic remains consistent and accurate. Furthermore, the Controller layer communicates with the View layer to update the visual representation of the game based on the current state.

To provide flexibility and ease of configuration, CastleQuest incorporates a dedicated **Configuration package**. This package contains Configurator that allow various managers within the Controller layer to be configured based on JSON files. The Configuration package ensures that game settings, window dimensions, hero attributes, objects settings, and other configurable aspects can be easily modified and maintained without modifying the underlying code.

In addition, CastleQuest includes a **Logging package**, which provides a Logger class responsible for logging important events, errors, and debugging information during runtime. The Logger runs alongside the application, capturing relevant log messages and storing them in a log file. This logging functionality helps in troubleshooting, performance analysis, and tracking important events within the game.

> FOR MORE DETAILED INFO ABOUT TECHNICAL PART OF THE APPLICATION PLEASE VISIT [THIS](https://gitlab.fel.cvut.cz/B222_B0B36PJV/motoslub/-/wikis/%F0%9F%94%A7-Technical-Documentation) 

## Project Structure

```js
.
└── semester_work/  
    ├── .idea  
    ├── src/  
    │   ├── main/  
    │   │   ├── java/  
    │   │   │   └── lubiku/  
    │   │   │       └── castleQuest/  
    │   │   │           ├── Configuration/  
    │   │   │           │   ├── Configurators/  
    │   │   │           │   │   └── Configurator  
    │   │   │           │   ├── ConfigCollector  
    │   │   │           │   ├── Configurator  
    │   │   │           │   └── JSONConfigWriter  
    │   │   │           ├── Controller/  
    │   │   │           │   ├── Handlers/  
    │   │   │           │   │   ├── Utils/  
    │   │   │           │   │   │   └── EventRectangle  
    │   │   │           │   │   ├── CollisionHandler  
    │   │   │           │   │   ├── EventHandler  
    │   │   │           │   │   └── KeyHandler  
    │   │   │           │   ├── Managers/  
    │   │   │           │   │   ├── ApplicationWindowManager  
    │   │   │           │   │   ├── EnvironmentManager  
    │   │   │           │   │   ├── GameWindowManager  
    │   │   │           │   │   ├── HeroManager  
    │   │   │           │   │   ├── MapManager  
    │   │   │           │   │   ├── MonsterManager  
    │   │   │           │   │   ├── NPCManager  
    │   │   │           │   │   ├── ObjectManager  
    │   │   │           │   │   └── TileManager  
    │   │   │           │   ├── MainController  
    │   │   │           │   └── MainManager  
    │   │   │           ├── Logging/  
    │   │   │           │   └── Logger  
    │   │   │           ├── Model/  
    │   │   │           │   ├── Enemies/  
    │   │   │           │   │   ├── MonsterSlime  
    │   │   │           │   │   └── MonsterZombie  
    │   │   │           │   ├── Environment/  
    │   │   │           │   │   └── Lighting  
    │   │   │           │   ├── NPC/  
    │   │   │           │   │   └── NPC  
    │   │   │           │   ├── Objects/  
    │   │   │           │   │   ├── ChestGameObject  
    │   │   │           │   │   ├── GateGameObject  
    │   │   │           │   │   ├── HealPotionGameObject  
    │   │   │           │   │   ├── HeartGameObject  
    │   │   │           │   │   ├── KeyGameObject  
    │   │   │           │   │   ├── MapGameObject  
    │   │   │           │   │   ├── SpecialKeyGameObject  
    │   │   │           │   │   └── SpeedPotionGameObject  
    │   │   │           │   ├── Parents/  
    │   │   │           │   │   ├── Entity  
    │   │   │           │   │   ├── GameObject  
    │   │   │           │   │   ├── Monster  
    │   │   │           │   │   └── Tile  
    │   │   │           │   └── Hero  
    │   │   │           ├── View/  
    │   │   │           │   ├── Frames/  
    │   │   │           │   │   ├── AppFrame  
    │   │   │           │   │   └── GameFrame  
    │   │   │           │   ├── GameInterfaceUtils/  
    │   │   │           │   │   └── InterfaceComponents  
    │   │   │           │   ├── Panels/  
    │   │   │           │   │   ├── ChooseMapPanel  
    │   │   │           │   │   ├── LoadGamePanel  
    │   │   │           │   │   └── StartPanel  
    │   │   │           │   ├── GamePanel  
    │   │   │           │   └── UI  
    │   │   │           └── Main  
    │   │   └── resources  
    │   └── test  
    └── target  
```

## Essential game features and methods

### Acummulator method

The accumulator method is used in games to make sure the game logic runs consistently, regardless of how fast or slow the graphics are rendered. It keeps track of the time elapsed between frames and accumulates it. When enough time has passed for a game update, it performs the update, ensuring smooth and consistent gameplay.

```java
public void runAccumulatorMethod(GamePanel GAME_PANEL, Thread thread) {
        LOGGER.log("\nStarting accumulator method");
        // Accumulator method
        double drawInterval = (double) 1_000_000_000 / this.FPS;
        double accumulator = 0;
        long lastingTime = System.nanoTime();
        long currentTime;
        while (thread != null) {
            currentTime = System.nanoTime();
            accumulator += (currentTime - lastingTime) / drawInterval;
            lastingTime = currentTime;
            if (accumulator >= 1) {
                System.out.println("HER");
                this.performGameLoop(GAME_PANEL);
                accumulator--;
            }
        }
    }
```

### performGameLoop

The performGameLoop function is responsible for updating and repainting the game panel. It calls the update method of the GAME_PANEL object to perform necessary game logic updates, such as moving characters, handling collisions, or updating game state. Then, it calls the repaint method to redraw the game panel on the screen, reflecting any changes made during the update. This function ensures that the game panel stays up-to-date and visually refreshed as the game progresses.

```java 
    private void performGameLoop(GamePanel GAME_PANEL) { GAME_PANEL.update(); GAME_PANEL.repaint(); }
```

> Repaint is a method defined in the Component class, which is a superclass of GamePanel in my code. When called, repaint requests that the component be repainted at the next available opportunity. 
> It triggers a call to the component's paint method, which in turn calls the appropriate paintComponent method.

### keyPressed

The keyPressed method is a key handler function used in a game. It listens for key events and performs different actions based on the current game state. Depending on the state, it calls specific methods to handle the key press, such as handling normal gameplay, paused game state, character interactions, dialogues, title screen, map navigation, game over state, or game finished state. It also logs appropriate messages when the game over or game finished states are reached. This function ensures that different key inputs are properly handled based on the current state of the game.

```java 
    @Override
    public void keyPressed(KeyEvent e) {
        int keyCode = e.getKeyCode();
        if (this.GAME_PANEL.getGameState() == this.GAME_PANEL.getNormalGameState()) { handleNormalGameState(keyCode); }
        else if (this.GAME_PANEL.getGameState() == this.GAME_PANEL.getPausedGameState()) { handlePausedGameState(keyCode); }
        else if (this.GAME_PANEL.getGameState() == this.GAME_PANEL.getCharacterGameState()) { handleCharacterGameState(keyCode); }
        else if (this.GAME_PANEL.getGameState() == this.GAME_PANEL.getDialogueGameState()) { handleDialogueGameState(keyCode); }
        else if (this.GAME_PANEL.getGameState() == this.GAME_PANEL.getTitleScreenState()) { handleTitleScreenState(keyCode); }
        else if (this.GAME_PANEL.getGameState() == this.GAME_PANEL.getMapGameState()) { handleMapGameState(keyCode); }
        else if (this.GAME_PANEL.getGameState() == this.GAME_PANEL.getGameOverGameState()) {
            handleGameOverState(keyCode);
            GAME_PANEL.getMAIN_CONTROLLER().getLOGGER().log("GAME OVER");
        } else if (this.GAME_PANEL.getGameState() == this.GAME_PANEL.getGameFinishedGameState()) {
            handleGameFinishedState(keyCode);
            GAME_PANEL.getMAIN_CONTROLLER().getLOGGER().log("GAME FINISHED");
        }
    }
```


### Collision Detection and Movement Handling Code Snippets

The provided code snippets contains a crucial section for the game as they handles the movement and collision detection for all entities and objects present in the game. This section plays a vital role in ensuring the smooth navigation and interaction of entities with the game environment and objects.

By calling this code sections, it enable entities to move in different directions based on their assigned directions, such as up, down, left, or right. The code calculates the appropriate translation for each entity's solid area, simulating their movement across the game space.

Moreover, this code snippets includes collision detection functionality, which is essential for maintaining the integrity of game's physics and interactions. It checks for intersections between an `x's` solid area and the solid areas of `y's` within the environment. If a collision occurs, the code sets the entity's collision flag to true, indicating that a collision has taken place. This information can be used to trigger specific actions or events within game, such as scoring, damage calculation, or object interactions.

#### Between Entity and Monster
 
```java
switch (entity.getDirection()) {
    case "up" -> {
         entity.getSolidArea().translate(0, -entity.getENTITY_SPEED());
         if (checkMonsterIntersection(entity.getSolidArea(), i) ) { entity.setCollision(true);  index = i; }
    }
    case "down" -> {
         entity.getSolidArea().translate(0, +entity.getENTITY_SPEED());
         if (checkMonsterIntersection(entity.getSolidArea(), i) ) { entity.setCollision(true);  index = i; }
    }
    case "left" -> {
         entity.getSolidArea().translate(-entity.getENTITY_SPEED(), 0);
         if (checkMonsterIntersection(entity.getSolidArea(), i) ) { entity.setCollision(true); index = i; }
    }
    case "right" -> {
         entity.getSolidArea().translate(+entity.getENTITY_SPEED(), 0);
         if (checkMonsterIntersection(entity.getSolidArea(), i) ) { entity.setCollision(true); index = i; }
    }
}
```

#### Between Entity and Entity

```java
switch (entity.getDirection()) {
    case "up" -> {
        entity.getSolidArea().translate(0, -entity.getENTITY_SPEED());
        if (checkEntityIntersection(entity.getSolidArea(), target.getSolidArea())) { entity.setCollision(true); contact = true; }
    }
    case "down" -> {
        entity.getSolidArea().translate(0, +entity.getENTITY_SPEED());
        if (checkEntityIntersection(entity.getSolidArea(), target.getSolidArea())) { entity.setCollision(true); contact = true; }
    }
    case "left" -> {
        entity.getSolidArea().translate(-entity.getENTITY_SPEED(), 0);
        if (checkEntityIntersection(entity.getSolidArea(), target.getSolidArea())) { entity.setCollision(true); contact = true; }
     }
     case "right" -> {
        entity.getSolidArea().translate(+entity.getENTITY_SPEED(), 0);
        if (checkEntityIntersection(entity.getSolidArea(), target.getSolidArea())) { entity.setCollision(true); contact = true; }
     }
}
```

#### Between Entity and Object

```java
switch (entity.getDirection()) {
    case "up" -> {
        entity.getSolidArea().translate(0, -entity.getENTITY_SPEED());
        if (checkObjectIntersection(entity.getSolidArea(), i) && checkObjectCollision(i)) { entity.setCollision(true); if (isHero) { index = i; } }
    }
    case "down" -> {
        entity.getSolidArea().translate(0, +entity.getENTITY_SPEED());
        if (checkObjectIntersection(entity.getSolidArea(), i) && checkObjectCollision(i)) { entity.setCollision(true); if (isHero) { index = i; } }
    }
    case "left" -> {
        entity.getSolidArea().translate(-entity.getENTITY_SPEED(), 0);
        if (checkObjectIntersection(entity.getSolidArea(), i) && checkObjectCollision(i)) { entity.setCollision(true); if (isHero) { index = i; } }
    }
    case "right" -> {
        entity.getSolidArea().translate(+entity.getENTITY_SPEED(), 0);
        if (checkObjectIntersection(entity.getSolidArea(), i) && checkObjectCollision(i)) { 
 entity.setCollision(true); if (isHero) { index = i; } }
    }
}
```
#### Between Entity and Tiles

```java
switch (entity.getDirection()) {
    case "up" -> this.handleUpTileCollision(entity, mapBlockNumbers, entityTopWorldY, entityLeftCol, entityRightCol);
    case "down" -> this.handleDownTileCollision(entity, mapBlockNumbers, entityBottomWorldY, entityLeftCol, entityRightCol);
    case "left" ->  this.handleLeftTileCollision(entity, mapBlockNumbers, entityLeftWorldX, entityTopRow, entityBottomRow);
    case "right" -> this.handleRightTileCollision(entity, mapBlockNumbers, entityRightWorldX, entityTopRow, entityBottomRow);
        } 
```

<br>