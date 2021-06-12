# DevOps

## Git commands

### To host a project on GitHub:

1. Create a new repository in github
2. In VSCode open terminal
3. Initialize git 
```
git init
```
4. Create a .gitignore file in root and add node_modules in it
5. Add all files and commit
```
git add . && git commit -m "First Commit"
```
6. Add the remote git repository
```
git remote add origin <url_of_your_github_repo>
```
7. Push to github
```
git push origin master
```

### Everytime you make any changes:

1. Commit 
```
git commit -m "Commit message"
```
2. Push to github
```git push origin master
```

### Other commands

1. Change remote origin
```
git remote set-url origin <url_of_new_github_repo>
```

2. Check remote status
```
git remote -v
```

3. Remove remote origin
```
git remote rm origin
```


## Heroku

### Create new app and deploy

1. Create a new app
```
heroku create <app_name>
```

2. Add buildpacks of you're deploying Vue.JS app
```
heroku buildpacks:add heroku/nodejs
heroku buildpacks:add https://github.com/heroku/heroku-buildpack-static
```

3. Push build to heroku
```
git push heroku master
```

### Other commands

1. Environment Variables
```
//Check status
heroku config

// Get variables
heroku config:get GITHUB_USERNAME

// Set variables
heroku config:set GITHUB_USERNAME=joesmith

// Remove variables
heroku config:unset GITHUB_USERNAME
```

2. Rename app:
```
heroku apps:rename newname
```