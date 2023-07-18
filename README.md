# ClassicPress workflows for Plugins and Themes Developers

In this repository you'll find GitHub workflows that you can use in your projects.

_Remember to check Action permissions in your repository under Settings -> Actions -> General._

## Add ZIP to release

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
- From your repository go to "Releases"
- Draft a new release
- In the "Choose a tag" dropdown put version number. 
- It will prompt "+ Create new tag: x.x.x on publish". Click on it.
  
  <img width="363" alt="Create new tag" src="https://github.com/ClassicPress/dev-workflows/assets/29772709/2b46f344-a248-48a9-a67a-eb4a019b18b7">

- Enter a title and a description for your release.
- Click on publish.
- Leave the workflow time to run. You'll get the ZIP file attached to the release.
  
  <img width="943" alt="Release created" src="https://github.com/ClassicPress/dev-workflows/assets/29772709/07a11939-6ad3-42b1-9dc5-ed0106b5f40f">
