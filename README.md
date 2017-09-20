# MSOTI *"Together We Stand"*
Cours/TPs/Ressources

### ***structure du projet***

```
.
├── README.md
├── Traitement Images
│   ├── cours
│   │   ├── ch0 TI Initiation à Matlab.ppt.pdf
│   │   ├── ch1 TI.pdf
│   │   └── ch2 TI Filtrage.pdf
│   ├── ressources
│   └── tps
│       ├── TP1
│       │   ├── TP1 Ex3 .pdf
│       │   ├── TP1 sol.md
│       │   └── TP1 TI.pdf
│       └── TP2
│           ├── TP2 sol.md
│           └── TP2 TI.pdf
├── Architecture N Tiers J2EE
│   ├── cours
│   ├── ressources
│   └── tps
├── Gestion de projet
│   ├── cours
│   ├── ressources
│   └── tps
├── Informatique decisionnelle
│   ├── cours
│   ├── ressources
│   └── tps
├── Systemes Repartis
│   ├── cours
│   ├── ressources
│   └── tps
└── Vision par Ordinateur
    ├── cours
    ├── ressources
    └── tps

```


---
### How to contribute
1. install Git

2. Just head over to the [GitHub page](https://github.com/YounessFkhach/MSOTI) and click the "Fork" button. It's just that simple

3. install Git (or any other git client)

4. clone your fork repo
```bash
git clone https://github.com/<your USERNAME>/MSOTI.git
```
5. Add the original 'upstream' repo to list of remotes
```bash
git remote add upstream https://github.com/YounessFkhach/MSOTI.git
```
6. Whenever you want to update your fork with the latest upstream changes, you'll need to first fetch the upstream repo's branches and latest commits to bring them into your repository:
```bash
# Fetch from upstream remote
git fetch upstream
# Checkout your master branch and merge upstream
git checkout master
git merge upstream/master
```

7. make your changes

8. save changes locally
```bash
git commit
```
9. send saved changes to your fork repo
```bash
git pull origin master
```



10. now to add your contribution to the original repo just go  to "https://github.com/< Your USERNAME >/MSOTI/pulls" and open a new pull request to save changes to the original repo(https://github.com/YounessFkhach/MSOTI.git)

