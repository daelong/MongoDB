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

