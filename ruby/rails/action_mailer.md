# Action Mailer Cheat Sheet


## Index
[Intro](#Intro)<br>
[Resources](#Resources)<br>
[UserMailer](#UserMailer)<br>
[Workflow](#Workflow)

<a name="Intro" />
## Intro
Use anytime you want to add email into your projects
<a name="Resources" />
## Resources
* [Action Mailer Basics from Rubyonrails.org](http://guides.rubyonrails.org/action_mailer_basics.html)
* [Letter Opener on Github](https://github.com/ryanb/letter_opener)
<a name="UserMailer" />

## UserMailer
* Rails treats mailers like MVCs. They create a folder called “mailers” that has user_mailer.rb, which acts like a controller.
* Missing view, so we have to find the view somewhere.
* This view is actually the email itself. Whatever you put here will be displayed in the email.

<a name="workflow" />
## Workflow
1. No installation necessary, yay!
2. To start, use letter opener: https://github.com/ryanb/letter_opener
3. In Gemfile, add this code inside group :development section
4. Add delivery method to config > environments > development.rb
config.action_mailer.delivery_method = :letter_opener
5. $ rails g mailer PageMailer → generally you want the name to match the resource its applying to
Note: you can also include options like $ rails g mailer PageMailer visit_happened welcome find_friends getting_started
6. Add to your controller, to the action you want the email to trigger
PageMailer.visit_happened.deliver
7. 



