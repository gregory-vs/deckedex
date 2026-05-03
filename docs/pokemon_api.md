# 🧠 Pokémon TCG Card Search & Collection Manager

## 1. Context

This agent is responsible for interacting with the Pokémon TCG ecosystem using the Pokémon TCG API.

It provides capabilities for:

- Searching cards
- Filtering and querying card data
- Managing user collections
- Supporting deck building and collection tracking

This agent acts as a unified layer between external systems (frontend, services) and the Pokémon TCG API.

---

## 2. Objective

Enable systems to:

- Search Pokémon cards using flexible filters
- Combine multiple query parameters dynamically
- Retrieve paginated and sorted results
- Track owned vs missing cards
- Support deck building logic
- Provide data for collection analytics

---

## 3. External API

Base URL:
https://api.pokemontcg.io/v2

Authentication (optional but recommended):

Header:
X-Api-Key: {API_KEY}

---

## 4. Core Endpoint

GET /cards

---

## 5. Query Strategy

### 5.1 Query Language

The API uses a query format:

?q=field:value

### 5.2 Rules

- Field names are case-sensitive
- Values are generally case-insensitive
- Multiple filters are combined using space (AND logic)

---

## 6. Supported Fields

- name → Card name
- types → Pokémon type (Fire, Water, Fighting, etc.)
- hp → Hit points
- rarity → Card rarity
- set.id → Set identifier
- set.name → Set name
- supertype → pokemon / trainer / energy

---

## 7. Query Examples

Search by name:
GET /cards?q=name:lucario

Search by type:
GET /cards?q=types:fighting

Search by rarity:
GET /cards?q=rarity:rare

Search by set:
GET /cards?q=set.id:sv1

Combined filters:
GET /cards?q=name:charizard types:fire rarity:rare

Range filter:
GET /cards?q=hp:[100 TO 200]

Exact match:
GET /cards?q=name:"Lucario"

---

## 8. Pagination

Parameters:
page={number}
pageSize={number}

Example:
GET /cards?page=1&pageSize=20

Best practice:

- Always paginate
- Recommended pageSize <= 50

---

## 9. Sorting

Parameter:
orderBy=field

Descending:
orderBy=-field

Example:
GET /cards?orderBy=-hp

---

## 10. Response Structure

{
"data": [...],
"page": 1,
"pageSize": 20,
"count": 20,
"totalCount": 1000
}

---

## 11. Collection Management Logic

The agent should support:

- Marking cards as owned
- Tracking missing cards
- Calculating collection completion percentage
- Filtering owned vs unowned cards

Suggested internal endpoints:

GET /collection
GET /collection/missing
POST /collection/add
POST /collection/remove

---

## 12. Query Builder Strategy

Dynamic query construction:

const query = [
name && `name:${name}`,
type && `types:${type}`,
rarity && `rarity:${rarity}`
].filter(Boolean).join(' ')

---

## 13. Common Use Cases

Deck building:
?q=types:fighting supertype:pokemon

Collection tracking:
?q=set.id:sv1

High value cards:
?q=rarity:rare

---

## 14. Architecture Strategy

Recommended backend structure:

- API integration layer (Pokémon TCG API)
- Cache layer (Redis or database)
- Collection persistence (user-owned cards)

Suggested internal services:

- CardSearchService
- CollectionService
- DeckService

---

## 15. Best Practices

Do:

- Always use pagination
- Apply filters whenever possible
- Cache frequently accessed data
- Normalize input values

Avoid:

- Unfiltered requests (/cards without query)
- High-frequency calls without caching
- Large page sizes

---

## 16. Agent Responsibilities

The agent must:

- Build valid queries dynamically
- Enforce pagination limits
- Normalize inputs (e.g. lowercase when needed)
- Cache results when possible
- Return structured, consistent responses
- Support both search and collection workflows

---

## 17. Example Full Request

GET https://api.pokemontcg.io/v2/cards?q=types:fighting rarity:rare&page=1&pageSize=20&orderBy=-hp

---

## 18. TL;DR

- Endpoint: /cards
- Filter: q=field:value
- Combine filters with space
- Always paginate
- Main fields: name, types, rarity, set.id

---
