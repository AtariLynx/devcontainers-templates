# Atari Lynx dev container templates

This repository contains dev container templates to be used with Atari Lynx development based on cc65 and and tooling support.

## cc65 template
The template for cc65 use the sources from https://github.com/cc65/cc65/ to build the cc65 tool suite for 6502 development. There are Atari Lynx specific tools available as separate features. This template is usable for other 6502 based targets as well.

The image is based on the dev container Alpine base image. The Alpine version can be specified in the `imageVariant` template option. 

The template support choosing a specific cc65 version based on tags in the Git code repository. Versions 2.16 to 2.19 are available, as well `latest` for a build of the latest source code on `master` branch. Use the template option `cc65Version` to specify the version.

Apply the template to your Atari Lynx cc65 project by running:

```
devcontainer templates apply --template-id ghcr.io/atarilynx/templates/cc65:latest
```

or 

```
devcontainer templates apply --template-id ghcr.io/atarilynx/templates/cc65:latest
	--template-args '{ "imageVariant" : "3.21", "cc65Version" : "2.19" }'
```


## Available features

There are a number of features available for Atari Lynx development this [repository]https://github.com/AtariLynx/features.

You can add these features by specifying them in your `devcontainer.json` file.

```json
	"features": {
		"ghcr.io/atarilynx/devcontainers/make_lnx:latest": {},
		"ghcr.io/atarilynx/devcontainers/sprpck:latest": {}
	},
```

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
devcontainer templates publish ./src -n atarilynx/templates
```

A specific template is published with:

```cmd
devcontainer templates publish ./src/cc65 -n atarilynx/templates
```
