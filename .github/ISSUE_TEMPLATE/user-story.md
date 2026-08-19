---
name: User Story
about: This template defines a user story
title: ''
labels: ''
assignees: ''

---

# GiftLink — User Stories

Source: GiftLink capstone project brief (full-stack web application connecting users giving away household items with users seeking free household items).

---

## 1. Home Page

**As a** visitor
**I need** a home page with a "Get Started" button
**So that** I can begin browsing available gift listings

### Details and Assumptions
* The brief states the home page contains a "Get Started" button that takes the user to the listings page.
* Assumption: the home page itself does not require login, since login is only mentioned as a gate for the details page.

### Acceptance Criteria
```gherkin
Given I am on the GiftLink home page
When I select the "Get Started" button
Then I am taken to the listings page showing all available gifts
```

---

## 2. Browse Listings

**As a** user
**I need** to view a listings page of all available gift items
**So that** I can browse what others are giving away

### Details and Assumptions
* The brief states each item on the listings page should have a link to a details page with further information.
* Assumption: the listings page itself is viewable without logging in, since the brief only mentions requiring login when a user clicks into an item's details page.

### Acceptance Criteria
```gherkin
Given I am on the listings page
When the page loads
Then I see all available gift listings, each with a link to its details page
```

---

## 3. Navigation Bar

**As a** user
**I need** a navigation bar with links to Home, Search, Register, and Login
**So that** I can move easily between the core parts of the application

### Details and Assumptions
* The brief explicitly lists these four nav elements: register link, login link, home link, search link.
* The brief also states that once logged in, the nav bar displays the user's first name instead of the login/register links, and that logging out toggles it back.

### Acceptance Criteria
```gherkin
Given I am not logged in
When I view the navigation bar
Then I see links for Home, Search, Register, and Login

Given I am logged in
When I view the navigation bar
Then I see my first name displayed instead of the Register and Login links
```

---

## 4. Search and Filter Listings

**As a** user
**I need** to search and filter gift listings
**So that** I can find items that match what I'm looking for

### Details and Assumptions
* The brief specifies filtering by category, condition, item age, and the household item sought.
* Sample data will be provided to import into the database for testing this feature (per the brief).

### Acceptance Criteria
```gherkin
Given I am on the search page
When I enter search terms or apply filters for category, condition, or age
Then I see listings that match my search and filter criteria
```

---

## 5. Registration

**As a** new user
**I need** to register an account with my first name, last name, email, and password
**So that** I can securely access the application's features

### Details and Assumptions
* The brief states registration requires first name, last name, email, and password, and that it should be done "securely."
* Assumption: "securely" implies password handling practices such as hashing, though the brief does not specify implementation details.
* The brief notes the login page links to the register page for users who need to sign up.

### Acceptance Criteria
```gherkin
Given I am on the registration page
When I submit my first name, last name, email, and a password
Then a new account is created and I am able to log in with those credentials
```

---

## 6. Login (Authentication)

**As a** registered user
**I need** to log in with my credentials
**So that** I can access features that require authentication, like gift details

### Details and Assumptions
* The brief states authentication is handled via JSON Web Tokens (JWT) for secure communication with the database.
* The brief states that selecting a gift while not logged in redirects the user to the login screen.

### Acceptance Criteria
```gherkin
Given I am not logged in and select a gift on the listings page
When I am redirected to the login screen
Then I can enter my credentials to log in

Given I submit valid credentials on the login page
When authentication succeeds
Then I receive a JWT and am logged into the application
```

---

## 7. Logout

**As a** logged-in user
**I need** to log out of the application
**So that** my session ends and my account stays secure

### Details and Assumptions
* The brief states that selecting Logout toggles the button back to "Login," removes the displayed username, and shows a Register button in its place.

### Acceptance Criteria
```gherkin
Given I am logged in
When I select the "Logout" button
Then the button changes to "Login", my username is no longer displayed, and a "Register" button appears in the navigation bar
```

---

## 8. Gift Details Page and Comments

**As a** logged-in user
**I need** to view a gift's details page and its comments section
**So that** I can learn more about the item and communicate with other users about it

### Details and Assumptions
* The brief states the details page requires login, shows the description provided by the gifting user, and includes a comments section for communicating with others about that item.

### Acceptance Criteria
```gherkin
Given I am logged in and select a gift listing
When the details page loads
Then I see the item's description and a comments section

Given I am on a gift's details page
When I submit a comment
Then my comment appears in the comments section for other users to see
```

---

## 9. Edit User Profile

**As a** logged-in user
**I need** to view and edit my profile information
**So that** I can keep my account details, like my username, up to date

### Details and Assumptions
* The brief states selecting the user's name in the nav bar opens their profile page, where they can edit their username, and the nav bar updates accordingly.

### Acceptance Criteria
```gherkin
Given I am logged in
When I select my name in the navigation bar
Then I am taken to my profile page showing my current information

Given I am on my profile page
When I edit my username and save the change
Then my updated username is reflected in the navigation bar
```

---

## Note on Sourcing

Every statement marked as fact above is traceable to specific language in the GiftLink capstone project brief supplied for this task — no outside assumptions about GiftLink's intended behavior were introduced. Where a requirement was not explicitly stated in the brief (e.g., whether the home, listings, or search pages require login), it is labeled as an **Assumption** above rather than presented as a given requirement. If your course rubric specifies otherwise, revise the relevant story accordingly.
