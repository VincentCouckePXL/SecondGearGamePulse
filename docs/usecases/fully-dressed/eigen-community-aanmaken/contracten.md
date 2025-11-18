## **Contract: Community.addUser()**

| Field | Content |
|-------|---------|
| **Operation** | addUser(user: User) |
| **Cross-References** | Use Case: Aanmaken van een Eigen Community |
| **Preconditions** | 1. Er bestaat een Community.<br>2. De User is niet geblokkeerd.<br>3. De User is niet reeds lid van de Community. |
| **Postconditions** | - [Association formed] De User is toegevoegd aan `Community.users`.<br>- [Association formed] De Community is toegevoegd aan `User.joinedCommunities`. |

---

## **Contract: Community.addAdmin()**

| Field | Content |
|-------|---------|
| **Operation** | addAdmin(user: User) |
| **Cross-References** | Use Case: Aanmaken van een Eigen Community |
| **Preconditions** | 1. Er bestaat een Community.<br>2. De User is lid van de Community.<br>3. De User is niet reeds een admin. |
| **Postconditions** | - [Association formed] De User is toegevoegd aan `Community.admins`.<br>- [Attribute modification] De adminlijst van de Community is bijgewerkt. |

---

## **Contract: Community.addTag()**

| Field | Content |
|-------|---------|
| **Operation** | addTag(tag: Tag) |
| **Cross-References** | Use Case: Aanmaken van een Eigen Community |
| **Preconditions** | 1. Er bestaat een Community.<br>2. De tag is een geldige Tag enum-waarde.<br>3. De tag is niet reeds toegevoegd aan de Community. |
| **Postconditions** | - [Association formed] De Tag is toegevoegd aan `Community.tags`. |

---

## **Contract: Community.setImage()**

| Field | Content |
|-------|---------|
| **Operation** | setImage(image: Image) |
| **Cross-References** | Use Case: Aanmaken van een Eigen Community |
| **Preconditions** | 1. Er bestaat een Community.<br>2. De image voldoet aan formaat- en grootte-eisen (jpg/png/webp, < 5MB). |
| **Postconditions** | - [Association formed] De Image is gekoppeld aan `Community.communityImage`.<br>- [Attribute modification] De community-afbeelding is bijgewerkt. |

---

## **Contract: User.addCommunity()**

| Field | Content |
|-------|---------|
| **Operation** | addCommunity(community: Community) |
| **Cross-References** | Use Case: Aanmaken van een eigen Community |
| **Preconditions** | 1. Er bestaat een User.<br>2. Er bestaat een Community.<br>3. De User is niet reeds lid van de Community. |
| **Postconditions** | - [Association formed] De Community is toegevoegd aan `User.joinedCommunities`.<br>- [Association formed] De User is toegevoegd aan `Community.users`. |

---

## **Contract: Game.addCommunity()**

| Field | Content |
|-------|---------|
| **Operation** | addCommunity(community: Community) |
| **Cross-References** | Use Case: Aanmaken van een Eigen Community |
| **Preconditions** | 1. Er bestaat een Game.<br>2. Er bestaat een Community.<br>3. De Community is nog niet gekoppeld aan de Game. |
| **Postconditions** | - [Association formed] De Community is toegevoegd aan `Game.communities`.<br>- [Attribute modification] De community-lijst van de Game is bijgewerkt. |