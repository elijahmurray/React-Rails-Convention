This is a demonstration of the basic full SPA react setup.  

The goal of the app is to provide a convention for React + Rails Combo.  

It has no rails oriented setup(for now at least). Any suggestions, be it milestones,
folder structure, dependencies are very welcome.  

There are two types of apps in Netguru(source: Pavel "Gdański Koksu" Jędrzejczyk).  
One type is full SPA app, and this repo is the representation of it's initial setup.

To create an app with latest tools(mostly dev ones):  

npm i -g create-react-app  
rails new netguruSPA --api  
git init  
create-react-app client  
echo "client/node_modules” >> Gemfile  
echo "gem 'foreman'" >> Gemfile  
bundle install  
touch Procfile  
echo "api: bundle exec rails s -p 3000” >> Procfile  
echo "web: cd client && npm start" >> Procfile  
touch lib/tasks/start.rake  


Add to lib/tasks.start.rake:  
task :start do  
  exec 'foreman start -p 3000'  
end  

Add to head tag in client/public/index.html(only if using react-bootstrap or bootstrap):  
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/latest/css/bootstrap.min.css">  

Add to package.json: "proxy": "http://localhost:3000/,  

cd client && npm i dotenv i18n-js lodash moment redux redux-form redux-saga react-router   react-router-redux react-datepicker react-bootstrap --save  

And lastly:  
npm i ava --save-dev  


Cd to top folder and run rake start. If everything works do:  
Git add .  
Git commit -m „Init NetguruSPA”  
