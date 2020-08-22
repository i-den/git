Common Operations
```bash
Working Directory                        Staging Area                        Local Git Repo
        | >>-----------Stage git add -------> |                                     |
        |                                     | >>---------- Commit git commit ---> |
        |                                     |                                     |
        | <--------------- Overwrite with a certain version git checkout --------<< |
```

Lifecycles
```bash
Working Directory                        Staging Area                        Local Git Repo
  Untracked                               Staged 
  Modified
  Unmodified                              Unmodified                           Unmodified
```