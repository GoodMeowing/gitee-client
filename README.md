# Introduction
Unofficial Gitee client. Based on [official API doc](https://gitee.com/api/v5/swagger#/getV5ReposOwnerRepoStargazers?ex=no). Automatically integrates request sequence control and error retry mechanism.

# Usage
You need a token to authenticate. Login your Gitee platform, find `access token` from `settings`. You can generate a personal access token there.

``` ts
// init client with token
cosnt client = new GiteeRawClient({
  token: 'token',
});

// get repo issues
const issues = await client.issues.all({
    owner: 'goodmeowing',
    repo: 'push_test',
});;
// get repo prs
const pulls = await client.pulls.all({
    owner: 'goodmeowing',
    repo: 'push_test',
});;
// get basic repo data
const repos = await client.repos.getRepoData({
    owner: 'goodmeowing',
    repo: 'push_test',
});;
console.log(issues);
console.log(pulls);
console.log(repos);
```

You can handle rate control by passing a customized promise-handler
See `./src/promise-handler/promise-handler.ts`

``` ts
cosnt client = new GiteeRawClient({
  token: 'token',
  // pass your customized config
  new PromiseHandler();
});
```