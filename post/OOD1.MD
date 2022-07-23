---
title: "ood__PARKING LOT"
date: 2020-03-01T15:56:39+08:00
Description: 
Tags: [
    "ood","java","interview"
]
Categories: []
DisableComments: false
---
design a parking lot
<!-- more -->

## what is the model used for? use case: testing or research 

ParkingLot -- Level --ParkingSpot




## classes

+ class ParkingLot {
    List<Level> level;
}

+ class Level {
    private List<ParkingSpot> spots;
}

+ class ParkingSpot {
    Vehicle veh;
}

+ class Car extends Vehicle {
    
}

## basic function

+ #### Basic functionality: for a given vehicle, tell whether there is available spot in the parking lot

+ #### Possible extensions: provide available spot locations, assign spot to the vehicle

**Think in a high level**


```java
class ParkingLot {
    List<Level> level;
    boolean park(Vehicle v);
    boolean leave(Vehicle v);

    /** given a vehicle, tell me whether I can park it ? */
    public boolean hasSpot(Vehicle v) {
        // TODO: check each level, for each leavel, call Level#hasSpot(Vehicle v)
    }
}
```
improve code above, in Users' perspective

```java
class ParkingLot {
    List<Level> levels;

    Ticket park(Vehicle v);
    Vehicle leave(Ticket t);

    /** given a vehicle, tell me whether I can park it ? */
    public boolean hasSpot(Vehicle v) {
        // TODO: check each level, for each leavel, call Level#hasSpot(Vehicle v)
    }
}
```

high level code :up:

---

low level design 


```java
class Level {
    private List<ParkingSpot> spots;

    // provide an function for ParkingLot
    boolean hasSpot(Vehicle v);
}

```

```java
class ParkingSpot {
    Vehicle veh;

// provide an function for level
    boolean fit(Vehicle v);
}
```

```java
class Vehicle {
    getSize();
}
```

```java
 class Car extends Vehicle {
    
}
```

## complete implementation

### Assumption
#### 1. multiple level
#### 2. Check vehicle size

### API
#### boolean hasSpot(Vehicle v)
#### boolean park(Vehicle v)
#### boolean leave(Vehicle v)

```java
public enum VehicleSize{
    Compact, Large
}
```

```java
public abstract class Vehicle{
    public abstract VehicleSize getSize();
}
```

Car class

```java
public class Car extends Vehicle{
    @Override
    public VehicleSize getSize() {
        return VehicleSize.Compact;
    }
}
```
Truck class

```java
public class Truck extends Vehicle{
    @Override
    public VehicleSize getSize() {
        return VehicleSize.Large;
    }
}
```


```java
class ParkingSpot {
    private final VehicleSize size;
    private Vehicle currentVehicle;

    ParkingSpot(VehicleSize size) {
        this.size = size;
    }
// provide an function for level
    boolean fit(Vehicle v) {
        if (currentVehicle == null) {
            // Q: how to check size

        1. if -else: bad for extensions
        //    if (v.size == LARGET && this.size == COMPACT) {
        //        return false;
        // } else {
        //     return true;
        // }
        
        2. use enum ordinal: return size.ordinal() >= v.getSize().ordinal()
             //bad extension add new vehicle type, new VehicleSize enum type
        }
        
        3. Add a size attribute in enum VehicleSize and use it for comparison

    }
}
```
```java
class Vehicle {
    int size;
}
```

```java
class Level {
    private final List<ParkingSpot> spots;

    Level(int numOfSpots) {
        spots = new ArrayList<>(numOfSpots);
    }
}
```




3. call api

boolean available() {

}

get Ticket() {
    Time;
    spot;
    fee;
}

