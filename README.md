# MongoDB
mongoDB study start 

mongoDB
use DATABASE_NAME : database 생성
db : 현재 사용중인 데이터베이스 확인
show dbs : 데이터베이스 리스트 확인
db.dropDatabase() : database 제거(use DATABASE_NAME으로 db선택후에 진행)
db.createCollection(name, [options]) : name은 생성하려는 컬렉션의 이름, option은 document로 구성된 해당 컬렉션의 설정값
option 설명 :
capped	Boolean	이 값을 true 로 설정하면 capped collection 을 활성화 시킵니다. Capped collection 이란, 고정된 크기(fixed size) 를 가진 컬렉션으로서, size 가 초과되면 가장 오래된 데이터를 덮어씁니다. 이 값을 true로 설정하면 size 값을 꼭 설정해야합니다.
autoIndex	Boolean	이 값을 true로 설정하면, _id 필드에 index를 자동으로 생성합니다. 기본값은 false 입니다.
size	number	Capped collection 을 위해 해당 컬렉션의 최대 사이즈(maximum size)를 ~ bytes로 지정합니다.
max	number	해당 컬렉션에 추가 할 수 있는 최대 갯수를 설정합니다.

db.createCollection("books") : 옵션없이 컬렉션 생성
db.createCollection("articles", {
... capped: true,
... autoIndex: true,
... size: 6142800,
... max: 10000
... }) : 옵션끼고 생성
db.people.insert({"name": "velopert"}) : createCollection()메소드 사용하지 않고 document추가하면 컬렉션 자동 생성
show collections: 컬렉션 리스트 확인

db.COLLECTION_NAME.drop() : 컬렉션 제거
db.COLLECTION_NAME.insert(document): 컬렉션에 다큐먼트 추가
ex) db.books.insert({"name": "NodeJS Guide", "author": "Velopert"}) 이런식으로
db.COLLECTION_NAME.find() : 컬렉션의 다큐먼트 리스트 확인
db.COLLECTION_NAME.remove(criteria, justOne) : 다큐먼트 제거
remove매개변수
*criteria	document	삭제 할 데이터의 기준 값 (criteria) 입니다. 이 값이 { } 이면 컬렉션의 모든 데이터를 제거합니다.
justOne	boolean	선택적(Optional) 매개변수이며 이 값이 true 면 1개 의 다큐먼트만 제거합니다. 이 매개변수가 생략되면 기본값은 false 로 서, criteria에 해당되는 모든 다큐먼트를 제거합니다.

mongoDB
use DATABASE_NAME : database 생성
db : 현재 사용중인 데이터베이스 확인
show dbs : 데이터베이스 리스트 확인
db.dropDatabase() : database 제거(use DATABASE_NAME으로 db선택후에 진행)
db.createCollection(name, [options]) : name은 생성하려는 컬렉션의 이름, option은 document로 구성된 해당 컬렉션의 설정값
option 설명 :
capped	Boolean	이 값을 true 로 설정하면 capped collection 을 활성화 시킵니다. Capped collection 이란, 고정된 크기(fixed size) 를 가진 컬렉션으로서, size 가 초과되면 가장 오래된 데이터를 덮어씁니다. 이 값을 true로 설정하면 size 값을 꼭 설정해야합니다.
autoIndex	Boolean	이 값을 true로 설정하면, _id 필드에 index를 자동으로 생성합니다. 기본값은 false 입니다.
size	number	Capped collection 을 위해 해당 컬렉션의 최대 사이즈(maximum size)를 ~ bytes로 지정합니다.
max	number	해당 컬렉션에 추가 할 수 있는 최대 갯수를 설정합니다.

db.createCollection("books") : 옵션없이 컬렉션 생성
db.createCollection("articles", {
... capped: true,
... autoIndex: true,
... size: 6142800,
... max: 10000
... }) : 옵션끼고 생성
db.people.insert({"name": "velopert"}) : createCollection()메소드 사용하지 않고 document추가하면 컬렉션 자동 생성
show collections: 컬렉션 리스트 확인

