# Android Junior Interview (1-3 Years Experience)

**Target**
- Junior Android Developer
- Can work independently
- Suitable for Japanese projects
- Has ownership mindset
- Potential to mentor fresher in the future

**Duration:** 60 minutes

---

# PART 1 - PROJECT EXPERIENCE & OWNERSHIP (20 points)

## Question 1: Introduce your most recent project

### Expected Answer

- Project domain
- Team size
- Responsibilities
- Technologies used

Example:

> I worked on a social networking application with about 25 members.
> My responsibility was implementing chat, notification and video call features.
> Technologies: Kotlin, MVVM, Retrofit, Firebase, Twilio.

---

### Sub Question 1

What feature did you develop from start to finish?

### Good Answer

Candidate can clearly explain:

- Requirement
- Design approach
- API integration
- Testing process
- Release process

### Red Flag

> I only fixed bugs.

---

### Sub Question 2

How did you estimate your tasks?

### Good Answer

> I break down tasks into UI, API integration, business logic and testing.
>
> Then estimate each part separately.

### Red Flag

> Leader estimated for me.

---

### Sub Question 3

Tell me about the most difficult bug you solved.

### Good Answer Structure

- What happened?
- How did you investigate?
- Root cause?
- Final solution?
- Lessons learned?

### Red Flag

Cannot explain root cause.

---

# PART 2 - ANDROID FUNDAMENTALS (20 points)

## Question 2: Explain MVVM

### Expected Answer

MVVM consists of:

- View
- ViewModel
- Repository
- Data Source

Flow:

UI
↓
ViewModel
↓
Repository
↓
API / Local DB

---

### Sub Question 1

Why do we need ViewModel?

### Expected Answer

- Separate UI from business logic
- Survive configuration changes
- Easier testing

---

### Sub Question 2

Can ViewModel call Retrofit directly?

### Expected Answer

No.

Recommended:

ViewModel
→ Repository
→ API

Reason:

- Easier testing
- Better separation of concerns

---

### Sub Question 3

What if data comes from both API and Room?

### Expected Answer

Repository decides data source.

Example:

- Load Room first
- Then fetch API
- Save API response into Room
- UI observes Room

---

### Sub Question 4

What repositories exist in your current project?

### Expected Answer

Real examples:

- AuthRepository
- UserRepository
- ProductRepository

Candidate should answer based on real project.

---

# Question 3: Explain Coroutine

### Expected Answer

Coroutine is a lightweight asynchronous programming solution.

Benefits:

- Non-blocking
- Easier than callbacks
- More lightweight than Thread

---

### Sub Question 1

Difference between launch and async?

### Expected Answer

launch:

```kotlin
viewModelScope.launch {}
```

Returns:

```kotlin
Job
```

async:

```kotlin
viewModelScope.async {}
```

Returns:

```kotlin
Deferred<T>
```

Used when a value needs to be returned.

---

### Sub Question 2

When should we use async?

### Expected Answer

When we need parallel tasks that return values.

Example:

```kotlin
val user = async { api.getUser() }
val products = async { api.getProducts() }

await()
```

---

### Sub Question 3

What is viewModelScope?

### Expected Answer

Coroutine scope tied to ViewModel lifecycle.

When ViewModel is destroyed:

- Coroutine gets cancelled automatically.

---

### Sub Question 4

Difference between lifecycleScope and viewModelScope?

### Expected Answer

viewModelScope

- Lives as long as ViewModel

lifecycleScope

- Lives as long as Activity/Fragment

---

# Question 4: Explain StateFlow

### Expected Answer

StateFlow is a state holder.

Example:

```kotlin
private val _state =
    MutableStateFlow(UiState())
```

---

### Sub Question 1

Why must StateFlow have an initial value?

### Expected Answer

StateFlow always contains a current state.

---

### Sub Question 2

Difference between StateFlow and SharedFlow?

### Expected Answer

StateFlow

- Has current value
- Requires initial value

SharedFlow

- Event stream
- No required initial value

---

### Sub Question 3

Should Snackbar use StateFlow or SharedFlow?

### Expected Answer

SharedFlow

Reason:

Snackbar is an event.

---

### Sub Question 4

Should Loading State use StateFlow or SharedFlow?

### Expected Answer

StateFlow

Reason:

Loading is UI state.

---

### Sub Question 5

Difference between StateFlow and LiveData?

### Expected Answer

StateFlow

- Kotlin native
- Better Compose support

LiveData

- Lifecycle aware
- Android-specific

---

# PART 3 - ANDROID PRACTICAL (20 points)

## Question 5: Design a Product List screen

API:

```json
[
  {
    "id": 1,
    "name": "Iphone",
    "price": 1000
  }
]
```

