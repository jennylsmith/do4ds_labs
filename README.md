## DevOps for Data Science

### Labs and Activities 

These are the labs following the book [DevOps for Data Science](https://do4ds.com/) by Alex K Gold. 

### Usage

#### Pre-requisites

- github account
- gitpod account
- VSCode IDE installed
- VSCode extensions installed
  - Remote SSH 
  - Gitpod Flex

#### Gitpod AWS Runner

1. Go to Project Link on [Gitpod](https://app.gitpod.io/projects?project=01934c12-4d07-7185-bcb1-cce2999becda)

![](/assets/project_env_settings_1.png)

2. Create a new environment 

![](/assets/project_env_settings_2.png)

3. Select open with VSCode 

![](/assets/vscode_integration_1.png)

Next, the VSCODE application will launch with Gitpod workspace and connect to the AWS runner using `remote-ssh` extension.

![](/assets/vscode_integration_2.png)


#### Gitpod Local

Alternatively, you can run the project locally using Gitpod.

1. Install Gitpod Desktop
    - [Gitpod Desktop](https://www.gitpod.io/docs/desktop)


1. Go to Project Link on [Gitpod](https://app.gitpod.io/projects?project=01934c12-4d07-7185-bcb1-cce2999becda)

![](/assets/project_env_settings_1.png)

2. Create a new environment 

![](/assets/project_env_settings_2.png)

3. Select open with VSCode 

![](/assets/vscode_integration_1.png)

Next, the VSCODE application will launch with local Gitpod container using the `remote-ssh` extension.

![](/assets/vscode_integration_2.png)


## Contributing

If you would like to contribute to this project, please fork the repository and create a pull request.


### Create a new branch

```bash
BRANCH_NAME=feat_branch
git checkout -b $BRANCH_NAME
```
### Commit changes

```bash
git add . 
git commit -m "Add [DESCRIPTION]"
```
### Push changes

```bash
git push origin $BRANCH_NAME
```
### Create a pull request

```bash
gh pr create -B dev -H $BRANCH_NAME \
  --title "TITLE" \
  --body "[DESCRIPTION]" \
  --draft \
  --dry-run
```


