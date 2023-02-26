# 206 Graphs

## Introduction

In this chapter, we will take our collections to the next dimension. Literally. We'll look at how to store collections of information that is more complex than a simple ordered List of objects.

Think for example of a digital representation of Stockholm's Metro Network:

<img width="711" alt="image" src="https://user-images.githubusercontent.com/7360266/152983698-22fb9246-311b-4470-bef2-49442e330057.png">

You could store the information in multiple Arrays, maybe:

```cs
Station[] T13 = new Station[] {
   Norsborg, Hallunda, Allby, ...
};
Station[] T14 = new Station[] {
   Fruängen, Västertorp, ...
};
```

But then, if you wanted to see, where you can go from T-Centralen, you'd have to run over all lists to check, whether your station is part of that line:

<details>
  <summary>Pseudo-Code</summary>

```
Procedure find_connected_stations
   lines ← array of all lines
   startStation ← station to search connections for
   result ← empty array of stations

   for each line in lines
      for each station in line
         if station = startStation
            add previousStation to result
            add nextStation to result
         end if
      end for
   end for

   return result
end procedure
```

</details>

That would be the equivalent of looking at multiple separate maps for each line and requiring to find your station in each of those:

<img src ="https://stockholmmetro.com/assets/images/green-line.jpg">

Pretty annoying, or? The original map is much more useful. As soon as you found your station, you can see all connections at one glance:

```cs

public class Connection {
   public Station target;
   public Line line;
   public Station source;
}

public class Station {
   public string name;
   public Connection[] connections;
}
```

We'll look at how we can define a structure like this in code and use it to structure a very useful type of collection for sorted data.

## Passing Criteria
There is no passing criteria associated with this course. This information will be validated through the Pathfinding exercises.

## Excellent Criteria
There is no passing criteria associated with this course. This information will be validated through the Pathfinding exercises.

## Bonus
Design a Graph for (a part of) Stockholm's Subway System. There is:
- Stations
  - With Names
- Connections
  - From one Station to another Station
  - With a Name for the Line you're taking
  - And a Duration, how long it'd take

Now, implement a small application where you start at T-Centralen and:
- It prints all possible connections from here
- You can choose, which one to take
- Then, it updates your current station
- And repeats (loops back)

Example Output:
```
You're at T-Centralen. Possible Connections:
0: T14 to Gamla Stan (2 Minutes)
1: T17 to Gamla Stan (2 Minutes)
2: T14 to Östermalmstorg (3 Minutes)
3: T17 to Hötorget (4 Minutes)
Which  one do you want to take?
Input: 1
You're at Gamla Stan. Possible Connections:
...
```