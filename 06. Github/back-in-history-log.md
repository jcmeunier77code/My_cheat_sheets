# Going back in history

```
git log
```

Each commit has 
- unique commit hash
- commit message 
- author + date

helpfull for debugging things 

<img width="591" alt="image" src="https://user-images.githubusercontent.com/97024809/172992083-24230c60-f7f1-4383-8f1e-ca8c859ccbe3.png">

we can go back to a specific project version, with checkout commit-hash

then you'll be in a detached head state 

```
git checkout commit-hash
```

then you can test code or fic bugs (won't be saved)

when ready to go back 

```
git checkout branch-name
```

back to HEAD (pointing on the latest commit)



