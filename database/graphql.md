# GraphQL

- GraphQL is a query language for APIs
- It contains a a server-side runtime for executing queries, the runtime library supports most of the programming languages
- It uses a type system
- A GraphQL service is created by defining types and fields using GraphQL schema language, then providing functions for each field on each type
- It is not a database, it's database agnostic engine and can be used with any kind of database or even no database at all

## Operation

- The request which will be sent to server is called an operation, GraphQL supports three types of operation
  - `query`
  - `mutation`
  - `subscription`
- An operation has the following syntax

```graphql
operationType OperationName($variableName: variableType) {
    objectName(fieldName: $variableName) {
        fieldName
    }
}
```

- The query works without any variables definition and the curly brackets
  - When using variables, a seperate payload with variable value is required, `{"fieldName": "value"}`
- When variable definitions exist, passing a value to the variable is required, only when there is an `!` (non-null symbol) next to the variable type in the variable definitions
- Use `($variableName: variableType = defaultValue)` syntax in the variable definition to pass a default value for the variable
- Operation can have single line comments starts with `#`
- Operation name is only required in multi-operation documents
- A query can have a shorthand syntax where the operation type and operation name can be omitted
  - Shorthand syntax can't add operation name and variable information to the operation

### Query

- GraphQL will response the following query with exactly the same shape as the query

```graphql
  hero {
    name
    friends {
      name
    }
  }
}
```

- Example response:

```json
{
  "data": {
    "hero": {
      "name": "R2-D2",
      "friends": [
        {
          "name": "Luke Skywalker"
        },
        {
          "name": "Han Solo"
        },
        {
          "name": "Leia Organa"
        }
      ]
    }
  }
}
```

- GraphQL queries look the same for both single items or lists of items. However the actually data types are defined in the schema

#### Argument

- Every field and nested object can get its own set of arguments
- Enumeration type argument like unit name can be passed into scalar fields as well, then unit conversion can be performed on the server side

```gql
{
  human(id: "1000") {
    name
    height(unit: FOOT)
  }
}
```

#### Aliases

- It can be used to query for the same field or object with different arguments
- Aliases will rename the result of a field

```gql
{
  empireHero: hero(episode: EMPIRE) {
    name
  }
  jediHero: hero(episode: JEDI) {
    name
  }
}
```

- Example response

```json
{
  "data": {
    "empireHero": {
      "name": "Luke Skywalker"
    },
    "jediHero": {
      "name": "R2-D2"
    }
  }
}
```

#### Directives

- It can be used to change the structure of the query based on the variable value passed into it
- `@include(if: $booleanVarName)` can be added after object or field name in a query and related content will be return if variable value is `true`
- `@skip(if: $booleanVarName)` Skip this field if the argument is `true`

```gql
query Hero($episode: Episode, $withFriends: Boolean!) {
  hero(episode: $episode) {
    name
    friends @include(if: $withFriends) {
      name
    }
  }
}
```

### Mutation

- It is used to perform write operations
- Mutation operation returns the updated data using the query syntax

```gql
mutation CreateReviewForEpisode($ep: Episode!, $review: ReviewInput!) {
  createReview(episode: $ep, review: $review) {
    stars
    commentary
  }
}
```

- Example payload for variables

```json
{
  "ep": "JEDI",
  "review": {
    "stars": 5,
    "commentary": "This is a great movie!"
  }
}
```

- Example response

```json
{
  "data": {
    "createReview": {
      "stars": 5,
      "commentary": "This is a great movie!"
    }
  }
}
```

- While query fields are executed in parallel, mutation fields run in series, one after the other

### Fragment

- A reusable unit that can construct sets of fields, and then it can be included in queries or mutations to avoid repeatition

```gql
{
  leftComparison: hero(episode: EMPIRE) {
    ...comparisonFields
  }
  rightComparison: hero(episode: JEDI) {
    ...comparisonFields
  }
}

fragment comparisonFields on Character {
  name
  appearsIn
  friends {
    name
  }
}
```

- Fragment can access variables declared in the query or mutation

```gql
query HeroComparison($first: Int = 3) {
  leftComparison: hero(episode: EMPIRE) {
    ...comparisonFields
  }
  rightComparison: hero(episode: JEDI) {
    ...comparisonFields
  }
}

fragment comparisonFields on Character {
  name
  friendsConnection(first: $first) {
    totalCount
    edges {
      node {
        name
      }
    }
  }
}
```
