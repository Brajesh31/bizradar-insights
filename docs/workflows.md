# 🔁 Product Workflows

## 1. Opportunity exploration

```mermaid
flowchart TD
 A([Open Opportunities]) --> B[Enter location]
 B --> C[Location search service]
 C --> D{Choose a result}
 D -->|No| B
 D -->|Yes| E[Select category]
 E --> F[Generate market inputs]
 F --> G[Create category opportunity list]
 G --> H[Calculate BizScore/category intelligence]
 H --> I[Build competition and forecast panels]
 I --> J[Render cards and map]
 J --> K([Select candidate])
```

## 2. Feasibility report

```mermaid
flowchart TD
 A([Select candidate]) --> B[Open report route]
 B --> C{ideaId supplied?}
 C -->|Yes| D[Load custom_ideas record]
 C -->|No| E[Read city/category/score parameters]
 D --> F[Build report model]
 E --> F
 F --> G[Calculate finance and SWOT]
 G --> H[Calculate competitor/rent/persona/seasonality/risk]
 H --> I[Render report tabs]
 I --> J{Save report?}
 J -->|Yes| K[Insert saved_ideas]
 J -->|No| L([Continue])
 K --> L
```

## 3. AI idea parsing

```mermaid
sequenceDiagram
 participant User
 participant React as Idea Analyzer
 participant SB as Supabase Functions
 participant Fn as parse-idea
 participant Model as Lovable AI Gateway
 User->>React: Submit idea
 React->>SB: Invoke function
 SB->>Fn: Request body
 Fn->>Model: Structured extraction prompt
 Model-->>Fn: Generated JSON text
 Fn->>Fn: Parse and return fields
 Fn-->>React: Structured output
 React-->>User: Display analysis
```

## 4. Authentication

```mermaid
sequenceDiagram
 participant Browser
 participant Context as AuthContext
 participant Supabase as Supabase Auth
 Browser->>Context: Mount application
 Context->>Supabase: Subscribe to auth changes
 Context->>Supabase: getSession()
 Supabase-->>Context: Session or null
 Context-->>Browser: Update user/loading state
 Browser->>Context: Sign in/up/out
 Context->>Supabase: Auth operation
 Supabase-->>Context: Result and session update
```

## 5. Save ownership

Saved rows should be bound to the authenticated user's ID. Database RLS must enforce ownership. Client-side filters and hidden routes are not security boundaries.
