#### express-session helps to manage session

#### generally session data is maintained in the session cookie, session cookie expire leads to loss of session data

#### uses cookie parser


https://www.geeksforgeeks.org/session-management-using-express-session-module-in-node-js/

#### express session store

	by default express-sessin uses inmemory, session data lost when server is restarted.
	so use third party dbs to store use defined memory to store session.
	read : https://www.npmjs.com/package/connect-mongodb-session
	read: Compatible Session Stores from npm express-session
	
	If you don't supply express-session with a storage mechanism, then it just uses a lightweight memory store. 
	Thus, it is not persisted across server restarts.


### options

####	resave:
	
  Forces the session to be saved back to the session store.
	As it create race condition, check documentation and use resave;
	race condtion express: where a client makes multiple parallel requests without a session

####	saveUninitialized
	
  Forces a session that is "uninitialized" to be saved to the store. 
	A session is uninitialized when it is new but not modified. 
	Choosing false is useful for implementing login sessions, 
	reducing server storage usage, or complying with laws that require permission before setting a cookie. 
	Choosing false will also help with race conditions where a client makes multiple parallel requests 
	without a session.

####	secret:
	
  This is the secret used to sign the session ID cookie. 
	This can be either a string for a single secret, or an array of multiple secrets. 
	If an array of secrets is provided, only the first element will be used to sign the session ID cookie, 
	while all the elements will be considered when verifying the signature in requests.
	encrypting session data
