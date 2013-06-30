---
title: PostgreSQL & Materialized Path
layout: post
---

[Tree structure](http://en.wikipedia.org/wiki/Tree_structure) буюу мод бүтцийг [RDBMS][rdbms] төрлийн системүүдэд
хадгалах [маш олон аргууд](http://troels.arvin.dk/db/rdbms/links/#hierarchical) байдгаас [Materialized Path][mp] аргыг [PostgreSQL][psql] дээр таницуулья.

#### Асуудал
Ихэнх хөгжүүлэгчид мод бүтцийг өгөгдлийн санд хадгалахдаа эцэг бичлэгийнх нь `ID`-г хүү бичлэгт нь хадгалах
замаар шийддэг. Үүний сонгодог жишээ болох ангилал зүйг жишээ болгон авч үзье.

{% highlight psql %}
blog_development=# \d categories
  Table "public.categories"
  Column    |       Type        | Modifiers
  ----------+-------------------+-----------
  id        | integer           | not null
  name      | character varying |
  parent_id | integer           |
  Indexes:
    "categories_pkey" PRIMARY KEY, btree (id)

blog_development=# select * from categories ;
  id |   name     | parent_id
  ---+------------+-----------
  1  | Books      |
  2  | Education  |         1
  3  | Law        |         1
  4  | History    |         2
  5  | Counseling |         2
{% endhighlight %}

<br/>

#### Materialized Path

#### Materialized Path болон PostgreSQL Array


[psql]: http://en.wikipedia.org/wiki/PostgreSQL
[rdbms]: http://en.wikipedia.org/wiki/Relational_database_management_system
[mp]: http://en.wikipedia.org/wiki/Materialized_path