db.COLLECTION_NAME.drop() : 컬렉션 제거
db.COLLECTION_NAME.insert(document): 컬렉션에 다큐먼트 추가
ex) db.books.insert({"name": "NodeJS Guide", "author": "Velopert"}) 이런식으로
db.COLLECTION_NAME.find() : 컬렉션의 다큐먼트 리스트 확인
db.COLLECTION_NAME.remove(criteria, justOne) : 다큐먼트 제거
remove매개변수
*criteria	document	삭제 할 데이터의 기준 값 (criteria) 입니다. 이 값이 { } 이면 컬렉션의 모든 데이터를 제거합니다.
justOne	boolean	선택적(Optional) 매개변수이며 이 값이 true 면 1개 의 다큐먼트만 제거합니다. 이 매개변수가 생략되면 기본값은 false 로 서, criteria에 해당되는 모든 다큐먼트를 제거합니다.

db.COLLECTION_NAME.find(query, projection)
query	 document 	Optional(선택적).  다큐먼트를 조회할 때 기준을 정합니다. 기준이 없이 컬렉션에 있는 모든 다큐먼트를 조회 할때는 이 매개변수를 비우거나 비어있는 다큐먼트 { } 를 전달하세요.
projection  document 	Optional. 다큐먼트를 조회할 때 보여질 field를 정합니다.

반환값 : cursor 
cursor : query 요청의 결과값을 가르키는 pointer, cursor객체를 통하여 보이는 데이터의 수를 제한 할 수도, 데이터를 sort할 수 도 있다. 10분동안 사용되지 않으면 만료된다.
db.articles.find().pretty() : 다큐먼트 깔끔하게 조회
db.articles.find( { “writer”: “Velopert” } ).pretty() : writer가 Velopert인 document 조회
db.articles.find( { “likes”: { $lte: 30 } } ).pretty() : likes값이 30이하인 document 조회

비교(Comparison) 연산자:
$eq	(equals) 주어진 값과 일치하는 값
$gt	(greater than) 주어진 값보다 큰 값
$gte	(greather than or equals) 주어진 값보다 크거나 같은 값
$lt	(less than) 주어진 값보다 작은 값
$lte	(less than or equals) 주어진 값보다 작거나 같은 값
$ne	(not equal) 주어진 값과 일치하지 않는 값
$in	주어진 배열 안에 속하는 값
$nin	주어빈 배열 안에 속하지 않는 값

db.articles.find( { “writer”: { $in: [ “Alpha”, “Bravo” ] } } ).pretty() : writer가 Alpha, Bravo에 해당하는 document 조회
db.articles.find({ $or: [ { “title”: “article01” }, { “writer”: “Alpha” } ] }) : title이 article01이거나 writer가 Alpha인 document 조회
db.articles.find( { $and: [ { “writer”: “Velopert” }, { “likes”: { $lt: 10 } } ] } ) :  writer값이 Velopert이고 likes값이 10미만인 document 조회
(= db.articles.find( { “writer”: “Velopert”, “likes”: { $lt: 10 } } ))

$regex 연산자
{ <field>: { $regex: /pattern/, $options: '<options>' } }
{ <field>: { $regex: 'pattern', $options: '<options>' } }
{ <field>: { $regex: /pattern/<options> } }
{ <field>: /pattern/<options> }
이런식으로 사용가능하고 $regex를 작성하지 않고도 사용이가능하다.
$option:
i	대소문자 무시
m	정규식에서 anchor(^) 를 사용 할 때 값에 \n 이 있다면 무력화
x	정규식 안에있는 whitespace를 모두 무시
s	dot (.) 사용 할 떄 \n 을 포함해서 매치

