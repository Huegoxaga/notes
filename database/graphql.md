# GraphQL

- GraphQL is a query language for APIs
- It contains a a server-side runtime for executing queries, the runtime library supports most of the programming languages
- It uses a type system
- A GraphQL service is created by defining types and fields using GraphQL schema language, then providing functions for each field on each type
- It is not a database, it's database agnostic engine and can be used with any kind of database or even no database at all

## Schema Language

- Schema files are text files, usually named `schema.graphql`
- All types other than the built-in types need to be defined in the schema files for use, starting from the schema object

### Scalar Types

- They don't have any sub-fields - they are the leaves of the query

#### Built-in Scalar Types

- `Int`: A signed 32‐bit integer.
- `Float`: A signed double-precision floating-point value.
- `String`: A UTF‐8 character sequence.
- `Boolean`: true or false.
- `ID`: The ID scalar type represents a unique identifier, often used to refetch an object or as the key for a cache. The ID type is serialized in the same way as a String; however, defining it as an ID signifies that it is not intended to be human‐readable.

#### Enumeration Types

- A special kind of scalar that is restricted to a particular set of allowed values
- Defining a enum type

```gql
enum EnumTypeName {
  ENUM_ONE
  ENUM_TWO
  ENUM_THREE
}
```

- GraphQL service implementations in various languages will have their own language-specific way to deal with enums

#### Custom Scalar Types

- This varies based on the specific implementation language

### Type Modifiers

- By adding an exclamation mark, `!` after the type name, server always expects to return a non-null value for this field
  - If it ends up getting a null value, that will actually trigger a GraphQL execution error
  - The Non-Null type modifier can also be used when defining arguments for a field, which will cause the GraphQL server to return a validation error if a null value is passed as that argument
- Wrapping the type in square brackets, `[` and `]`, indicates that this field will return an array of that type
  - It works the same for arguments
- `[TypeName!]` inside `[]` simply means the list itself can be null, but it can't have any null members
  - `[TypeName!]!` means it must be a non-empty list with at least one element of the specific type
- One can arbitrarily nest any number of Non-Null and List modifiers

### Object Type

- An object type is like a table, it stores many attributes
- Syntax for defining an object type

```gql
type ObjectType1 {
  fieldName1: scalarType!
  fieldName2: [ObjectType2!]!
  fieldName3(argumentName: EnumName = Enum1): scalarType
}
```

- Arguments can be either required or optional. When an argument is optional, it can have a default value

#### Schema Type

- It defines the schema itself
- It is the root of the schema file
- The root type should be either `Query`, `Mutation`, and `Subscription`
  - They are special object types
  - They define the entry point of this schema
  - These object type need to be further defined
- The following snippet define a root query and root mutation type for the schema

```gql
schema {
  query: Query
  mutation: Mutation
}
```

#### Query Types

- They are responsible for reading data
- The syntax for defining a query in the scheme is as follows

```gql
type Query {
  objectName1(argumentName: argumentType): ObjectType1
  objectName2(argumentName: argumentType!): ObjectType2
}
```

- Example Query type definition

```gql
type Query {
  hero(episode: Episode): Character
  droid(id: ID!): Droid
}
```

- Then query about `hero` and `droid` can be made

#### Mutation Types

- They are responsible for writing data
- The syntax for defining a mutation in the schema is as follows

```gql
type Mutation {
  addTodo(id: ID!, name: String, description: String, priority: Int): Todo
}
```

#### Input Types

- It is used to pass object type as an argument
- Input types look exactly the same as regular object types, but with the keyword `input` instead of `type`
- Input object types can't have arguments on their fields
- Example definition

```gql
input ReviewInput {
  stars: Int!
  commentary: String
}
```

- Example mutation

```gql
mutation CreateReviewForEpisode($ep: Episode!, $review: ReviewInput!) {
  createReview(episode: $ep, review: $review) {
    stars
    commentary
  }
}
```

