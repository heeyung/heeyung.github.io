# [Github] 원격 저장소 URL 변경하기

### 원격 저장소(remote) URL 변경하기

기존 원격 저장소 URL을 변경하기 위해 **git remote set-url**명령어를 사용한다.

```shell
# View existing remotes
$ git remote -v
origin  https://github.com/user/repo.git (fetch)
origin  https://github.com/user/repo.git (push)

# Change the 'origin' remote's URL
$ git remote set-url origin https://github.com/user/repo2.git

# Verify new remote URL
$ git remote -v
origin  https://github.com/user/repo2.git (fetch)
origin  https://github.com/user/repo2.git (push)
```

Simple!

[참고 글](http://minsone.github.io/git/github-managing-remotes-changing-a-remotes-url)