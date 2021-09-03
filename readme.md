# Messaging Service


Techincal Information:

1. Use bcrypt for password hash and authentication
2. Use session token stored in the client's cookie (client side) and redis (server side)
3. Use redis as the database (more on that down under the database heading)


## Database

Redis is used here as the database (and cache for sessions).

Structure:
* `messaging-service:users:${username}:profile`:  A table containing the user's json struct (username, passhash, fullname)
* `messaging-service:users:${username}:blocked`:  A set of usernames which are not allowed to communicate with the user
* `messaging-service:users:${username}:activity`: A list containing all of the user's signin attempts and their status
* `messaging-service:chats:${username1 + username2, where username1 < username2 }`: A list containing messages as json structs
* `messaging-service:sessions:${uuid}`: A string representing the username who signed for this session
