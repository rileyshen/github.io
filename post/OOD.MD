---
title: "ood"
date: 2022-02-01T15:56:39+08:00
Description: 
Tags: [
    "ood","java","interview"
]
Categories: []
DisableComments: false
---

最重要的是 balance between solution that works immediately and also adptable to change in the future

# 1. 清楚 requirement
+ discuss 
    + are you looking for me to demonstrate the structure of solution, or fully implement it

## 2. hash out the primary use cases
+ thing, talk through, use cases
    + different functionality of the system 


## 3. identify key objects

## 4. identify operations supported by objects

## 5. identify interactions between objects



### design amazon/ flipkart (online shoping platefrom)

+ Discoverability: how will the buyer discover a product? how will the search surface results, recommendation system
+ cart & checkout: innovation checkout solution like One-Click-purchase, promote discount purchase
+ payment methods: credit card, gift cards
+ product review & ratings


### design a movie ticket booking system
+ duplication: same cinema having multiple cinema halls showing different movie simultaneously, or the same movie being show at different times in the same cinema/hass

+ payment methods: how the process for a user to purchase a ticket

+ selection: how would user pick an available seat, 
+ price variances: discounted pricing(student, children)


### design an atm
+ overdrawing: when atm doesn't have any cash left
+ pin varification: enter a wrong pin multiple times
+ card reading: card has been correctly inserted or not

### design an airline management system
+ Itinerary complexity: 行程, nulti-flight itineraries, how would nultiple passengers on the same itinerary be handle

+ alerts: notify the customers when there is a change to the flight status
+ external access: this system interact with other actors making reservations to the same flights

### design blackjack

+ scoring: what level of the system is scroing handled? advantages and disadvantages

+ rules: 

+ betting

### design a hotel management system

+ room complexity: system support different room types within the same hotel

+ alerts: remind user that their check-in date is approaching...

+ customization: users make special request on their room.

+ cancellation/ modification: allowed time period




### design a parking lot

+ payment flexibility
+ capacity
+ vehicle types
+ pricing


### design an elevator

#### clarify requirement
+ 运输到不同楼层
+ 电梯状态上，下，停(才可以开门)
+ 层数不同增加电梯数量
+ elevator cab 本身 size， 最多装几个人，最多多重
+ 协调算法，全局最优，局部个人最有
+ 报警按钮，紧急
+ 电梯本身分类，货运，人运
+ 监控系统

#### divide and conquer
+ 摩天大楼场景：
    - 奇偶层
    + 1-10 层一个电梯， 10-20， 20-30， 车库一个电梯
    + 不同类别电梯： 人，货，餐车， VIP 等等





#### define class(core object)
+ Elevator System
+ elevator cab
+ floors
+ doors
+ button panel(inside floor map, outside up down)
+ dispatcher
+ monitoring/alarm



#### define field (properties)
+ Elevator System
>List<ElevatorCab>, or array of elevator position

+ elevator cab
 - state(idle, up, down)

+ Button Menu
- external/ internal
- floor map button
- up/down button



#### define method, how data flow works

data flow:
+ 外部用户按按钮 take external request --> elevator system dispatch the request to target elevator using algorithm -->

#### implementing core method
+ Fist come First Serve, 
+ priorityQueue/minHeap: base 用户位置和电梯位置
+ scan 在有用户的 floor 来听， hashmap 记录哪个楼层有用户按按钮
+ look，如果

#### optimize with design pattern




### design an online stock brokerage system
+ watchlists
+ transaction types (stop loss and stop limit order)
+ stock lots
+ reporting


### design a car rental system
+ Identification: each vehicle be uniquely identified and located within the parking garage
+ logs: system maintain a log for each vehicle and for each member
+ fee: collect a late fee for late returns
+ customization: members' request for additonal services like roadside assistance, full insurance, and GPS
### design facebook
+ Discovrability: users able to search other users' profiles
+ following: able to follow/unfollow other users without becoming a direct connection
+ gruop/pages: create both groups and pages in addition to their own user profiles
+ privacy: handle privacy lists with certain content to be display only to specified connections
+ alerts: how will users be notified for pre-selected events

### Design a hash map
要考虑实现的功能
- size()
- isEmpty()
- chear()
- put(K key, V value)
- get(K key)
- containsKey(K key)
- containsValue(V value)
- remove(K key)


- array of entries
- each entry is actually a single linked list
    - contains the <key, value> pair

```java
public class MyHashMap<k, v> {

    public static class Node(K, V) {
        final k key;
        v value;
        Node<k, v> next;
        Node(k key, v value) {
            this.key = key;
            this.value = value;
        }
        public K getKey() {
            return key;
        }
        public V getValue() {
            return value;
        }
        public V setValue() {
            this.value = value;
        }
    }

    public static final int DEFAULT_CAPACITY = 16;
    public static final int DEFAULT_LOAD_FACTORY = 0.75f;
    
    private Node<K, V> array;
    private int size;
    private float loadFactory;

    public MyHashMap() {
        this()
    }

}

// init

```