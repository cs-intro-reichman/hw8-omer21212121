# Homework 8: Social Network - Implementation Summary

## Overview
Successfully implemented a social network system using Object-Oriented Programming principles. The implementation consists of two main classes: `User` and `Network`.

## User Class Implementation

### Methods Implemented:

1. **follows(String name)** - O(n) search
   - Searches the follows array for a given name
   - Returns true if found, false otherwise
   - Uses `.equals()` for string comparison

2. **addFollowee(String name)** - O(n) check + O(1) insert
   - Checks if user already follows the name
   - Checks if follows list is full (max 10)
   - Adds name to the end of the array and increments fCount
   - Prints appropriate feedback messages

3. **removeFollowee(String name)** - O(n) search + O(n) shift
   - Searches for the name in the follows array
   - Shifts all elements after the removed name one position up
   - Sets the last element to null and decrements fCount
   - Prints appropriate feedback messages

4. **countMutual(User other)** - O(n*m) where n,m are follow counts
   - Counts how many users both this user and the other user follow
   - Iterates through this user's follows and checks if other follows them

5. **isFriendOf(User other)** - O(n)
   - Checks if two users follow each other
   - Returns true only if both users follow each other

## Network Class Implementation

### Methods Implemented:

1. **toString()** - O(n)
   - Returns a textual representation of the network
   - Each user prints itself using User's toString() method
   - Demonstrates object-oriented design principle

2. **getUser(String name)** - O(n)
   - Searches for a user by name in the users array
   - Returns the User object if found, null otherwise

3. **addUser(String name)** - O(n) check + O(1) insert
   - Checks if network is full
   - Checks if user already exists (using getUser)
   - Creates and adds new User object

4. **addFollowee(String name1, String name2)** - O(n)
   - Validates both users exist in the network
   - Calls the User class's addFollowee method
   - Returns false if either user doesn't exist or addition fails

5. **followeeCount(String name)** - O(n*m) helper method
   - Private helper method for mostPopularUser
   - Counts how many users in the network follow the given name
   - Each user can follow a name at most once

6. **mostPopularUser()** - O(n²*m)
   - Finds the user who appears most in other users' follow lists
   - Uses followeeCount helper method for each user
   - Returns the name of the most popular user

7. **recommendWhoToFollow(String name)** - O(n²*m)
   - Recommends a user to follow based on mutual followees
   - Skips the user themselves and users already followed
   - Returns the user with the maximum mutual followee count

## Testing Results

### UserTest Output:
✅ All tests passed successfully
- toString and follows methods work correctly
- Adding and removing followees with proper validation
- Handling full follows list
- Counting mutual followees
- Checking friendship relationships

### NetworkTest Output:
✅ All tests passed successfully
- Network toString works correctly
- User lookup (getUser) works
- Adding users and followees
- Recommendation algorithm works (suggested Idan for Alex)
- Most popular user algorithm works (identified Zohar)

## Key Design Principles Applied

1. **Encapsulation**: Private fields with public methods
2. **Object Responsibility**: Users manage their own follows lists
3. **Reusability**: Network class reuses User class methods
4. **Data Integrity**: Follows arrays maintain contiguous blocks
5. **Error Handling**: Proper validation and feedback messages

## Complexity Analysis

- **Space Complexity**: O(n*m) where n = number of users, m = max follows per user
- **Time Complexity**: Most operations are O(n) or O(n²), acceptable for this scale

## Notes

- Maximum followees per user: 10 (static constraint)
- Network capacity: Set during construction (flexible)
- Follows lists maintain contiguous blocks (no gaps)
- Proper null handling when objects not found
- String comparison uses `.equals()` method throughout
