1. This is an attack vector where the attacker has stolen the user's session cookie. Here, the attacker requests the user's shopping cart with the stolen session cookie
1. The application backend looks up the server-side session associated with the session cookie and extends the expiration date
1. The application backend uses the session to look up the user's shopping cart. It responds to the attacker with the user's shopping cart HTML, CSS & JavaScript