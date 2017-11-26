# devise email validation 해제 하기

베리 심플!

### 1. user.rb

```ruby
devise :database_authenticatable, :registerable,
	   :recoverable, :rememberable, :trackable
	   # , :validatable
def email_required?
  false
end
```

:validatable 삭제하고 email_required를 만들어준다.

### 2. 뷰 작업

뷰에서 input type="email"로 되어 있기 때문에 바꿔준다.

```shell
rails g devise:views
```

view들을 생성해주고

* app/views/devise/sessions/new.html.erb

  ```erb
  [...]
  <%= f.text_field :email, required: false, autofocus: true %>
  [...]
  ```

* app/views/devise/registrations/edit.html.erb

  ```erb
  [...]
  <%= f.text_field :email, required: false, autofocus: true %>
  [...]
  ```

* app/views/devise/registrations/new.html.erb

  ```erb
  [...]
  <%= f.text_field :email, required: false, autofocus: true %>
  [...]
  ```

완성!!