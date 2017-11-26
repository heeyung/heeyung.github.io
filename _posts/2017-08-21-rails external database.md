# rails external database

레일즈 외부 데이터베이스 연결해보기

1. 외부 mysql - 아직 안 해봄

   Gemfile

   ```ruby
   gem 'mysql2'
   ```

   [블로그](http://cobwwweb.com/connect-to-a-remote-mysql-database-in-rails) 참고했음
   config/database.yml

   ```yaml
   [rails_env]:
     adapter: mysql2
     encoding: utf8
     pool: 5
     host: [mysql_ip]
     username: [mysql_username]
     password: [mysql_password]
     port: [mysql_port]
     socket: [path_to_mysql_socket_file]
     database: [db_name]
   ```

   The **rails_env** is likely either **development** or **production**, while the others are values you either just created or found.

2. rds

   일단 [이거](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/create_deploy_Ruby.rds.html) 보기

   ![ss](https://s3.ap-northeast-2.amazonaws.com/dgulionsession/%EC%BA%A1%EC%B2%98.PNG)

   ```yaml
   [rails_env]:
     adapter: mysql2
     encoding: utf8
     database: <%= ENV['RDS_DB_NAME'] %>
     username: <%= ENV['RDS_USERNAME'] %>
     password: <%= ENV['RDS_PASSWORD'] %>
     host: <%= ENV['RDS_HOSTNAME'] %>
     port: <%= ENV['RDS_PORT'] %>
   ```

   perfect!

