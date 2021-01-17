# Design Patterns Explained with Food 🥕

GOF Design Patterns in C# with working examples inspired by food

This repository was made as a way to demonstrate and learn using moderately realistic examples of the Gang of Four Design Patterns (Design Patterns - Elements of Reusable Object-Oriented Software).

## Motivation

Many examples of these patterns as taught online typically avoid incorporating dependencies like Databases, AMQP Queues, external services for things like Email and HTTP APIs.  This makes it easier to demonstrate the core motivation of the design patterns, but also makes it more difficult to imagine real-world use cases. The projects in this repo contain mock versions of these types of dependencies incorporated into various plausible business scenarios.  The examples are intended to be lean enough so that the principal benefit of each pattern is evident, but complex enough to avoid oversimplified scenarios.

## Example Programs

Every design pattern has a corresponding .NET 5.0 console application.

| Pattern  | Type  | Example Program  | Why Used  |
|---|---|---|---|
| Abstract Factory  | Creational  | Custom Meal Planner  | We want to be able to create families of Diets with their own behavior for generating things like grocery lists and other data in an extensible fashion without specifying concrete classes in our client |
| Builder  | Creational  | Bakery Purchase Order System  | We want to separate the complex logic used to construct POs from its representation. We can provide a fluent syntax for creating new purchase orders and a seamless way to use the builder as an instance of the class its building when construction is complete.  |
| Factory Method  | Creational  | Food Delivery Service  | We want to make it easier to extend delivery type construction. We can introduce new delivery types without modifying client code.  |
| Prototype  | Creational  | Dining Room Designer  | In our graphic design application, we'd like to make it easier to create icons that are expensive to create or obtain.  We can create deep copies of protypical chair and table objects for our designer that can be used and modified independently after being cloned.  |
| Singleton  | Creational  | Ingredients Database  | We create a singleton connection pool manager that is used by different clients to connect to a database.  If more clients try to connect than the pool permits, it prevents further connection.  Uses Lazy initialization for thread safety.  |
| Adapter  | Structural  | Recipe Search  | We need to use JSON to populate a recipe document store for our website, but our favorite API returns XML.  We can use an adapter to match our required interface and use the existing resource as-is.  |
| Bridge  | Structural   | Farmer's Market Simulator  | A Farmer's Market Simulator provides different class hierarchies for types of Vendors and types of Payment Processors.  Since any vendor should be compatible with any Payment Processor, we favor composition using a bridge to develop the Vendor Abstraction from the Payment Processor Implementation independently.  |
| Composite  | Structural   | Tea Cartonizer  | We sell tea by the carton.  Cartons can contain more cartons.  We'd like to print the number of servings on the outside of any carton, even if it contains lots of other cartons.  We can use the composite pattern to treat the aggregation in the same way that we treat individual objects, exposing behavior to get the number of servings regardless of the specific object details, treating aggregations and individual objects uniformly.  |
| Decorator  | Structural  | Front-of-House Service  | We have an automated system for letting diners know when their table is ready.  By default, we make an announcement over the restaurant intercom.  However, we would like to extend the ability to notify customers by email or text, and need a way to easily add, remove, and combine these options without adding a lot of complex logic or exponentially increasing the number of subclasses. |
| Facade  | Structural  | Grocery Store Report  | The underlying service providers that help us put our Grocery Store Reports are complex and hard to use.  We want to hide that complexity behind an easy-to-use interface for use in our client code |
| Flyweight  | Structural  | Grocery Store City Planner  | As part of our city planning efforts, we want to build a grocery store in an optimal location. We are building a simulation that simulates the location and movement of our citie's inhabitants, which are represented by a number of different objects.  Some of these objects represent unchanging, static data that is shared by large portions of other inhabitants, like neighborhood and mode of travel. Some of the data is intrinsic to the inhabitant itself during the simulation, like its latitude and longitude.  A flyweight can be used to save memory during the simulation by caching the extrinsic data as a shared resource among the hundreds of thousands of inhabitant objects. |
| Proxy  | Structural  | Food Bank Donation Processor | Our Food Bank Processor uses an off-the-shelf system for accepting food donations.  However, we want to control access to this resource while maintaining the same interface.  We have the need to log use of the resource and prevent certain items from being donated, so we use a Proxy.  |
| Chain of Responsibility  | Behavioral  | Kombucha Order Processor  | Our order pipeline for kombucha customers is pretty straightforward.  We cartonize, query a loyalty program, print shipping labels if the order is online, and email or print a receipt.  Some of the details of these steps change depending on some state - like whether the order is online, whether or not the customer is a loyalty member.  For instance, we want to print ads on receipts for non-loyalty-member customers.  We can use the chain of responsibility pattern to compose and execute each stage of the order processing pipeline.  |
| Command  | Behavioral  | Composter Sign Up Form  |   |
| Interpreter  | Behavioral  |   |   |
| Iterator  | Behvavioral  | Best Restaurant Finder  |   |
| Mediator  | Behavioral  | Food Truck Coordinator  |   |
| Memento  | Behavioral  |   |   |
| Observer  | Behavioral  | Diet Plan Tracking App  |   |
| State  | Behavioral  |   |   |
| Strategy  | Behavioral  |   |   |
| Template Method  | Behavioral  | Cookbook Printer  | We run a cookbook printing business for self-published chefs.  Much of the process used to print the recpies in our cookbooks is exactly the same, but often differs slightly depending on the recipe.  We use a template method with default behavior and virtual behavior overridden (either forcibly or optionally) by concrete recipes using inheritance. |
| Visitor  | Behavioral  | Farmer's Market Research  | We work for a company that provides sales and marketing reports for regional Farmer's Markets.  Different Farmer's Markets and their vendors have their own logic for generating data we can use for our reports, but we need to be able to generate our reports without significantly modifying any of the existing data-producing classes.  We instead make them 'visitable' by our own classes, which can in turn use them as needed to generate custom reports for sales and marketing teams. |

