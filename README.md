# JDBC_Assignment1


SQL: 1a

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


JAVA : 1b

package sqlandjava;
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.ResultSet;
import java.sql.Statement;


public class Assignment1 {
	
	public static Connection getConnection() throws Exception {
		try {
			String url = "jdbc:mysql://localhost:3306/sqlandjava";
			String username = "user";
			String password = "password";
			
			Connection conn = DriverManager.getConnection(url,username,password);
			System.out.println("Connected to Database!");
			return conn;
		}catch(Exception e)
		{
			System.out.println(e);
		}
		return null;
	}

	public static void main(String[] args) throws Exception {
		// TODO Auto-generated method stub
        Connection conn = getConnection();
        
        Statement statement = conn.createStatement();
        
        ResultSet res = statement.executeQuery("Select * from people");
        
        while(res.next()) {
        	System.out.println(res.getString("person_id")+ ":" + res.getString("firstname")+" "+ res.getString("lastname"));
        }
	}

}

Connected to Database!
1:Ana Bolt
2:Carl Dolk
3:Erik Fram
4:Gina Hult
