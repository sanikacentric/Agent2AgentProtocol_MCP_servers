Building a travel booking system where a user wants to book flights, hotels, or rental cars.
In this project, we simulate Travel Agents who connect to Airlines through MCP servers (web and database servers).
They communicate using messages, compare prices, and find the best option for customers.

This example shows how different parts — like dataclasses, Enums, servers, and agents — can work together cleanly in Python.

🔥 Steps Involved
1. Define Common Data Structures
We create Enums (ServiceType, MCPType, AgentStatus) to standardize service names and statuses.

A dataclass AgentMessage helps agents send structured information easily (sender, receiver, timestamp, etc.).

2. Set Up MCP Servers
The MCPServer acts like a backend server.

Based on its type (Web or Database), it knows how to respond to different requests like fetching prices.

If the server is offline, it returns an error.

3. Create Agent Cards
AgentCard represents an airline or a service provider.

Each agent has:

A web server

A database server

Services it supports (like flight, hotel)

Its own authentication token.

Agents can generate messages and validate responses from others.

4. Connect Airline Agents
AirlineAgent links an agent card to the airline operations.

It ensures requests from booking agents get passed to the right place.

5. Set Up a Booking Agent
BookingAgent acts like a travel search engine.

It contacts multiple airlines and finds the best price for flights or hotels.

It generates a request → sends it to airlines → collects responses → sorts by cheapest option.

6. Find Best Options
Using find_best_option() method:

Booking agent talks to airlines,

Gathers prices,

Picks the cheapest deal,

Shows the result to the customer.

🛠️ Example Walkthrough
In the main program:

We create two airlines (Emirates and Air India) with different prices.

We create one booking agent (TravelMaster) who connects to both airlines.

When a user wants a flight:

TravelMaster sends price-check requests.

Collects responses.

Displays cheapest flights.

👉 Example output:

yaml
Copy
Edit
Best flight options:
1. AirIndia: 250 USD
2. Emirates: 300 USD
(Hotel options show empty because Air India doesn't offer hotels.)

📝 Summary

Part	Role
ServiceType, MCPType, AgentStatus	To define standard terms
AgentMessage	To structure communication
MCPServer	To handle backend services
AgentCard	Represents a service provider
AirlineAgent	Connects airline to agents
BookingAgent	Finds best travel options
The system behaves like a mini real-world booking portal, but in a very simple and understandable way.

🏁 Conclusion
This project shows how you can simulate real-world agent communication in Python using clean coding principles like:
✅ Modular Classes
✅ Dataclasses for Messages
✅ Enum for Status Management
✅ Easy Agent Communication
✅ Smart Server Handling

Even though it’s simple, this design is very powerful to extend into a full-fledged application later (like adding real-time bookings, payment systems, etc.).

🌟 Benefits of this Design
Separation of Concerns: Each class handles its own responsibility (server, agent, booking).

Scalable: Easy to add more airlines, hotels, or rental services.

Error Handling: Servers return error messages when not available.

Structured Communication: Message passing is clear and consistent.

Mock Data: Easy to test without needing real APIs.

Real-world Practice: Mimics actual web service communication flow.
