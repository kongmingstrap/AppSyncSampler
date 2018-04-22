```
input CreateFavoriteInput {
	id: ID!
	title: String
	itemId: String!
	userId: String!
}

input CreateUserInput {
	id: ID!
	firstname: String
	lastname: String
	gender: String
	age: String
	address: String
	tel: String
}

input DeleteFavoriteInput {
	id: ID!
}

input DeleteUserInput {
	id: ID!
}

type Favorite {
	id: ID!
	title: String
	itemId: String!
	userId: String!
}

type FavoriteConnection {
	items: [Favorite]
	nextToken: String
}

type Mutation {
	createUser(input: CreateUserInput!): User
	updateUser(input: UpdateUserInput!): User
	deleteUser(input: DeleteUserInput!): User
	createFavorite(input: CreateFavoriteInput!): Favorite
	updateFavorite(input: UpdateFavoriteInput!): Favorite
	deleteFavorite(input: DeleteFavoriteInput!): Favorite
}

type Query {
	getUser(id: ID!): User
	listUsers(first: Int, after: String): UserConnection
	getFavorite(id: ID!): Favorite
	listFavorites(first: Int, after: String): FavoriteConnection
}

type Subscription {
	onCreateUser(
		id: ID,
		firstname: String,
		lastname: String,
		gender: String,
		age: String
	): User
		@aws_subscribe(mutations: ["createUser"])
	onUpdateUser(
		id: ID,
		firstname: String,
		lastname: String,
		gender: String,
		age: String
	): User
		@aws_subscribe(mutations: ["updateUser"])
	onDeleteUser(
		id: ID,
		firstname: String,
		lastname: String,
		gender: String,
		age: String
	): User
		@aws_subscribe(mutations: ["deleteUser"])
	onCreateFavorite(
		id: ID,
		title: String,
		itemId: String,
		userId: String
	): Favorite
		@aws_subscribe(mutations: ["createFavorite"])
	onUpdateFavorite(
		id: ID,
		title: String,
		itemId: String,
		userId: String
	): Favorite
		@aws_subscribe(mutations: ["updateFavorite"])
	onDeleteFavorite(
		id: ID,
		title: String,
		itemId: String,
		userId: String
	): Favorite
		@aws_subscribe(mutations: ["deleteFavorite"])
}

input UpdateFavoriteInput {
	id: ID!
	title: String
	itemId: String
	userId: String
}

input UpdateUserInput {
	id: ID!
	firstname: String
	lastname: String
	gender: String
	age: String
	address: String
	tel: String
}

type User {
	id: ID!
	firstname: String
	lastname: String
	gender: String
	age: String
	address: String
	tel: String
}

type UserConnection {
	items: [User]
	nextToken: String
}
```