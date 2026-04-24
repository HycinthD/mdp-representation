# MDP REPRESENTATION

## AIM:
To model the movement of the robot vaccum cleaner in a 2 room environment using Markov Decision Process(MDP).

## PROBLEM STATEMENT:
Robot Vaccum Cleaner

### Problem Description
A robot vaccum cleaner moves between two rooms (room0 and room1).It can CLEAN the room or move to the other room.Each Action gives Gives A reward : Cleaning a dirty room gives +10 , moving has a cost of -1, and trying to clean an already clean room gives 0

### State Space
States represent the location of the robot and cleanliness of each room: (robot_location, room0_status, room1_status) 

 robot_location = 0 (Room 0) or 1 (Room 1)
 
 room_status = 0 (dirty) or 1 (clean)

### Sample State

(0, 0, 1) -> Robot is in Room 0

Room 0 is dirty

Room 1 is clean

### Action Space
0 -> CLEAN 1 -> MOVE

### Sample Action

CLEAN - Cleans the current room

MOVE - Moves to the other room


### Reward Function

CLEAN dirty room -> +10

CLEAN clean room -> 0

MOVE -> -1

### Graphical Representation

<img width="931" height="522" alt="image" src="https://github.com/user-attachments/assets/baf1716e-da59-488a-be54-17239cfdad0d" />



## PYTHON REPRESENTATION:
```
Name: HYCINTH D
Reg No: 212223240055
# Robot Vacuum Cleaner MDP
P = {
    (0, 0, 0): {  # Robot in Room 0, both rooms dirty
        0: [(1.0, (0, 1, 0), 10, False)],  # CLEAN Room0
        1: [(1.0, (1, 0, 0), -1, False)]   # MOVE to Room1
    },
    (0, 1, 0): {  # Robot in Room 0, Room0 clean, Room1 dirty
        0: [(1.0, (0, 1, 0), 0, False)],   # CLEAN Room0 already clean
        1: [(1.0, (1, 1, 0), -1, False)]   # MOVE to Room1
    },
    (1, 0, 0): {  # Robot in Room1, both rooms dirty
        0: [(1.0, (1, 0, 1), 10, False)],  # CLEAN Room1
        1: [(1.0, (0, 0, 0), -1, False)]   # MOVE to Room0
    },
    (1, 0, 1): {  # Robot in Room1, Room0 dirty, Room1 clean
        0: [(1.0, (1, 0, 1), 0, False)],   # CLEAN Room1 already clean
        1: [(1.0, (0, 0, 1), -1, False)]   # MOVE to Room0
    },
    (0, 1, 1): {  # Both rooms clean, Robot in Room0
        0: [(1.0, (0, 1, 1), 0, True)],    # CLEAN → terminal
        1: [(1.0, (1, 1, 1), -1, True)]   # MOVE → terminal
    },
    (1, 1, 1): {  # Both rooms clean, Robot in Room1
        0: [(1.0, (1, 1, 1), 0, True)],    # CLEAN → terminal
        1: [(1.0, (0, 1, 1), -1, True)]   # MOVE → terminal
    }
}

print(P)
```

## OUTPUT:
```
{(0, 0, 0): {0: [(1.0, (0, 1, 0), 10, False)], 1: [(1.0, (1, 0, 0), -1, False)]}, 
 (0, 1, 0): {0: [(1.0, (0, 1, 0), 0, False)], 1: [(1.0, (1, 1, 0), -1, False)]},
 (1, 0, 0): {0: [(1.0, (1, 0, 1), 10, False)], 1: [(1.0, (0, 0, 0), -1, False)]},
 (1, 0, 1): {0: [(1.0, (1, 0, 1), 0, False)], 1: [(1.0, (0, 0, 1), -1, False)]},
 (0, 1, 1): {0: [(1.0, (0, 1, 1), 0, True)], 1: [(1.0, (1, 1, 1), -1, True)]},
 (1, 1, 1): {0: [(1.0, (1, 1, 1), 0, True)], 1: [(1.0, (0, 1, 1), -1, True)]}}
```

## RESULT:
Thus, the robotic vaccum cleaner problem is successfully represented in MDP form.

