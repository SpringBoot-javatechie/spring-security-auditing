# spring-security-role-auth
Implement Role base authorization (Facebook Group Example)

Step : 1 

Add 2 user , fire below curl

```curl --location --request POST 'http://localhost:9090/user/join' \
--header 'Content-Type: application/json' \
--header 'Cookie: JSESSIONID=14E9CEF5EFE59D531121E2095C745E0A' \
--data-raw '{
    "userName": "Basant",
    "password": "pwd1",
    "active": true
}'
```

```
curl --location --request POST 'http://localhost:9090/user/join' \
--header 'Content-Type: application/json' \
--header 'Cookie: JSESSIONID=14E9CEF5EFE59D531121E2095C745E0A' \
--data-raw '{
    "userName": "goyal",
    "password": "pwd2",
    "active": true
}'
```

Next update one user role as admin like below either from DB or from API 

```
update users_authentication_tbl set roles="ROLE_ADMIN" where id=2
```

Next create a post with user , curl 

```
curl --location --request POST 'http://localhost:9090/post/create' \
--header 'Authorization: Basic QmFzYW50OnB3ZDE=' \
--header 'Content-Type: application/json' \
--header 'Cookie: JSESSIONID=14E9CEF5EFE59D531121E2095C745E0A' \
--data-raw '{
    "subject": "Hashmap",
    "description": "Hashmap allow duplicate key"
}'
```

next approve this with admin credential and verify in DB about created by and modified by field should updated 

```
curl --location --request GET 'http://localhost:9090/post/approvePost/3' \
--header 'Authorization: Basic Z295YWw6cHdkMg==' \
--header 'Cookie: JSESSIONID=14E9CEF5EFE59D531121E2095C745E0A' \
--data-raw ''
```


Results :
![Screen Shot 1401-07-24 at 13 24 50](https://user-images.githubusercontent.com/25712816/196024642-d4ecf262-9030-4fe2-b234-758eeb665fe3.png)

