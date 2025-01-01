# ClassicPress workflows for Plugins and Themes Developers

TOC: <a href="#add-zip-to-release">Add ZIP to release</a> | <a href="#cpcs">Check with CPCS</a>

In this repository you'll find GitHub workflows that you can use in your projects.

_Remember to check Action permissions in your repository under Settings -> Actions -> General screen, you should have "Workflow permissions" -> "Read and write permissions" ticked_

## Add ZIP to release <a name="add-zip-to-release"></a>

This workflow creates and attach to your release a properly crafted ZIP file.

The ZIP file will be called `<REPOSITORY-NAME>-<REF-NAME>.zip` (example: `doit-v9.0.5.zip`) and expand to a folder called `<REPOSITORY-NAME>`  (example: `doit`).

### Setup
- In your repo put `add-zip-to-release.yml` into `.github/workflows`.
- This workflows use your repository name as folder name, so change it if you have to do something more specific.
- Create a `.gitattribute` file on top of your repo to exclude specific files fron your release. As example:
  ```
  .github export-ignore
  .gitattributes export-ignore
  mystuff export-ignore
  .gitignore export-ignore
  ```

### Usage
Follow those steps to release a new version:
- From your repository go to "Releases".
- Draft a new release.
- In the "Choose a tag" dropdown put version number. 
- It will prompt "+ Create new tag: x.x.x on publish". Click on it.
  
  <img width="363" alt="Create new tag" src="https://github.com/ClassicPress/dev-workflows/assets/29772709/2b46f344-a248-48a9-a67a-eb4a019b18b7">

- Enter a title and a description for your release.
- Click on publish.
- Leave the workflow time to run. You'll get the ZIP file attached to the release.
  
  <img width="943" alt="Release created" src="https://github.com/ClassicPress/dev-workflows/assets/29772709/07a11939-6ad3-42b1-9dc5-ed0106b5f40f">

## Check with CPCS (ClassicPress Directory Coding Standard) <a name="cpcs"></a>

### Setup
- In your repo put `cpcs.yml` into `.github/workflows`.
- Edit `cpcs.yml` on line 17 to reflect your Text Domain.
  ```
  sed -i '/MY_DOMAIN/ s//CHANGE-THIS-TO-YOUR-TEXT-DOMAIN/' phpcs.xml
                         ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  ```

### Usage
The workflow is triggered on Pull request creation.
You'll see if the test is passing.
If it fails you'll see in your PR.

<img width="822" alt="image" src="https://github.com/ClassicPress/dev-workflows/assets/29772709/fd346ca6-39ed-442f-8b83-a7121d1e9a09">

You can check what is failing from the annotations in "File changed" tab.

<img width="1159" alt="image" src="https://github.com/ClassicPress/dev-workflows/assets/29772709/e5cdc13b-c854-4519-84cf-e6e13dd001d4">

Also in the Action Summary you'll find `cpcs` output.

<img width="959" alt="image" src="https://github.com/ClassicPress/dev-workflows/assets/29772709/57d7b4dc-3e35-41f7-9c9c-98efd5a8f908">
