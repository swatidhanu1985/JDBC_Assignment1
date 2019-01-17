# JDBC_Assignment1

SQL:

CREATE SCHEMA `sqlandjava` ;
CREATE TABLE `people` (
	`person_id` INT NOT NULL,
	`firstname` VARCHAR(50) NOT NULL,
	`lastname` VARCHAR(50) NOT NULL,
	PRIMARY KEY (`person_id`)
)

INSERT INTO `sqlandjava`.`people` (`person_id`, `firstname`, `lastname`) VALUES ('1', 'Ana', 'Bolt');
SELECT `person_id`, `firstname`, `lastname` FROM `sqlandjava`.`people` WHERE  `person_id`=1;
INSERT INTO `sqlandjava`.`people` (`person_id`, `firstname`, `lastname`) VALUES ('2', 'Carl', 'Dolk');
SELECT `person_id`, `firstname`, `lastname` FROM `sqlandjava`.`people` WHERE  `person_id`=2;
INSERT INTO `sqlandjava`.`people` (`person_id`, `firstname`, `lastname`) VALUES ('3', 'Erik', 'Fram');
SELECT `person_id`, `firstname`, `lastname` FROM `sqlandjava`.`people` WHERE  `person_id`=3;
INSERT INTO `sqlandjava`.`people` (`person_id`, `firstname`, `lastname`) VALUES ('4', 'Gina', 'Hult');
SELECT `person_id`, `firstname`, `lastname` FROM `sqlandjava`.`people` WHERE  `person_id`=4;


CREATE USER user@localhost IDENTIFIED BY 'password';
GRANT SELECT ON sqlandjava.people TO user@localhost;