---

### Expected Architecture

```text
data/
domain/
presentation/
```

or Clean Architecture.

---

### Sub Question 1

Where should Model be placed?

### Expected Answer

domain/model

or

data/model

depending on architecture.

---

### Sub Question 2

How do you handle Loading?

### Expected Answer

```kotlin
sealed class UiState {
    object Loading
    data class Success(...)
    data class Error(...)
}
```

---

### Sub Question 3

How do you handle Error?

### Expected Answer

- Show error message
- Retry button
- Log crash if needed

---

### Sub Question 4

How do you implement Pull To Refresh?

### Expected Answer

- Trigger API again
- Update state
- Show loading indicator

---

# Question 6: Production Crash

Customer reports app crash.

How do you investigate?

---

### Expected Answer

1. Check Crashlytics
2. Analyze stacktrace
3. Reproduce issue
4. Fix
5. Regression test

---

### Sub Question 1

What information is important?

### Expected Answer

- Device
- Android version
- Stacktrace
- App version

---

### Sub Question 2

What if crash cannot be reproduced?

### Expected Answer

- Add logs
- Review code path
- Analyze Crashlytics trends

---

### Sub Question 3

What is Crashlytics?

### Expected Answer

Firebase crash reporting tool.

Provides:

- Stacktrace
- Device info
- Crash frequency

---

# Question 7: App Lag

App becomes slow when scrolling 500 items.

What would you check?

---

### Expected Answer

- RecyclerView optimization
- Image loading
- Heavy operations on Main Thread

---

### Sub Question 1

What is DiffUtil?

### Expected Answer

Calculates list differences efficiently.

Avoids full refresh.

---

### Sub Question 2

What is Paging?

### Expected Answer

Loads data in chunks instead of loading everything.

---

### Sub Question 3

How do you check Main Thread blocking?

### Expected Answer

- Android Profiler
- Logs
- StrictMode

---

# PART 4 - LIVE CODING (15 points)

## Question 8

Given:

```kotlin
data class User(
    val id: Int,
    val name: String,
    val age: Int
)
```

```kotlin
val users = listOf(
    User(1, "A", 18),
    User(2, "B", 22),
    User(3, "C", 25),
    User(4, "D", 17)
)
```

---

### Task 1

Get users age >= 18

### Answer

```kotlin
val result =
    users.filter {
        it.age >= 18
    }
```

---

### Task 2

Sort by age descending

### Answer

```kotlin
val result =
    users.sortedByDescending {
        it.age
    }
```

---

### Task 3

Return name list

### Answer

```kotlin
val names =
    users.map {
        it.name
    }
```

---

### Sub Question 1

Difference between map and filter?

### Expected Answer

filter

- Select items

map

- Transform items

---

### Sub Question 2

Difference between map and forEach?

### Expected Answer

map

- Returns new collection

forEach

- Iterates only

---

# PART 5 - MINDSET & JAPANESE PROJECTS (25 points)

## Question 9

Estimated 2 days.

Day 2 arrives but task is still unfinished.

What would you do?

### Good Answer

- Inform leader early
- Explain blockers
- Propose new estimate

### Bad Answer

> Continue silently for several more days.

---

### Sub Question

When should you report risk?

### Expected Answer

As soon as risk is identified.

Not after deadline.

---

# Question 10

You receive a task but don't fully understand the requirement.

What would you do?

### Good Answer

1. Read documents
2. Check existing implementation
3. Investigate
4. Prepare questions
5. Discuss with BA/Leader

---

### Bad Answer

> Start coding and fix later.

---

# Question 11

A fresher asks for help with a bug you don't know.

What would you do?

### Good Answer

- Help analyze
- Guide debugging process
- Escalate if needed

### Bad Answer

> Fix it for them without explanation.

---

### Sub Question

How do you mentor a fresher?

### Good Answer

- Explain thinking process
- Teach debugging
- Encourage independent investigation

---

# Question 12

Production bug occurs while leader is on leave.

What would you do?

### Good Answer

1. Gather information
2. Evaluate impact
3. Inform team
4. Suggest solution
5. Follow until resolved

---

### Sub Question

What if customer asks for progress update?

### Good Answer

> Root cause is being investigated.
>
> Current impact affects feature X.
>
> Next update will be provided in Y hours.

---

# FINAL SCORE

| Section | Score |
|----------|--------|
| Project Experience | 20 |
| Android Fundamentals | 20 |
| Android Practical | 20 |
| Live Coding | 15 |
| Mindset & Communication | 25 |
| Total | 100 |

---

# Hiring Recommendation

85+ = Strong Hire

75-84 = Hire

65-74 = Consider

<65 = Reject
