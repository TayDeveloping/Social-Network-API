# Social Network API

## Description

This project is a **NoSQL Social Network API** built with **Express.js**, **MongoDB**, and **Mongoose**. The API allows users to share thoughts, react to friends' thoughts, and manage a friend list. It provides a way to handle unstructured data efficiently, making it ideal for social networking applications. 

The API includes routes for managing users, thoughts, reactions, and friend lists.

## Table of Contents

- [Installation](#installation)
- [Usage](#usage)
- [API Endpoints](#api-endpoints)
- [Models](#models)
- [License](#license)
- [Walkthrough Video](#walkthrough-video)

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/social-network-api.git

2. Navigate to the project directory:
    cd social-network-api

3. Install the dependencies:
    npm install

4. Set up your MongoDB connection by creating a .env file in the root of the project and adding your MongoDB URI:
    MONGODB_URI=mongodb://localhost:27017/social-network-api

5. Start the server:
    npm start

## Usage

To use the Social Network API, follow these steps:

1. Ensure the server is running by executing the following command:
   ```bash
   npm start

2. Open Insomnia (or another API client like Postman).

3. Interact with the API by using the endpoints listed below to manage users, thoughts, reactions, and friend lists.


## API Endpoints
Users
GET /api/users - Get all users
GET /api/users/:userId - Get a single user by ID
POST /api/users - Create a new user
PUT /api/users/:userId - Update a user by ID
DELETE /api/users/:userId - Delete a user by ID
POST /api/users/:userId/friends/:friendId - Add a friend
DELETE /api/users/:userId/friends/:friendId - Remove a friend
Thoughts
GET /api/thoughts - Get all thoughts
GET /api/thoughts/:thoughtId - Get a single thought by ID
POST /api/thoughts - Create a new thought
PUT /api/thoughts/:thoughtId - Update a thought by ID
DELETE /api/thoughts/:thoughtId - Delete a thought by ID
Reactions
POST /api/thoughts/:thoughtId/reactions - Add a reaction to a thought
DELETE /api/thoughts/:thoughtId/reactions/:reactionId - Remove a reaction from a thought
Models
User
username: String (Unique, Required, Trimmed)
email: String (Unique, Required, Must be a valid email)
thoughts: Array of _id values referencing the Thought model
friends: Array of _id values referencing the User model (self-reference)
Virtuals:

friendCount: Retrieves the number of friends a user has.
Thought
thoughtText: String (Required, 1-280 characters)
createdAt: Date (Default: current timestamp, formatted using a getter)
username: String (Required)
reactions: Array of nested documents (reactions)
Virtuals:

reactionCount: Retrieves the number of reactions for a thought.
Reaction (Subdocument)
reactionId: ObjectId (Default: new ObjectId)
reactionBody: String (Required, 280 character max)
username: String (Required)
createdAt: Date (Default: current timestamp, formatted using a getter)

## License
This project is licensed under the MIT License.