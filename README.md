# SpringSecurityJdbcApp


http://www.programming-free.com/2015/09/spring-security-password-encryption.html



=========
DROP TABLE IF EXISTS users;
DROP TABLE IF EXISTS user_roles;
CREATE  TABLE users (
  userid VARCHAR(5) NOT NULL,
  username VARCHAR(45) NOT NULL ,
  password VARCHAR(60) NOT NULL ,
  enabled TINYINT NOT NULL DEFAULT 1 ,
  PRIMARY KEY (userid));
  
CREATE TABLE user_roles (
  user_role_id int(11) NOT NULL AUTO_INCREMENT,
  userid varchar(5) NOT NULL,
  role varchar(45) NOT NULL,
  PRIMARY KEY (user_role_id),
  UNIQUE KEY uni_username_role (role,userid),
  KEY fk_username_idx (userid),
  CONSTRAINT fk_username FOREIGN KEY (userid) REFERENCES users (userid));

INSERT INTO users(userid,username,password,enabled)
VALUES ('001','priya','$2a$04$CO93CT2ObgMiSnMAWwoBkeFObJlMYi/wzzOnPlsTP44r7qVq0Jln2', true);
INSERT INTO users(userid,username,password,enabled)
VALUES ('002','naveen','$2a$04$j3JpPUp6CTAe.kMWmdRNC.Wie58xDNPfcYz0DBJxWkucJ6ekJuiJm', true);

INSERT INTO user_roles (userid, role)
VALUES ('002', 'ROLE_USER');
INSERT INTO user_roles (userid, role)
VALUES ('001', 'ROLE_ADMIN');
INSERT INTO user_roles (userid, role)
VALUES ('001', 'ROLE_USER');

=========