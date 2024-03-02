# SQL-tasks

## Subtask 1 (Podstawy SQL)

Poniżej przedtawiono podstawowe komendy SQL

  * **SELECT** -is used to select data from a database.
  
        SELECT column1, column2, ...
        FROM table_name; 
  
  * **WHERE**- is used to filter records.
  
        SELECT column1, column2, ...
        FROM table_name
        WHERE condition; 
* **AND, OR, NOT**
	
	The WHERE clause can be combined with AND, OR, and NOT operators.
	
	The AND and OR operators are used to filter records based on more than one condition:

    The AND operator displays a record if all the conditions separated by AND are TRUE.
    The OR operator displays a record if any of the conditions separated by OR is TRUE.
    The NOT operator displays a record if the condition(s) is NOT TRUE.
 
 * **ORDER BY**- is used to sort the result-set in ascending or descending order.

        SELECT column1, column2, ...
        FROM table_name
        ORDER BY column1, column2, ... ASC|DESC; 
        
  * **INSERT INTO**- is used to insert new records in a table.

        INSERT INTO table_name (column1, column2, column3, ...)
        VALUES (value1, value2, value3, ...); 
	
  * **BETWEEN**- selects values within a given range.
  
        SELECT column_name(s)
        FROM table_name
        WHERE column_name BETWEEN value1 AND value2; 
  
  * **IN Operator**- allows to specify multiple values in a WHERE clause.
  		
		SELECT column_name(s)
		FROM table_name
		WHERE column_name IN (value1, value2, ...); 
		
* **LIKE**- is used in a WHERE clause to search for a specified pattern in a column.

		SELECT column1, column2, ...
		FROM table_name
		WHERE columnN LIKE pattern; 

* **NULL**

		SELECT column_names
		FROM table_name
		WHERE column_name IS NULL;


  ## Subtask 2

**1. Wyświetl tabelę actors w kolejności alfabetycznej sortując po kolumnie surname.**

    SELECT* FROM actors
    ORDER BY surnamer;

