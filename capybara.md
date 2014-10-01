#Must read links:
* [http://robots.thoughtbot.com/write-reliable-asynchronous-integration-tests-with-capybara](Write Reliable, Asynchronous Integration Tests With Capybara - Written by thoughtbot)

#Cheatsheet
based on [https://gist.github.com/zhengjia/428105](https://gist.github.com/zhengjia/428105)

##Navigating

```ruby
visit('/projects')
visit(post_comments_path(post))
```

##Clicking links and buttons

```ruby
click_link('id-of-link')
click_link('Link Text')
click_button('Save')
click('Link Text') # Click either a link or a button
click('Button Value')
```

##Interacting with forms

```ruby
fill_in('First Name', :with => 'John')
fill_in('Password', :with => 'Seekrit')
fill_in('Description', :with => 'Really Long Textâ€¦')
choose('A Radio Button')
check('A Checkbox')
uncheck('A Checkbox')
attach_file('Image', '/path/to/image.jpg')
select('Option', :from => 'Select Box')
```

##scoping

```ruby
within("//li[@id='employee']") do
  fill_in 'Name', :with => 'Jimmy'
end

within(:css, "li#employee") do
  fill_in 'Name', :with => 'Jimmy'
end

within_fieldset('Employee') do
  fill_in 'Name', :with => 'Jimmy'
end

within_table('Employee') do
  fill_in 'Name', :with => 'Jimmy'
end
```

##Querying

```ruby
expect(page).to have_xpath('//table/tr')
expect(page).to have_css('table tr.foo')
expect(page).to have_content('foo')
find_field('First Name').value
find_link('Hello').visible?
find_button('Send').click
find('//table/tr').click
locate("//*[@id='overlay'").find("//h1").click
all('a').each { |a| a[:href] }
```

##Scripting

```ruby
result = page.evaluate_script('4 + 4')
```

##Debugging

```ruby
save_and_open_page
```

##Asynchronous JavaScript

```ruby
click_link('foo')
click_link('bar')
expect(page).to have_content('baz')
expect(page).to_not have_xpath('//a')
expect(page).to have_no_xpath('//a')
```

##XPath and CSS

```ruby
within(:css, 'ul li') { ... }
find(:css, 'ul li').text
locate(:css, 'input#name').value
Capybara.default_selector = :css
within('ul li') { ... }
find('ul li').text
locate('input#name').value
```
