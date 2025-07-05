✅ UML Suggestions & Class Relationships
1. User Class
   Has-A (Composition):
        UserProfile profile
        UserPreferences preferences
    Uses:
        NotificationObserver (observer pattern)
        swipe(userId, swipe) uses Swipe enum and updates history: Map<String, Swipe>

2. UserProfile
   Has-A:
     Location location
     List<Interest> interests
     List<String> pictures
     Gender gender (Enum)

3. UserPreferences
   Has-A:
    List<Gender> genderInterests
    List<String> interestNames
    
4. Notification System
   Implements Observer Design Pattern:
     NotificationService (Singleton) has Map<String, NotificationObserver>
         add(observer, userId)
         notify(userId, message)
     UserNotificationObserver implements NotificationObserver

5. Matching System
   Implements Chain of Responsibility (COR):
     Matcher (interface / abstract)
        BasicMatcher
        InterestMatcher
        LocationMatcher
     Relationship:
        MatcherFactory → returns a Matcher based on MatcherType (Factory Pattern)
        DatingApp uses Matcher to compute calcScore(user1, user2)

6. Swipe and Match System
     Swipe Enum (LEFT, RIGHT)
     When both swipe RIGHT → Match created → ChatRoom is initialized

7. ChatRoom
     Has-Many:
         List<String> participantIds
         List<Message> messages

8. Message
       Has-A:
         String senderId
         Date timestamp

9. LocationService
     Provides:
         getNearbyUsers(Location, maxDistance)
     Uses:
         Location class to compute distanceInKm

📌 UML Enhancements
        Use arrows for inheritance:
            UserNotificationObserver → NotificationObserver (abstract)
        
        Use solid diamond for composition:
            User → UserProfile, UserPreferences
        
        Use solid line with arrow for usage:
            DatingApp → MatcherFactory
        
        Use dotted line for interface implementation
            UserNotificationObserver → NotificationObserver
        
        Represent multiplicity (1..*, 0..1) especially in:
            User 1..* → 0..* ChatRoom
            ChatRoom → 0..* Message
            User → 0..* Swipe

