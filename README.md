# task3mongoDB

Collection Name: bsastudents

1: Написать запрос для поиска всех студентов, у которых score > 87% и < 93% по любому из типов выполненных заданий.

db.bsastudents.find({scores: {$elemMatch: {score: {$gt: 87, $lt: 93}}}})

результат - всего 52 записи

2: Написать запрос-агрегацию для выборки всех студентов, у которых результат по экзамену (type: "exam") более 90% (использование unwind)

db.bsastudents.aggregate([{$unwind: "$scores"}, {$match: {"scores.type": "exam", "scores.score": {$gt: 90}}}])

результат - всего 18 записей

3: Студентам с именем Dusti Lemmond добавить поле “accepted” со значением true.

db.bsastudents.update({name: "Dusti Lemmond"}, {$set: {accepted: true}}, {multi: true})

результат - всего 2 записи
