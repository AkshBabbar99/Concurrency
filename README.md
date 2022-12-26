# Concurrency

## Ferry Problem Description (Semaphores)

The ferry offers services between two ports, port 0 and port 1. Automobiles travel between these two ports, as well as ambulance(s). Each automobile arrives at a port, boards the ferry (when it arrives at the port), crosses to the other port, disembarks the ferry, travels around for a bit, and then goes back to the port to cross again.
The ambulance is a vehicle (the automobiles and ambulance are both vehicles) that functions like the automobilewiththeexception: whenanambulanceboardstheferry,theferryleavesimmediately without waiting to be full.

The ferry travels between the two ports (0 and 1): when it arrives at a port, vehicles on board disembark first, then any waiting vehicles board. When the ferry is full, or an ambulance boards, it leaves for the other port.

* Class FerryApp is a console application that create the Ferry and all automobiles in the
simulation
* Class Auto simulates a single automobile thread
* Class Ambulance simulates a single ambulance thread
* Class Ferry simulates the ferry thread
* Interface Logger that is used to assert correct operation of the ferry

**Rules**:
1. The maximum capacity of the ferry is 5 vehicles. 
2. A vehicle at port “p” boards the ferry if
a. The ferry is at the same port p,
b. All vehicles that arrived with the ferry on board have all disembarked the ferry
c. There still exists room on the ferry for the vehicle.
3. A vehicle at port « p » must wait
a. If the ferry is not at the same port«p», 
b. Vehicles are disembarking from the ferry, 
c. The ferry is full and is ready to leave.
4. If an ambulance boards the ferry, the ferry leaves immediately.
5. If the ferry is not full and with no ambulance on board, it waits for other automobiles to arrive. 6. A vehicle can disembark only at the arrival at the next port.


## Restaurant Problem Description (DeadLock)

The restaurant application serves has a menu, each menu item is a recipe that consist of many ingredients. Customers (threads) make an order from the menu and wait till order is ready to takeout. The order is first put in a shared FIFO. The FIFO implements the producer (customer) / consumer (dispatcher) solution we discussed in class. The dispatcher (thread) consumes orders one-by-one and assign the order to one of 10 chefs working in the restaurant. Dispatcher shares a FIFO with each chef, same implementation as the order FIFO. Chefs (thread) get orders from their FIFO and start to acquire the ingredients from the kitchen. Every ingredient has a designated MUTEX to acquire, think of it as one sault container that is shared by all chefs!
Since recipe ingredients are ordered differently, a deadlock is eminent to happen when chefs compete to acquire the ingredients! Your task is to prevent that from happening.