![1](https://github.com/olawydmuch/challenge_portfolio_olaw/assets/131545880/c51c95d7-4b66-40e9-b3f2-a8b5bdba39ab)

**2. Wyświetl film, który powstał w 2019 roku.**

    SELECT* FROM movies
    WHERE year_of_production=2019;

![2](https://github.com/olawydmuch/challenge_portfolio_olaw/assets/131545880/aaf61a9e-54a9-49ff-bf24-fcfb34814d83)

**3. Wyświetl wszystkie filmy, które powstały między 1900, a 1999 rokiem.**

    SELECT* FROM movies
    WHERE year_of_production BETWEEN 1900 AND 1999;

![3](https://github.com/olawydmuch/challenge_portfolio_olaw/assets/131545880/ca14b42b-9f99-4cc5-9790-d9c2dc522ed6)

**4. Wyświetl JEDYNIE tytuł i cenę filmów, które kosztują poniżej 7$**

    SELECT title
	        ,price
    FROM movies
    WHERE price<=7
    
![4](https://github.com/olawydmuch/challenge_portfolio_olaw/assets/131545880/1ea4ecd0-d520-4591-8dcb-6024e5b9a82a)

**5. Użyj operatora logicznego AND, aby wyświetlić aktorów o actor_id pomiędzy 4-7 (4 i 7 powinny się wyświetlać). NIE UŻYWAJ operatora BETWEEN**

	SELECT*FROM actors
	WHERE actor_id>3 AND actor_id<8
	
![5](https://github.com/olawydmuch/challenge_portfolio_olaw/assets/131545880/0c85e38c-bad5-4969-b4e5-b988e12c5830)

**6. Wyświetl klientów o id 2,4,6 wykorzystaj do tego warunek logiczny.**

	SELECT*FROM customer
	customer_id=2 OR customer_id=4 OR customer_id=6

![6](https://github.com/olawydmuch/challenge_portfolio_olaw/assets/131545880/81e87091-3318-4ca8-a7b9-fc59fc8227dd)

**7. Wyświetl klientów o id 1,3,5 wykorzystaj do tego operator IN.**

	SELECT*FROM customers
	WHERE customer_id IN ('1', '3', '5');
	
![7](https://github.com/olawydmuch/challenge_portfolio_olaw/assets/131545880/0f68cc6f-0c92-4dfc-bd58-15d505e03dac)
	
**8. Wyświetl dane wszystkich osób z tabeli ‘actors’, których imię zaczyna się od ciągu “An”.**

	SELECT * FROM actors
	WHERE name LIKE 'An%';
	
![8](https://github.com/olawydmuch/challenge_portfolio_olaw/assets/131545880/51d46e49-0dc2-4ae2-a6ee-144809fa071c)

**9. Wyświetl dane klienta, który nie ma podanego adresu email.**

	SELECT * FROM Customers
	WHERE email IS NULL;
	
![9](https://github.com/olawydmuch/challenge_portfolio_olaw/assets/131545880/a758c442-56c5-4beb-b6e4-1b2e64494e76)

**10. Wyświetl wszystkie filmy, których cena wynosi powyżej 9$ oraz ich ID mieści się pomiędzy 2 i 8 movie_id.**

	SELECT * FROM movies
	WHERE price>8 AND movie_id BETWEEN 2 AND 8;
	
![10](https://github.com/olawydmuch/challenge_portfolio_olaw/assets/131545880/280fa9e9-17e2-4012-9c06-057af6cf6e61)


**11. Popełniłam błąd wpisując nazwisko Ani Miler – wpisałam Muler. Znajdź i zastosuj funkcję, która poprawi mój karkołomny błąd 🙈**

	UPDATE customers SET surname='Miler' WHERE name='Ania';
	
![11](https://github.com/olawydmuch/challenge_portfolio_olaw/assets/131545880/0cc5ca6b-8b59-42f9-8b5b-84f099e2fb1f)

**12. Pobrałam za dużo pieniędzy od klienta, który kupił w ostatnim czasie film o id 4. Korzystając z funkcji join sprawdź, jak ma na imię klient i jakiego ma maila. W celu napisania mu wiadomości o pomyłce fantastycznej szefowej.**

	SELECT sale.movie_id, customers.name, customers.email
	FROM sale
	INNER JOIN customers
	ON sale.customer_id=customers.customer_id;

![12](https://github.com/olawydmuch/challenge_portfolio_olaw/assets/131545880/fc1cd32b-9fe5-4504-80f7-2a1bffb7646a)

**13. Na pewno zauważył_ś, że sprzedawca zapomniał wpisać emaila klientce Patrycji. Uzupełnij ten brak wpisując: pati@mail.com**

	UPDATE customers
	SET email = 'pati@mail.com'
	WHERE name = 'Patrycja';

	SELECT * FROM customers
	
![13](https://github.com/olawydmuch/challenge_portfolio_olaw/assets/131545880/12a1abe7-647a-4d1d-aab8-f59eea7fbb39)

**14. Dla każdego zakupu wyświetl, imię i nazwisko klienta, który dokonał wypożyczenia oraz tytuł wypożyczonego filmu. (wykorzystaj do tego funkcję inner join, zastanów się wcześniej, które tabele Ci się przydadzą do wykonania ćwiczenia).**

	SELECT customers.name, customers.surname, movies.title
		FROM ((sale
		INNER JOIN customers ON sale.customer_id=customers.customer_id)
    		INNER JOIN movies ON sale.movie_id=movies.movie_id);

![14](https://github.com/olawydmuch/challenge_portfolio_olaw/assets/131545880/32380fca-40d2-409e-a1b6-3850f2ef5722)

**15. W celu anonimizacji danych, chcesz stworzyć pseudonimy swoich klientów. - Dodaj kolumnę o nazwie ‘pseudonym’ do tabeli customer,- Wypełnij kolumnę w taki sposób, aby pseudonim stworzył się z dwóch pierwszych liter imienia i ostatniej litery nazwiska. Np. Natalie Pilling → Nag**

	ALTER TABLE customers
	ADD pseudonim varchar(255);
	UPDATE customers SET pseudonim='Ols' WHERE customer_id='1';
	UPDATE customers SET pseudonim='Kal' WHERE customer_id='2';
	UPDATE customers SET pseudonim='Anr' WHERE customer_id='3';
	UPDATE customers SET pseudonim='Par' WHERE customer_id='4';
	UPDATE customers SET pseudonim='Mao' WHERE customer_id='5';
	UPDATE customers SET pseudonim='Nag' WHERE customer_id='6';
	SELECT * FROM customers;
    
![15](https://github.com/olawydmuch/challenge_portfolio_olaw/assets/131545880/67fd9bb5-1508-409d-bcbb-15975e03545e)

**16. Wyświetl tytuły filmów, które zostały zakupione, wyświetl tabelę w taki sposób, aby tytuły się nie powtarzały.**

	SELECT DISTINCT movies.title
		FROM sale
		INNER JOIN movies
		ON sale.movie_id=movies.movie_id;

![16](https://github.com/olawydmuch/challenge_portfolio_olaw/assets/131545880/3614a721-1971-4545-89ce-bc61fd5367bc)

**17. Wyświetl wspólną listę imion wszystkich aktorów i klientów, a wynik uporządkuj alfabetycznie. (Wykorzystaj do tego funkcji UNION)**

	SELECT name FROM actors
	UNION
	SELECT name FROM customers
	ORDER By name;

![17](https://github.com/olawydmuch/challenge_portfolio_olaw/assets/131545880/bfaecae9-ec6f-487e-84c3-efecd0fabec8)

**18. Polskę opanowała inflacja i nasz sklepik z filmami również dotknął ten problem. Podnieś cenę wszystkich filmów wyprodukowanych po 2000 roku o 2,5 $ (Pamiętaj, że dolar to domyślna jednostka- nie używaj jej nigdzie).**

	UPDATE movies SET  price = price + 2.5  WHERE year_of_production >2000;
	SELECT * FROM movies
	
![18](https://github.com/olawydmuch/challenge_portfolio_olaw/assets/131545880/95f541b7-3b10-4394-a1f5-924c14d136f3)

**19. Wyświetl imię i nazwisko aktora o id 4 i tytuł filmu, w którym zagrał**

	SELECT actors.actor_id, actors.name, actors.surname, movies.title
		FROM ((cast
		INNER JOIN actors ON cast.actor_id=actors.actor_id)
    	INNER JOIN movies ON cast.movie_id=movies.movie_id)
	WHERE actors.actor_id='4';

![19](https://github.com/olawydmuch/challenge_portfolio_olaw/assets/131545880/9276b65a-28e0-4a45-9cbb-93c8bb40cae0)

**20. A gdzie nasza HONIA!? Dodaj do tabeli customers nową krotkę, gdzie customer_id = 7, name = Honia, surname = Stuczka-Kucharska, email = honia@mail.com oraz pseudonym = Hoa**

	INSERT INTO customers (customer_id, name, surname, email, pseudonim)
	VALUES ('7', 'Honia', 'Stuczka-Kucharska', 'honia@mail.com', 'Hoa');

	SELECT * FROM customers

![20](https://github.com/olawydmuch/challenge_portfolio_olaw/assets/131545880/0942b5b1-6231-429e-943b-97dcfec9eb37)

