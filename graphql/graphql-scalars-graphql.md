# GraphQL Scalars — GraphQL Reference

GraphQL Scalars provides custom scalar type definitions that can be added to any GraphQL schema. The scalars are defined using the standard `scalar` keyword and are fully compatible with the GraphQL specification.

## Adding Scalars to a Schema

```graphql
# Import individual scalars as needed
scalar DateTime
scalar EmailAddress
scalar UUID
scalar URL
scalar IPv4
scalar JSONObject
scalar BigInt
scalar IBAN
scalar PhoneNumber
scalar PostalCode
```

## Full Scalar Catalog

### Date & Time
```graphql
scalar DateTime        # ISO 8601 date-time string (e.g. 2007-12-03T10:15:30Z)
scalar Date            # ISO 8601 date string (e.g. 2007-12-03)
scalar Time            # ISO 8601 time string (e.g. 10:15:30)
scalar DateTimeISO     # Strict ISO 8601 date-time with timezone offset
scalar LocalDate       # Date without timezone (YYYY-MM-DD)
scalar LocalTime       # Time without timezone (HH:mm:ss)
scalar LocalDateTime   # DateTime without timezone
scalar Duration        # ISO 8601 duration (e.g. P1Y2M3DT4H5M6S)
scalar Timestamp       # Unix timestamp (integer)
scalar UTCOffset       # UTC offset string (e.g. +05:30)
scalar ISO8601Duration # Strict ISO 8601 duration
```

### Identity & Unique Identifiers
```graphql
scalar UUID    # RFC 4122 UUID (e.g. 550e8400-e29b-41d4-a716-446655440000)
scalar GUID    # Globally Unique Identifier (same format as UUID)
scalar CUID    # Collision-resistant unique ID (cuid format)
scalar CUID2   # Next-generation cuid (cuid2 format)
scalar ULID    # Universally Unique Lexicographically Sortable Identifier
scalar ObjectID # MongoDB ObjectID (24-char hex string)
scalar DID      # Decentralized Identifier (W3C DID spec)
```

### Network & Internet
```graphql
scalar IPv4    # IPv4 address (e.g. 192.168.1.1)
scalar IPv6    # IPv6 address (e.g. 2001:db8::1)
scalar IP      # Any IP address (IPv4 or IPv6)
scalar MAC     # MAC address (e.g. 00:1B:44:11:3A:B7)
scalar URL     # Valid URL string
scalar Port    # Network port number (0–65535)
```

### Communication
```graphql
scalar EmailAddress  # Valid email address (RFC 5322)
scalar PhoneNumber   # E.164 format phone number (e.g. +14155552671)
```

### Finance
```graphql
scalar IBAN          # International Bank Account Number
scalar Currency      # ISO 4217 currency code (e.g. USD, EUR)
scalar USCurrency    # US currency amount (e.g. $10.99)
scalar RoutingNumber # ABA routing number (9-digit US bank code)
scalar AccountNumber # Generic account number
```

### Geographic
```graphql
scalar Latitude    # Decimal latitude (-90 to 90)
scalar Longitude   # Decimal longitude (-180 to 180)
scalar CountryCode # ISO 3166-1 alpha-2 country code (e.g. US)
scalar CountryName # Full country name
scalar PostalCode  # Postal/ZIP code (locale-aware)
scalar TimeZone    # IANA timezone identifier (e.g. America/New_York)
scalar Locale      # IETF BCP 47 language tag (e.g. en-US)
```

### Numeric Types
```graphql
scalar BigInt           # Arbitrary-precision integer
scalar Long             # 64-bit integer
scalar SafeInt          # Integer within JavaScript safe integer range
scalar PositiveInt      # Integer > 0
scalar NegativeInt      # Integer < 0
scalar NonPositiveInt   # Integer <= 0
scalar NonNegativeInt   # Integer >= 0
scalar PositiveFloat    # Float > 0
scalar NegativeFloat    # Float < 0
scalar NonPositiveFloat # Float <= 0
scalar NonNegativeFloat # Float >= 0
scalar UnsignedInt      # Integer >= 0
scalar UnsignedFloat    # Float >= 0
scalar Byte             # 8-bit integer (0–255)
```

### Structured Data
```graphql
scalar JSON        # Any valid JSON value
scalar JSONObject  # JSON object (key-value map)
scalar GeoJSON     # GeoJSON Feature or FeatureCollection object
```

### Encoding & Tokens
```graphql
scalar JWT         # JSON Web Token string
scalar Hexadecimal # Hexadecimal string (e.g. deadbeef)
scalar HexColorCode # CSS hex color (e.g. #FF5733)
scalar RGB         # CSS rgb() color string
scalar RGBA        # CSS rgba() color string
scalar HSL         # CSS hsl() color string
scalar HSLA        # CSS hsla() color string
```

### Text & Strings
```graphql
scalar NonEmptyString # String with at least one character
scalar RegularExpression # String matching a custom regex pattern
```

### Standards & References
```graphql
scalar SemVer      # Semantic version string (e.g. 1.0.0-alpha.1)
scalar ISBN        # International Standard Book Number (ISBN-10 or ISBN-13)
scalar ISSN        # International Standard Serial Number
scalar IPCPatent   # IPC patent classification code
scalar DeweyDecimal # Dewey Decimal System classification
scalar LCCSubclass  # Library of Congress Classification subclass
scalar SESSN       # Standard Engraving/Serial/Spec Number
```

### Utility
```graphql
scalar Void # Always returns null; used for mutations with no return value
```

## Example Schema Usage

```graphql
scalar DateTime
scalar EmailAddress
scalar UUID
scalar PhoneNumber
scalar URL

type User {
  id: UUID!
  email: EmailAddress!
  phone: PhoneNumber
  website: URL
  createdAt: DateTime!
  updatedAt: DateTime!
}

type Query {
  user(id: UUID!): User
}

type Mutation {
  createUser(email: EmailAddress!, phone: PhoneNumber): User!
}
```

## Resources

- Documentation: https://the-guild.dev/graphql/scalars/docs
- GitHub: https://github.com/graphql-hive/graphql-scalars
- npm: https://www.npmjs.com/package/graphql-scalars
