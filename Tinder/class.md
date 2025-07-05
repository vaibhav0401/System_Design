1. User
        notificationObserver: NotificationObserver
        preferences: UserPreferences
        profile: UserProfile

    Methods:
        swipe(userId: String, swipe: Swipe)
        hasLiked(userId: String): boolean
        isInterestedIn(userId: String): boolean

   2. UserProfile
        name: String
        bio: String
        age: int
        gender: Gender
        location: Location
        interests: List<Interest>
        pictures: List<String>

      3. UserPreferences
          minAge: int
          maxAge: int
          maxDistance: double
          interestNames: List<String>
          genderInterests: List<Gender>

         4. Notification System
              Observer Design Pattern
              NotificationService (Singleton)
                  observers: Map<String, NotificationObserver>
                  addObserver(observer: NotificationObserver, userId: String)
                  remove(userId: String)
                  notify(userId: String, message: String)
                  notifyAll(message: String)
                  NotificationObserver (abstract class/interface)
                  update(userId: String, message: String)

5. Matching System
      COR (Chain of Responsibility)
      Matcher (interface or abstract)
          calculateScore(user1: User, user2: User): double
      Implementations:
          BasicMatcher
          InterestMatcher
          LocationMatcher

   6. MatcherFactory
        Returns a matcher instance:
           getMatcher(type: MatcherType): Matcher
        MatcherType enum:
           BASIC, INTEREST, LOCATION

7. Swipe
   Enum: LEFT, RIGHT

8. ChatRoom
    id: String
    participantIds: List<String>
    messages: List<Message>

9. Message
    senderId: String
    content: String
    timestamp: DateTime

10. Location
        latitude: double
         longitude: double
         address: String
         distanceInKm(other: Location): double

11. Interest
        name: String
        description: String
        category: String