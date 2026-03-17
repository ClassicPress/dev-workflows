# ClassicPress workflows for Plugin and Theme Developers

In this repository you'll find GitHub workflows that you can use in your projects.

For information about developing plugins and themes for ClassicPress visit the [Plugin Guidelines](https://docs.classicpress.net/plugin-guidelines/) and [Theme Guidelines](https://docs.classicpress.net/theme-guidelines/).

## Table of Contents

- [Workflow permissions](#workflow-permissions)
- [Add ZIP to release](#add-zip-to-release)
- [Check with CPCS](#cpcs)


## Workflow permissions <a name="workflow-permissions"></a>

Remember to check that the Action permissions in your repository under Settings -> Actions -> General screen is set to "Workflow permissions" -> "Read and write permissions".

## Add ZIP to release <a name="add-zip-to-release"></a>

The following information applies to plugins and themes that are submitted to and listed in the [CP Directory](https://directory.classicpress.net/).

This workflow creates a properly crafted ZIP file and attaches this file to your release.

You can also add a ZIP file (that contains your plugin or theme) from elsewhere. See the [Plugin Directory Requirements](https://docs.classicpress.net/plugin-guidelines/directory-requirements/) and [Theme Directory Requirements](https://docs.classicpress.net/theme-guidelines/theme-directory-requirements/) for instructions.

### Setup
- In your repo create a folder called `.github/workflows` and add file `add-zip-to-release.yml` from the `workflows` folder of [this repository](https://github.com/ClassicPress/dev-workflows).
- This workflow uses your repository name as folder name, so change it if you have to do something more specific.
- Create a file called `.gitattributes` on top of your repo to exclude specific folders and files from your release (such as folder `.github/workflows` and file `.gitattributes`). Example:

  ```
  .github export-ignore
  .gitattributes export-ignore
  .gitignore export-ignore
  ```

### Usage
Follow these steps to release a new version:
- From your repository go to "Releases".
- Draft a new release.
- In the "Select tag" dropdown click "Create new tag".

<img width="364" height="249" alt="Create new tag" src="https://github.com/user-attachments/assets/6622b0d2-c02b-404b-a90d-b8561f73f236" />

- Enter (new) version number. Please respect [Semantic Versioning](https://semver.org/).

<img width="341" height="272" alt="Add new tag" src="https://github.com/user-attachments/assets/77f35506-d820-4de1-a09a-6d3095cce53a" />

- Enter a title and a description for your release.
- Click on publish.
- Leave the workflow time to run. You'll get the ZIP file attached to the release.
  
  <img width="943" alt="Release created" src="https://github.com/ClassicPress/dev-workflows/assets/29772709/07a11939-6ad3-42b1-9dc5-ed0106b5f40f">

## Check with CPCS (ClassicPress Directory Coding Standard) <a name="cpcs"></a>

### Setup
- In your repo create a folder called `.github/workflows` and add file `cpcs.yml` from the `workflows` folder of [this repository](https://github.com/ClassicPress/dev-workflows).
- Edit `cpcs.yml` on line 21 to reflect your Text Domain.

  ```
  sed -i '/MY_DOMAIN/ s//CHANGE-THIS-TO-YOUR-TEXT-DOMAIN/' phpcs.xml
                         ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  ```

### Usage
The workflow is triggered on Pull request creation.
You'll see if the test is passing.
If it fails you'll see in your PR.

<img width="822" alt="image" src="https://github.com/ClassicPress/dev-workflows/assets/29772709/fd346ca6-39ed-442f-8b83-a7121d1e9a09">

You can check what is failing from the annotations in the "Files changed" tab.

<img width="1159" alt="image" src="https://github.com/ClassicPress/dev-workflows/assets/29772709/e5cdc13b-c854-4519-84cf-e6e13dd001d4">

Also in the "Actions" tab you'll find `cpcs` output.

<img width="959" alt="image" src="https://github.com/ClassicPress/dev-workflows/assets/29772709/57d7b4dc-3e35-41f7-9c9c-98efd5a8f908">
