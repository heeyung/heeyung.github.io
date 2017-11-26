---
layout: post
title: rails multiple database table
category: rails
---

# Rails Multiple Database Table

user 테이블만 다른 데이터베이스에서 정보를 가지고 와야했다.

#### database 설정

**database.yml**

```yaml
default: &default
  adapter: mysql2
  encoding: utf8
  database: <%= ENV['FIRST_DB_NAME'] %>
  username: <%= ENV['FIRST_USERNAME'] %>
  password: <%= ENV['FIRST_PASSWORD'] %>
  host: <%= ENV['FIRST_HOSTNAME'] %>
  port: <%= ENV['FIRST_PORT'] %>

second_db:
  adapter: mysql2
  encoding: utf8
  database: <%= ENV['SECOND_DB_NAME'] %>
  username: <%= ENV['SECOND_USERNAME'] %>
  password: <%= ENV['SECOND_PASSWORD'] %>
  host: <%= ENV['SECOND_HOSTNAME'] %>
  port: <%= ENV['SECOND_PORT'] %>
[...]
```

이렇게 default말고 다른 database connection을 열어놓는다. 이 방법의 좋은 점은 또 다른 외부 디비를 ActiveRecord로 사용할 수 있다는 점이다.

#### activerecord 연결

**app/models/custom.rb**

```ruby
class Custom < ActiveRecord::Base
  establish_connection(:second_db)   
  self.table_name = 'users'
end
```

파일 명이나 클래스명은 마음대로 한다. `establish_connection(다른 database connection)`을 통해서 외부 디비 설정을 가지고 오고 그 다음 `self.table_name`을 통해서 사용할 table 명을 설정한다.

#### 사용

**bash**

```shell
$ Custom.all
[...]
```

외부 DB 의 테이블을 `activerecord`로 사용할 수 있다.

#### 주의

rake db:drop 이나 :migrate등의 명령어에는 포함되지 않는다.

## reference

[블로그](http://imnithin.in/multiple-database.html)

