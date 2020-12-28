# tutorial_javaspringlombok
finished tutorial using lombok and requirements listed in article
Tutorial -> https://spring.io/guides/tutorials/rest/


curl -v http://localhost:8080/employees | json_pp

HTTP code 200

curl -v localhost:8080/employees/99

HTTP code 404

curl -X POST localhost:8080/employees -H 'Content-type:application/json' -d '{"name": "Samwise Gamgee", "role": "gardener"}'

New employee created

curl -v -X PUT localhost:8080/employees/5 -H 'Content-Type:application/json' -d '{"name": "Samwise Gamgee", "role": "ring bearer"}'

Changes Samwise to ring bearer role from gardener

curl -v localhost:8080/employees/5 | json_pp



I have noticed that the Id’s increment although belonging to different repositories. 

Samwise Gamgee will have the Id of 5 and not 3, 

This is due to two orders already present in the database from incrementing the id

curl -X DELETE localhost:8080/employees/3

-> 

curl -X DELETE localhost:8080/employees/5



curl -v http://localhost:8080/orders | json_pp



curl -v -X DELETE http://localhost:8080/orders/4/cancel

Changes iPhone to be status canceled HTTP code 200 for success

curl -v -X DELETE http://localhost:8080/orders/4/cancel  

…try again gives HTTP code 405

curl -v -X PUT localhost:8080/orders/4/complete

…alternatively, put does not allow an already completed order to change with HTTP code 405





HATEOAS (Hypermedia as the Engine of Application State) discovers available actions and access the resources it needs. Uses URI and relation

Uses EntityModel for single resource CollectionModel for more than one resource. Returns links. Allows legacy versions to still be present with new versions.

Model assemblers inject the links at the controller class



JPA interacts with the database(in our case h2) supporting creating, reading, updating, and deleting records. A repository is injected into the controller. 
