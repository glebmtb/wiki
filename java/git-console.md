**List All Branches**
```
//To see local branches, run this command: 
git branch
//To see remote branches, run this command: 
git branch -r
//To see all local and remote branches, run this command: 
git branch -a
//сортировка
git branch --sort=-committerdate  # DESC
git branch --sort=committerdate  # ASC
```

**переход между ветками**
```
// сменить на локальную ветку
git checkout my-branch-name
//переход на удаленую ветку
git checkout --track origin/my-branch-name
```
