# GitHub-Commit-To-Trello-Card
### GitHub Action to attach GitHub commits and pull requests to a Trello card

#### Action Marketplace
[https://github.com/marketplace/actions/github-commit-to-trello-card](https://github.com/marketplace/actions/github-commit-to-trello-card)

#### Action Variables
- **trello-api-key** - Trello API key, visit https://trello.com/app-key for key
- **trello-auth-token** - Trello auth token, visit https://trello.com/app-key then click generate a token
- **trello-board-id** - Trello board ID, visit a board then append .json to url to find id
- **trello-card-action** - Trello card action "Attachment PR" (more to come)

#### Git Commit
```
git add .
git commit -m "Add this commit to Trello card #123"
git push
```

#### GitHub Action
```
name: GitHub To Trello Comment

on: [pull_request]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v2

      - uses: dalezak/github-commit-to-trello-card@main
        with:
          trello-api-key: ${{ secrets.TRELLO_KEY }}
          trello-auth-token: ${{ secrets.TRELLO_TOKEN }}
          trello-board-id: ${{ secrets.TRELLO_BOARD }}
          trello-card-action: "Attachment"
```

#### Local Build
```
npm run build
```

#### Release Build
```
git tag -a "v2" -m "v2"
git push origin --tags
```
