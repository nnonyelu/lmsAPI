# lmsAPI
All List of Library's users
GET
http://localhost:9080/api/users

API Endpoints api/users

Response

[
    {
        "userid": "111-1",
        "name": "amit",
        "address": "Nainital",
        "book1issue": "",
        "book2issue": "",
        "book1return": "",
        "book2return": "",
        "_links": {
            "self": {
                "href": "http://localhost:9080/api/user/111-1"
            }
        }
    },
    {
        "userid": "111-2",
        "name": "Harish",
        "address": "Lucknow",
        "book1issue": "",
        "book2issue": "",
        "book1return": "",
        "book2return": "",
        "_links": {
            "self": {
                "href": "http://localhost:9080/api/user/111-2"
            }
        }
    }
]


All List of book in Library

GET
api/books
http://localhost:9080/api/books

Response

[
    {
        "isbn": "111-1",
        "title": "autobiography of a yogi",
        "author": "Yogananda",
        "publisher": "pbs publisher",
        "status": "Avilable",
        "borrower": "none",
        "borrowDate": "none",
        "returnDate": "none",
        "_links": {
            "self": {
                "href": "http://localhost:9080/api/book/111-1"
            }
        }
    },
    {
        "isbn": "111-2",
        "title": "Gita",
        "author": "Lord Krishna",
        "publisher": "pbs publisher",
        "status": "Avilable",
        "borrower": "none",
        "borrowDate": "none",
        "returnDate": "none",
        "_links": {
            "self": {
                "href": "http://localhost:9080/api/book/111-2"
            }
        }
    }
]
1.	Ability to add books to the system.
POST api/books
http://localhost:9080/api/book
Request Pay load or body
{ "isbn": "111-4", "title": ".net", "author": "microsoft", "publisher": "PBS", "status": "Avilable", "borrower": "none", "borrowDate": "none", "returnDate": "none"
}
Response
{ "isbn": "111-4", "title": ".net", "author": "microsoft", "_links": { "self": { "href": "http://localhost:9080/api/book/111-4" }, "Books": { "href": "http://localhost:9080/api/books" } } }
2.	Ability to add users to the system.
POST api/users`
http://localhost:9080/api/user
Request Pay load
{ "userid": "111-3", "name": "yogesh mungali", "address": "noida, india, pin 202020", "book1issue": "", "book2issue": "", "book1return": "", "book2return": ""
}
Response
{ "userid": "111-3", "name": "yogesh mungali", "address": "noida, india, pin 202020", "book1issue": null, "book2issue": null, "book1return": null, "book2return": null, "_links": { "self": { "href": "http://localhost:9080/api/user/111-3" }, "Users": { "href": "http://localhost:9080/api/users" } } }
3.	Ability to lend books to users.
GET API End point lendbook/{user id}/{book id} request example
Get Method and link
http://localhost:9080/api/111-1/111-1
Response { "userid": "111-1", "name": "amit", "address": "Nainital", "book1issue": "Book 1 Issue :autobiography of a yogi", "book2issue": null, "book1return": null, "book2return": null }
4.	Ability to return books to the library.
GET API End point return/{user id}/{book id}
request example
Get Method and link
http://localhost:9080/api/return/111-1/111-1
Response
[ { "isbn": "111-1", "title": "autobiography of a yogi", "author": "Yogananda", "publisher": "pbs publisher", "status": "Avilable", "borrower": "none", "borrowDate": "none", "returnDate": "none", "_links": { "self": { "href": "http://localhost:9080/api/book/111-1" } } }, { "isbn": "111-2", "title": "Gita", "author": "Lord Krishna", "publisher": "pbs publisher", "status": "Avilable", "borrower": "none", "borrowDate": "none", "returnDate": "none", "_links": { "self": { "href": "http://localhost:9080/api/book/111-2" } } } ]
5.	Ability to limit the number of books borrowed by user.
"Only max 2 books can borrowed by per user"; if he try more then 2 books will get user.status = "You [user id ]"+userid +"have used total limit as only max 2 books can borrowed by per user"
6.	Ability to search a book by title, author.
search a book by title API End point api/search/book/{title}
request example (search a book by title("Gita"))
Get Method and link http://localhost:9080/api/search/book/Gita
Response [ { "isbn": "111-4", "title": "Gita", "author": "Iskon", "publisher": "pbs publisher", "status": "Avilable", "borrower": "none", "borrowDate": "none", "returnDate": "none" }, { "isbn": "111-2", "title": "Gita", "author": "Lord Krishna", "publisher": "Kbs publisher", "status": "Avilable", "borrower": "none", "borrowDate": "none", "returnDate": "none" } ]
search a book by author API End point api/search/book/{author}
request example (search a book by author("Iskon"))
Get Method and link http://localhost:9080/api/search/book/Iskon
Response [ { "isbn": "111-5", "title": "shreemad bhagwat geeta", "author": "Iskon", "publisher": "pbs publisher", "status": "Avilable", "borrower": "none", "borrowDate": "none", "returnDate": "none" }, { "isbn": "111-4", "title": "Gita", "author": "Iskon", "publisher": "pbs publisher", "status": "Avilable", "borrower": "none", "borrowDate": "none", "returnDate": "none" } ]
7.	Ability to search a user by name.
I have added 2 user with same name and name is "Amit"
GET API End point api/search/user/{name}
request example
Get Method and link
http://localhost:9080/api/search/user/amit
Response [ { "userid": "111-2", "name": "amit", "address": "Delhi", "book1issue": "none", "book2issue": "none", "book1return": "none", "book2return": "none", "status": "none", "_links": { "self": { "href": "http://localhost:9080/api/user/amit" }, "Users": { "href": "http://localhost:9080/api/users" } } }, { "userid": "111-2", "name": "amit", "address": "Delhi", "book1issue": "none", "book2issue": "none", "book1return": "none", "book2return": "none", "status": "none", "_links": { "self": { "href": "http://localhost:9080/api/user/amit" }, "Users": { "href": "http://localhost:9080/api/users" } } } ]
