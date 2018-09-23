
{
  "address": {
     "building": "1007",
     "coord": [ -73.856077, 40.848447 ],
     "street": "Morris Park Ave",
     "zipcode": "10462"
  },
  "borough": "Bronx",
  "cuisine": "Bakery",
  "grades": [
     { "date": { "$date": 1393804800000 }, "grade": "A", "score": 2 },
     { "date": { "$date": 1378857600000 }, "grade": "A", "score": 6 },
     { "date": { "$date": 1358985600000 }, "grade": "A", "score": 10 },
     { "date": { "$date": 1322006400000 }, "grade": "A", "score": 9 },
     { "date": { "$date": 1299715200000 }, "grade": "B", "score": 14 }
  ],
  "name": "Morris Park Bake Shop",
  "restaurant_id": "30075445"
}

Write a MongoDB query to display all the documents in the collection restaurants

db.restaurants.find().pretty()

Write a MongoDB query to display the fields restaurant_id, name, borough and cuisine for all the documents in the collection restaurant. 
> db.restaurants.aggregate({$project:{restaurant_id:1,name:1,borough:1,cuisine:1})


Write a MongoDB query to display the fields restaurant_id, name, borough and cuisine, but exclude the field _id for all the documents in the collection restaurant
> db.restaurants.aggregate({$project:{restaurant_id:1,name:1,borough:1,cuisine:1,_id:0}})

Write a MongoDB query to display the fields restaurant_id, name, borough and zip code, but exclude the field _id for all the documents in the collection restaurant.
>db.restaurants.aggregate({$project:{restaurant_id:1,name:1,borough:1,zipcode:1,_id:0}})
 
 Write a MongoDB query to display all the restaurant which is in the borough Bronx
 > db.restaurants.aggregate({$match:{'borough':'Bronx'}})
 
 Write a MongoDB query to display the first 5 restaurant which is in the borough Bronx
   db.restaurants.find({'borough':'Bronx'}).limit(5).pretty()
   
   Write a MongoDB query to display the next 5 restaurants after skipping first 5 which are in the borough Bronx
   db.restaurants.find({'borough':'Bronx'}).limit(5).skip(5).pretty()
   
   Write a MongoDB query to find the restaurants who achieved a score more than 90
   >db.restaurants.find({'grades.score':{$gt:90}},{_id:0,name:1}).pretty()
   
   Write a MongoDB query to find the restaurants that achieved a score, more than 80 but less than 100
   >db.restaurants.find({'grades.score':{$gt:80,$lt:100}},{_id:0,name:1}).pretty().count()
   
    Write a MongoDB query to find the restaurants which locate in latitude value less than -95.754168
	>db.restaurants.find({'address.coord':{$lt:-95.754168}},{name:1,'address.coord':1,_id:0}).pretty()
   
    Write a MongoDB query to find the restaurants that do not prepare any cuisine of 'American' and their grade score more than 70 and latitude less than -65.754168. 
	>db.restaurants.find({'cuisine':'American ','grades.score':{$gt:70},'address.coord':{$lt:-65.754168}},{cuisine:1,'address.coord':1,_id:0}).pretty()	
  
	Write a MongoDB query to find the restaurants which do not prepare any cuisine of 'American' and achieved a score more than 70
	and located in the longitude less than -65.754168.
	Note : Do this query without using $and operator
	>db.restaurants.find({ 'cuisine':'American ', 'grades.score':{$gt:70}, 'address.coord':{$lt:-65.754168} } )
	
	Write a MongoDB query to find the restaurants which do
	not prepare any cuisine of 'American ' and achieved a 
	grade point 'A' not belongs to the borough Brooklyn.
	The document must be displayed according to the 
	cuisine in descending order
    >db.restaurants.find({ 'cuisine':{$ne:'American '}, 'grades.grade':'A', 'borough':'Brooklyn' }).sort({'cuisine':-1})
	
	
	Write a MongoDB query to find the restaurant Id, name, borough and cuisine for those restaurants which contain 'Wil' as first three letters for its name
	>db.restaurants.find({name:/Wil/},{restaurant_id:1,name:1,cuisine:1})

	db.restaurants.aggregate({$match:{'name':/Wil/}},{$project:{restaurant_id:1,name:1,borough:1,cuisine:1,_id:0}})
	
	using not operator
	> db.restaurants.find({name:/^Wil/},{restaurant_id:1,name:1,cuisine:1})
	
	Write a MongoDB query to find the restaurant Id, name, borough and cuisine for those restaurants which contain 'ces' as last three letters for its name
	> db.restaurants.find({name:/ces$/},{restaurant_id:1,name:1,cuisine:1})
	 
	 Write a MongoDB query to find the restaurant Id, name, borough and cuisine for those restaurants which contain 'Reg' as three letters somewhere in its name.
	db.restaurants.find({name:/Reg/},{restaurant_id:1,name:1,cuisine:1}).count()
	db.restaurants.find({name:/.*Reg.*/},{restaurant_id:1,name:1,cuisine:1}).count()
	
	
	Write a MongoDB query to find the restaurants which belong to the borough Bronx and prepared either American or Chinese dish.
	> db.restaurants.find({'borough':'Bronx',$or:[{'cuisine':'American '},{'cuisine':'Chinese'}]}).count()
	
	Write a MongoDB query to find the restaurant Id, name, borough and cuisine for those restaurants which belong to the borough Staten Island or Queens or Bronxor Brooklyn
	db.restaurants.find({$or:[{'borough':'Staten Isnland'},{'borough':'Queens'},{'borough':'Bronx'},{'borough':'Brooklyn'}]},{restaurant_id:1,name:1,borough:1,cuisine:1,_id:0})
	
	
	Write a MongoDB query to find the restaurant Id, name, borough and cuisine for those restaurants which are not belonging to the borough Staten Island or Queens or Bronxor Brooklyn
	
	(wrong)db.restaurants.find({grades.score:{$lte:10}},{restaurant_id:1,borough:1,cuisine:1,grades.score:1,_id:0})
	
	use $not operator instead of $lte, when your column is an array
	
	> db.restaurants.find({'grades.score':{$not:{$gt:10}}},{restaurant_id:1,borough:1,cuisine:1,'grades.score':1,_id:0}).count()
	
	
	Write a MongoDB query to find the restaurant Id, name, borough and cuisine for those restaurants which prepared dish except 'American' and 'Chinees' or restaurant's name begins with letter 'Wil'. 
	> db.restaurants.find({'name':{$not:/Wil/},$or:[{cuisine:{$not:/American/},cuisine:{$not:/Chinese/}}] },{_id:0,name:1,cuisine:1})
	
	
	Write a MongoDB query to find the restaurant Id, name, and grades for those restaurants which achieved a grade of "A" and scored 11 on an ISODate "2014-08-11T00:00:00Z" among many of survey dates
		
	"here we learned how to access specified indexed document of an array "	
	
	db.restaurants.find({"grades.1.date": ISODate("2014-08-11T00:00:00Z"), 
                        "grades.1.grade":"A" , 
                        "grades.1.score" : 9
                      }, 
                       {"restaurant_id" : 1,"name":1,"grades":1}
                   );
})
	
	> db.restaurants.find({'grades.1.grade':'A','grades.1.score':9}).pretty().limit(1)

	Write a MongoDB query to find the restaurant Id, name, address and geographical location for those restaurants where 2nd element of coord array contains a value which is more than 42 and upto 52
	
	
	db.restaurants.find({'address.coord.1':{$gt:42,$lte:52}},{restaurant_id:1,name:1,address:1,coord:1,_id:0})
	
	Write a MongoDB query to arrange the name of the restaurants in ascending order along with all the columns
	db.restaurants.find({},{name:1,_id:0}).pretty().sort({'name':1})
	
	 Write a MongoDB query to arrange the name of the restaurants in descending along with all the columns. 
	db.restaurants.find({},{name:1,_id:0}).pretty().sort({'name':-1})	
	
	Write a MongoDB query to arranged the name of the cuisine in ascending order and for that same cuisine borough should be in descending order
	db.restaurants.find({},{cuisine:1,borough:1,_id:0}).pretty().sort({'cuisine':1,'borough':-1})
	
	
	Write a MongoDB query to know whether all the addresses contains the street or not
	> db.restaurants.find({'address.street':{$exists:true}})
	
	'using $type operator'
	Write a MongoDB query which will select all documents in the restaurants collection where the coord field value is Double
	db.restaurants.find(
                    {"address.coord" : 
                       {$type : 1}
                    }
                   );
				   
	
	'using $mod operator'
	Write a MongoDB query which will select the restaurant Id, name and grades for those restaurants which returns 0 as a remainder after dividing the score by 7
	db.restaurants.find(
                      {"grades.score" :
                         {$mod : [7,0]}
                      },
                         {"restaurant_id" : 1,"name":1,"grades":1}
                    );
					
					
	''
	Write a MongoDB query to find the restaurant name, borough, longitude and attitude and cuisine for those restaurants which contains 'mon' as three letters somewhere in its name
	
	> db.restaurants.find({name:/.*mon.*/},{name:1,borough:1,"address.coord":1,cuisine:1,_id:0}).limit(1).pretty().count()
	
	 db.restaurants.find({ name :{ $regex : "mon.*", $options: "i" }},{"name":1,"borough":1,"address.coord":1,"cuisine" :1}
	
	
	
	
	
	