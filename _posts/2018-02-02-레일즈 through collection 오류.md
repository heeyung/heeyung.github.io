# 180202 오류

*view*

```erb
<div class="container">
  <%= simple_form_for @influencer do |f| %>
    <%= f.error_notification %>
    <div class="row">
      <div class="col-sm-6">
        <%= f.input :location %>
      </div>
      <div class="col-sm-6">
        <%= f.input :gender, as: :radio_buttons, collection: [['male', '1'], ['female', '2']]%>
      </div>
      <div class="col-sm-12">
        <%= f.input :image %>
      </div>
      <div class="col-sm-12">
        <%= f.input :description %>
      </div>
      <div class="col-sm-4">
        <!-- 원래는 이거다. -->
        <%= f.collection_check_boxes :language_ids, Language.all, :id, :name do |l| %>
          <%= l.check_box %>
          <%= l.label %> &nbsp;&nbsp;
        <% end %>
		<!-- 이부분 이 내가 암걸린 부분 강제로 만들었다. -->
        <% Language.all.each_with_index do |language,index| -%>
            <label for="influencer_influencer_languages_attributes_<%=index%>_language_id"><input type="checkbox" value="<%=language.id%>" name="influencer[influencer_languages_attributes][<%=index%>][language_id]" id="influencer_influencer_languages_attributes_<%=index%>_language_id"><%=language.name%></label>
        <% end %>

        <%= simple_fields_for :language_ids do |language| %>
          <%= f.association :influencer_languages ,collection: Language.all,:label_method => :name ,:value_method => :id%>
        <% end %>
      </div>
      <div class="col-sm-4">
        <%= f.input :category_ids, collection: Category.all%>
      </div>
      <div class="col-sm-4">
        <%= f.input :client_ids, collection: Client.all%>
      </div>
    </div>

    <div class="row buttons-row">
      <div class="col-md-6 col-sm-6">
        <%= f.submit "정보 입력", class: "btn btn-primary btn-block btn-round" %>
      </div>
    </div>
  <% end %>
</div>

```

*controller*

```ruby
[...]
  def influencer_params
    params.require(:influencer).permit(:location, :description, :image, :gender, language_ids: [],influencer_languages_attributes: [:language_id])
  end
[...]
```

저기 language_ids로 위의 코드가 작동된다. attributes 코드는 뻘짓의 후예