- Example variables

```json
{
  "ep": "JEDI",
  "review": {
    "stars": 5,
    "commentary": "This is a great movie!"
  }
}
```

### Interface

- An Interface is an abstract type that includes a certain set of fields that a type must include to implement the interface
- Syntax for defining an interface

```gql
interface Character {
  id: ID!
  name: String!
  friends: [Character]
  appearsIn: [Episode]!
}
```

- Syntax for implementing an interface

```gql
type Human implements Character {
  id: ID!
  name: String!
  friends: [Character]
  appearsIn: [Episode]!
  starships: [Starship]
  totalCredits: Int
}
```

- Interfaces are useful when requesting an object or set of objects from several different types

### Union Types

- As its name suggests, it represents a group of possible object type
- Defining a union type, `union UnionTypeName = ObjectType1 | ObjectType1 | ObjectType1`
  - The object type included in a union must be a concrete type, it can't be a fragment
- When a query is expected to return a union type, it can return any one of the type included in the union
- Use inline fragment to cast the union type into a concrete type in the response, in order to be able to query any fields inside that object type

```gql
{
  search(text: "an") {
    __typename
    ... on Human {
      name
      height
    }
    ... on Droid {
      name
      primaryFunction
    }
    ... on Starship {
      name
      length
    }
  }
}
```

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
{
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

- `hero` in the example, should be defined as a field of the root `Query` type definition in the schema
- GraphQL queries look the same for both single items or lists of items. However the actually data types are defined in the schema
- All queries should specify a scalar or enum type for return

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

#### Meta Fields

- They are defined as the `Introspection` system for the GraphQL
- Anything that is preceded with a double underscore, is part of the introspection system
- `__typename` returns the type name of the return object as a `String` type value
- `__schema` available from the root level, returns a `__Schema` object with the following fields:
  - `description` returns the description about this API schema in a `String`
  - `types` returns a list of `__Type` objects defined in the schema
  - `queryType` returns a `__Type` object representing the type that all queries would start at for this API
  - `mutationType` returns a `__Type` object representing the type that all mutations would start at for this API
  - `subscriptionType` returns a `__Type` object representing the type that all subscription would start at for this API
  - `directives` returns a list of available `__Directive` objects for this API
- `__type` takes an argument and returns the `__Type` object of selected object
  - `name` return the name of this type
  - `kind` returns a `__TypeKind` enum for this type
  - `fields` returns a list of `__Field` objects representing the available fields for this type
  - `description` returns the description of this type in a `String`
- Other default object types
  - `__InputValue`
  - `__EnumValue`

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

- A fragment cannot refers itself inside its definition

#### Inline Fragment

- To ask for a field on a specific object type, you need to use an inline fragment
- The object type after keyword `on` can be a concrete object type or an interface followed by some common fields

```gql
query HeroForEpisode($ep: Episode!) {
  hero(episode: $ep) {
    name
    ... on Droid {
      primaryFunction
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

### Subscription

- long-lived connection for receiving data
- Subscriptions are usually invoked as a response to a mutation

## Implementation

- GraphQL can be implemented using libraries written in various programming languages
- Libraries can be used to run either a GraphQL API server, or a GraphQL client to send requests
- On the server side each field in a query will invoke a function called resolver
  - Resolver is responsible for fetch requested data from the database
  - In a query, objects can have objects as a field. Resolvers are chained in an asynchronous manner, and they complete their actions when a scalar data is obtained
  - Generally a resolver function takes four arguments
    - The previous object, which for a field on the root Query type is often not used.
    - The arguments provided to the field in the GraphQL query.
    - A value which is provided to every resolver and holds important contextual information like the currently logged in user, or access to a database.
    - A value which holds field-specific information relevant to the current query as well as the schema details, also refer to type GraphQLResolveInfo for more details
- [Click Here](https://graphql.org/code/) to see all options
