# Coverage Reporter - Action

This action was developed to be used on projects that do not have a CI/CD pipeline, such as LIBs and Packages like ARCO.

This action uses the [paambaati/codeclimate-action@v3.2.0](https://github.com/paambaati/codeclimate-action) as base and was developed to be the central action of Coverage report of [@Corabank](https://github.com/corabank) projects.

## How to use this Action to generate your coverage reporter

To use this action you need to create an action on your project and set this action as part of the steps of your action

```yml
name: Cora - Coverage Reporter

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  coverage:
    runs-on: ubuntu-latest
    steps:
      - name: Run tests and upload coverage
        #Here we pass the version of front-coverage-action tag.
        #We can have multiple versions
        uses: corabank/front-coverage-action/coverage@v0.0.1
        with:
          reporterId: ${{ secrets.CC_TEST_REPORTER_ID }}
          coverageCommand: test:coverage
          nodeVersion: 16.x
```

## Inputs

Here we can see how the Inputs of `with` options of the action.
There's only one required input to set, the `reporterId`, as we can see bellow:

| Input           | Required | Default | Description                                                                               |
| :-------------- | :------- | :------ | :---------------------------------------------------------------------------------------- |
| reporterId      | true     | -       | CodeClimate CC_TEST_REPORTER_ID. <br/><small>Tip: Create a Github Secret for this</small> |
| coverageCommand | false    | jest    | Coverage command of your application                                                      |
| nodeVersion     | false    | 16.x    | Here you can change the version of node to fit weith your app node version                |
