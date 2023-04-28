USE lesson_5;

***** Создайте функцию, которая принимает кол-во сек и формат их в кол-во дней часов.
***** Пример: 123456 ->'1 days 10 hours 17 minutes 36 seconds '

delimiter //
DROP FUNCTION sec_convert;
CREATE FUNCTION sec_convert(sec INT)
RETURNS VARCHAR(45) DETERMINISTIC
BEGIN
  DECLARE days INT DEFAULT 0;
  DECLARE hours INT DEFAULT 0;
  DECLARE minutes INT DEFAULT 0;
  DECLARE seconds INT DEFAULT sec;
  DECLARE result VARCHAR(45) DEFAULT "";
  
  IF seconds >= 86400 THEN
  SET days = FLOOR(seconds/86400), seconds = seconds - days*86400;
  END IF;
  
  IF seconds >= 3600 THEN
  SET hours = FLOOR(seconds/3600), seconds = seconds - hours*3600;
  END IF;
  
  IF seconds >= 60 THEN
  SET minutes = FLOOR(seconds/60), seconds = seconds - minutes*60;
  END IF;
  
  -- 1 days 10 hours 17 minutes 36 seconds
  SET result = CONCAT(days, ' days ', hours, ' hours ', minutes, ' minutes ', seconds, ' seconds');
  RETURN result;
END //
delimiter ;

SELECT sec_convert(123456);

***** Выведите только четные числа от 1 до 10.
***** Пример: 2,4,6,8,10

delimiter //
DROP FUNCTION even_numbers;
CREATE FUNCTION even_numbers(`number` INT)
RETURNS VARCHAR(45)
DETERMINISTIC
BEGIN
	DECLARE num INT DEFAULT 2;
	DECLARE result VARCHAR(45) DEFAULT '';
	IF `number` < num THEN
		RETURN result;
	ELSE
		WHILE `number` >= num DO
		IF mod(num, 2) = 0 THEN 
			SET result = CONCAT(result, ' ', num);
            SET num = num + 2;
		ELSE
			SET num = num + 1;
        END IF;
		END WHILE;
	END IF;
	RETURN result;
END //
delimiter ;

SELECT  even_numbers(10);



