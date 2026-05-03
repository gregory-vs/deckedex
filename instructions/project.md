# 🧠 Pokémon TCG Deck Builder (Laravel + Next.js + MUI)

## 1. Context

This agent is responsible for building and maintaining a web application for managing Pokémon TCG decks.

The system allows users to:

- Register and authenticate
- Search Pokémon cards using an external API
- Create and manage decks
- Add and remove cards from decks
- Import cards via clipboard
- Filter and visualize deck compositions

Architecture:

- Backend: Laravel (REST API + business logic)
- Frontend: Next.js (React framework)
- UI Library: Material UI (MUI)

External dependency:

- Pokémon TCG API (see pokemon_api.md)

---

## 2. Objective

The agent must implement an MVP that enables:

- User authentication (login + register)
- Deck creation and management
- Card search via external API
- Card selection and clipboard import
- Deck visualization and filtering

---

## 3. Tech Stack

### Backend

- Laravel (REST API)
- MySQL or PostgreSQL
- Cache (optional, recommended)

### Frontend

- Next.js (App Router)
- React
- Material UI (MUI)
- Axios or Fetch API

---

## 4. High-Level Architecture

[ Next.js Frontend ]
↓
[ Laravel API ]
↓
[ Pokémon TCG API ]
↓
[ Database ]

---

## 5. Core Features

### 5.1 Authentication

- User registration (email + password)
- User login (email + password)
- Token-based authentication (recommended: JWT or Laravel Sanctum)

---

### 5.2 Deck Management

Users must be able to:

- Create a new deck
- Delete a deck
- View all decks
- View deck details

---

### 5.3 Card Management in Deck

Within a deck:

- Add cards individually
- Remove cards individually
- View cards in the deck

---

### 5.4 Clipboard Import

User can paste a list of card names.

Flow:

1. Parse input (split by line)
2. Normalize values
3. Search each card via API
4. Add matched cards to the deck

---

### 5.5 Card Search

Must support:

- Search by name
- Filter by type
- Filter by rarity
- Filter by set

Uses Pokémon TCG API (pokemon_api.md)

---

### 5.6 Deck Visualization

Deck screen must:

- Display cards with images
- Show card info
- Allow filtering

Filters:

- Pokémon type (Fire, Water, etc.)
- Card category:
  - Pokémon
  - Trainer (supporter)
  - Energy
- Name search

---

## 6. Backend Design (Laravel)

### 6.1 Entities

#### Users

- id
- email
- password

#### Decks

- id
- name
- user_id

#### Deck_Cards

- id
- deck_id
- card_id (external API id)
- name
- image

---

### 6.2 API Endpoints

#### Auth

POST /auth/register  
POST /auth/login

#### Decks

GET /decks  
POST /decks  
GET /decks/{id}  
DELETE /decks/{id}

#### Deck Cards

POST /decks/{id}/cards  
DELETE /decks/{id}/cards/{cardId}

#### Search

GET /cards/search

---

### 6.3 Services

- CardSearchService → integrates Pokémon API
- DeckService → business logic
- AuthService → authentication

---

## 7. Frontend Design (Next.js + MUI)

### 7.1 Routing (App Router)

- /login
- /register
- /decks
- /decks/[id]
- /search

---

### 7.2 UI Components (MUI)

Use Material UI components:

- Container
- Grid
- Card
- CardMedia
- CardContent
- TextField
- Button
- Select
- Chip
- Dialog

---

### 7.3 Pages

#### Auth

- Login page
- Register page

#### Decks

- Deck list
- Deck detail
- Create deck modal/page

#### Search

- Search interface with filters

---

### 7.4 Components

- CardItem
- CardList
- SearchBar
- FiltersPanel
- DeckBuilder
- ClipboardImport

---

### 7.5 State Management

- React hooks (useState, useEffect)
- Optional: Context API

Manage:

- Auth state
- Decks
- Selected deck
- Search results

---

## 8. Clipboard Import Strategy

Input:

Pikachu  
Charizard  
Lucario

Steps:

1. Split lines
2. Trim values
3. Query API for each
4. Add to deck

---

## 9. Filtering Logic

Filters must support:

- Card type:
  - Pokémon
  - Trainer
  - Energy

- Pokémon type:
  - Fire, Water, Fighting, etc.

- Name search

---

## 10. External API Usage

Follow pokemon_api.md rules:

- Endpoint: /cards
- Use query param `q`
- Combine filters with space
- Always paginate

---

## 11. Best Practices

### Backend

- Use service layer
- Validate requests
- Cache API responses

### Frontend

- Debounce search input
- Use loading states
- Avoid unnecessary renders

---

## 12. Non-Goals (MVP)

- No deck validation rules
- No competitive meta analysis
- No social features

---

## 13. Agent Responsibilities

The agent must:

- Implement backend and frontend features
- Integrate correctly with external API
- Maintain clean and simple architecture
- Avoid overengineering

---

## 14. Future Enhancements

- Deck sharing
- Collection tracking
- Recommendations
- Performance optimization

---