$where : $where 연산자를 통하여 javascript expression 을 사용 할 수 있습니다.
db.articles.find( { $where: “this.comments.length == 0” } ) : $where로 자바스크립트 언어를 사용하여 comments가 없는것 조회

$elemMatch 연산자 : $elemMatch 연산자는 Embedded Documents 배열을 쿼리할때 사용됩니다. 저희 mock-up data 에서는 comments 가 Embedded Document에 속합니다.
db.articles.find( { “comments”: { $elemMatch: { “name”: “Charlie” } } } ) : comments에 있는 배열에서 name이 Charlie인 document 조회
{
    "username": "velopert",
    "name": { "first": "M.J.", "last": "K."},
    "language": ["korean", "english", "chinese"]
  }
이런식으로 Embedded Document 배열이 아니라 아래 Document의 “name” 처럼 한개의 Embedded Document 일 시에는,
db.users.find({ "name.first": "M.J."}) : name document에서 배열이 아닌 한개의 embedded document first가 M.J인 것 조회 이렇게 사용한다.

Document의 배열이아니라 그냥 배열일 시에는 다음과 같이 Query 합니다.
db.users.find({"language": "korean"})


projection :  find()메소드의 두번째 파라미터, 쿼리의 결과값에서 보여줄 field를 정하는 것
db.articles.find( { } , { “_id”: false, “title”: true, “content”: true } ) : title, content값이 있는 것만 title, content만 조회
db.articles.find( { “title”: “article03” }, { comments: { $slice: 1 } } ) : query에 title이 article03인 것을 조회하고 projection에서 $slice로 comments를 하나만 보여주게끔 조회(제한을 거는것)

$elemMatch : query연산자의 것과 역할은 다르고 사용법은 같다. 
db.articles.find(
...     {
...         "comments": {
...             $elemMatch: { "name": "Charlie" }
...         }
...     },
...     {
...         "title": true,
...         "comments": {
...             $elemMatch: { "name": "Charlie" }
...         },
...         "comments.name": true,
...         "comments.message": true
...     }
... ) 이런식으로 query, projection에서 다 설정해줘야함

find()메소드 활용 - sort(), limit(), skip()
그냥 find()를 사용하면 criteria에 일치하는 모든 document들을 출력해주기 때문에 정리를 해야한다.
cursor형태로 반환되는 값의 객체가 가지고 있는 limit()메소드와 skip()메소드를 통해 출력문의 갯수를 제한할수 있고, sort()메소드를 사용하여 데이터를 순서대로 나열할 수 있다.

cursor.sort( DOCUMENT ) : 데이터를 정렬할 때 사용된다. 매개변수로는 어떤 KEY 를 사용하여 정렬 할 지 알려주는 document 를 전달한다.
다큐먼트의 구조 : { KEY: value }
KEY 는 데이터의 field 이름이고, value 의 값은 1 혹은 -1 입니다. 이 값을 1로 설정하면 오름차순으로, -1로 하면 내림차순으로 정렬
db.orders.find().sort( { "_id": 1 } ) : id를 기준으로 오름차순 정렬
db.orders.find().sort( { "amount": 1, "_id": -1 } ) : amount값을 기준으로 오름차순 정렬, 정렬한 값에서 id값을 기준으로 내림차순 정렬

cursor.limit( value ) : 출력할 데이터 갯수를 제한할 때 사용됩니다. value 파라미터는 출력 할 갯수 값 입니다.
db.orders.find().limit(3) : 출력할 갯수 3개로 제한

cursor.skip( value ) : 출력 할 데이터의 시작부분을 설정할 때 사용됩니다.  value 값 갯수의 데이터를 생략하고 그 다음부터 출력합니다.
db.orders.find().skip(2) : 앞에서부터 2개 데이터 skip하고 출력

var showPage = function(page){
... return db.orders.find().sort( { "_id": -1 } ).skip((page-1)*2).limit(2);
... } 이런식으로 응용하여 사용 가능 



