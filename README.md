# CastleQuest

## Introduction

Welcome to the enchanting world of Castle Quest, a captivating 2D RPG adventure that will immerse you in a thrilling quest. In this extraordinary journey, you take on the role of a courageous hero, destined to conquer the challenges that lie ahead.

Your mission is to find the elusive exit gate, hidden deep within the mystical castle. But beware, for the path is not an easy one. Fierce monsters, from lumbering zombies to mischievous slimes, guard the castle's corridors, waiting to test your mettle. With each encounter, your skills and strategic prowess will be put to the ultimate test.

Are you ready to embark on an unforgettable adventure? Prepare to be captivated by the allure of Castle Quest, where bravery, strategy, and quick thinking will guide you towards the ultimate triumph. The fate of the castle rests in your hands. Will you emerge victorious and uncover the secrets of the exit gate? The journey begins now!

## About Application

The CastleQuest application follows architectural pattern known as Model-View-Controller (MVC), ensuring a clear separation of concerns and promoting modular development practices. This architecture provides a solid foundation for managing complex game logic, user interactions, and data flow.

## Application Architecture

At the core of CastleQuest's architecture is the **Model layer**, which encapsulates the game's data and business logic. The Model layer consists of various entities, such as the Hero, NPCs, monsters, and objects, each represented by a corresponding class. These classes encapsulate the state and behavior of their respective entities, allowing for efficient data management and manipulation.

The **View layer** is responsible for rendering the game's visuals and providing a responsive user interface. It includes components such as the application frame, game frame, various panels and other UI elements. The View layer interacts with the Model layer to retrieve and display data, ensuring that the user interface remains synchronized with the underlying game state. Additionally, the View layer communicates user interactions back to the Controller layer, initiating appropriate actions and updates.

The **Controller layer** acts as the intermediary between the Model and View layers, facilitating the flow of data and orchestrating the game's behavior. It receives user input from the View layer, processes it, and updates the Model accordingly. The Controller layer also communicates with the Model layer to retrieve data and perform necessary calculations, ensuring that the game logic remains consistent and accurate. Furthermore, the Controller layer communicates with the View layer to update the visual representation of the game based on the current state.

To provide flexibility and ease of configuration, CastleQuest incorporates a dedicated **Configuration package**. This package contains Configurator that allow various managers within the Controller layer to be configured based on JSON files. The Configuration package ensures that game settings, window dimensions, hero attributes, objects settings, and other configurable aspects can be easily modified and maintained without modifying the underlying code.

In addition, CastleQuest includes a **Logging package**, which provides a Logger class responsible for logging important events, errors, and debugging information during runtime. The Logger runs alongside the application, capturing relevant log messages and storing them in a log file. This logging functionality helps in troubleshooting, performance analysis, and tracking important events within the game.

> FOR MORE DETAILED INFO ABOUT TECHNICAL PART OF THE APPLICATION PLEASE VISIT [THIS](https://gitlab.fel.cvut.cz/B222_B0B36PJV/motoslub/-/wikis/%F0%9F%94%A7-Technical-Documentation) 
