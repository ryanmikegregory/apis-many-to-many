# Apis Many-to-Many

```
CREATE TABLE "person" (
	"id" SERIAL PRIMARY KEY,
	"name" VARCHAR(25)
);

INSERT INTO "person" (name) VALUES
('Scott'), ('Rachael'), ('Jackson'), ('Moxie'), ('Baxter');

SELECT "id", "name" FROM "person";

CREATE TABLE "hobby" (
	"id" SERIAL PRIMARY KEY,
	"description" VARCHAR(100)
);

INSERT INTO "hobby" ("description") VALUES
('TV Watching'), ('Playing Video Games'), ('Couching'), ('Reading'), ('Barking');

SELECT * FROM "hobby";

CREATE TABLE "person_hobby" (
	"id" SERIAL PRIMARY KEY,
	"person_id" INT REFERENCES "person",
	"hobby_id" INT REFERENCES "hobby"
);

INSERT INTO "person_hobby" ("person_id", "hobby_id") VALUES
(1,2), (1,4), (2,1), (2,3), (2,4), (3,1), (3,1), (3,2), (3,3), (3,4), (3,5), (4,3), (4,5), (5,5); 

SELECT "person"."name", "hobby"."description" FROM "person"
JOIN "person_hobby" ON "person"."id" = "person_hobby"."person_id"
JOIN "hobby" ON "hobby"."id"="person_hobby"."hobby_id";

SELECT "person"."name", "hobby"."description" FROM "person"
JOIN "person_hobby" ON "person"."id" = "person_hobby"."person_id"
JOIN "hobby" ON "hobby"."id"="person_hobby"."hobby_id"
WHERE "person"."id"=2;
```
