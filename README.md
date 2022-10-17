# THINGS IN HERE

## GEMS

```
# Use Sass to process CSS
gem "sassc-rails"

```

- only sass rails for .scss files


## MODELS
- todo lists: has many todo items
- todo items: has a method to check if the todo item has been completed

```
  def completed?
    !completed_at.blank?
  end
```
- then used a block to see if its completed or not

```
<% if todo_item.completed? %>
```

## OTHER
- he did his own styling
- added a css class based on whether the task is completed or not

```
<div class="row clearfix">
	<% if todo_item.completed? %>
		<div class="complete">
			<%= button_to complete_todo_list_todo_item_path(@todo_list, todo_item.id), method: :patch do %>
				<i style="opacity: 0.4;" class="fa fa-check"></i>
			<% end %>
		</div>
		<div class="todo_item">
			<p style="opacity: 0.4;"><strike><%= todo_item.content %></strike></p>
		</div>
		<div class="trash">
			<%= button_to todo_list_todo_item_path(@todo_list, todo_item.id), method: :delete, data: { confirm: "Are you sure?" } do %>
				<i class="fa fa-trash"></i>
			<% end %>
		</div>
	<% else %>
		<div class="complete">
			<%= button_to complete_todo_list_todo_item_path(@todo_list, todo_item.id), method: :patch do %>
				<i class="fa fa-check"></i>
			<% end %>
		</div>
		<div class="todo_item">
			<p><%= todo_item.content %></p>
		</div>
		<div class="trash">
			<%= link_to todo_list_todo_item_path(@todo_list, todo_item.id), method: :delete, data: { confirm: "Are you sure?" } do %>
				<i class="fa fa-trash"></i>
			<% end %>
		</div>
	<% end %>
</div>
```
