1. Найдите 10 самых часто встречающихся слов.
select plaintext from wordform limit 10;

2. Найдите все слова, которые начинаются с буквы ‘a’, регистр не должен иметь значения.
select plaintext from wordform where plaintext ilike 'a%';

3. Найдите все произведения, которые относятся к жанру ‘p’.
select title, genretype from work where genretype = 'p';

4. Найдите среднее количество параграфов в произведения жанра ‘t’.
select avg(totalparagraphs) from work where genretype = 't';

5. Выведите все произведения, в которых количество слов выше среднего.
select title from work where totalwords > (select avg(totalwords)from work);

6. Выведите имя героя, количество его реплик, и произведение, в котором этот герой встречается.
select charname, speechcount, work.title from character join character_work on character.charid = character_work.charid join work on character_work.workid = work.workid;

7. Выведите среднее количество реплик героев в произведении ‘Romeo and Juliet’.
select round(avg(speechcount)), work.title from character join character_work on character.charid = character_work.charid join work on character_work.workid = work.workid where work.title = 'Romeo and Juliet' group by work.title;

8. Выведите общее количество слов в каждой из секций в таблице paragraph.
select section, sum(wordcount) as total from paragraph group by section;

9. Выведите всех героев, которые имеют от 15 до 30 реплик.
select charname, speechcount from character where speechcount between 15 and 30;

10. Выведите все произведения, которые были написаны в 17 веке
select title, year from work where year between 1601 and 1699;

11. Найдите все произведения, которые имею в полном названии слово ‘the’.
select longtitle from work where longtitle like '%the%';

12. Выведите все уникальные секции в paragraph.
select distinct section from paragraph;

13. Для каждой главы выведите: id, описание и название произведения, к которой относится данная глава.
select chapterid, description, work.title from chapter join work on chapter.workid= work.workid;

14. Для каждого параграфа выведите: номер параграфа, имя героя, и количество реплик героя
select paragraphnum, character.charname, character.speechcount from paragraph join character on paragraph.charid = character.charid;

15. Для каждого параграфа выведите: номер параграфа, название произведения и год выхода этого произведения.
select paragraphnum, work.title, work.year from paragraph join work on paragraph.workid = work.workid;