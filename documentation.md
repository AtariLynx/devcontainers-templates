# Documentation for maintaining templates



## Publishing a new template version manually

Make sure you are logged in to GitHub Container Registry at ghcr.io.

```cmd
export CR_PAT="{your_github_personal_access_token}"
echo $CR_PAT | docker login ghcr.io -u {github_username} --password-stdin
```

The account needs to have `write:packages` (and implicitly `read:packages`) permissions.

Update the version of the new templates in the `devcontainer-template.json` file:

```json
{
    "id": "cc65",
    "version": "1.0.0", // Update according to semantic versioning
    // ...
```

Publication of all templates:

```cmd
devcontainer templates publish ./src -n atarilynx/devcontainers-templates
```

A specific template is published with:

```cmd
devcontainer templates publish ./src/cc65 -n atarilynx/devcontainers-templates
```
