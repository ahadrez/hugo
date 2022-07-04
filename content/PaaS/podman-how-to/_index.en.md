---
date: 2016-04-09T16:50:16+02:00
title: Podman
weight: 20
---

## Example Podman Cheat Sheet

On top of [Hugo global configuration](https://gohugo.io/overview/configuration/), **Hugo-theme-learn** lets you define the following parameters in your `config.toml` (here, values are default).


List local Images: 
`podman images`


Log in to a remote registry:
`podman login RegistryURL -u user -p password`

Pull an image from a remote registry:
`podman pull registry.redhat.io/rhel8/httpd-24`

Run a container with Podman:
`podman run -dti -p 80:80 -v /nfs:/var/www/html registry.redhat.io/rhel8/httpd-24`

List the running containers:
`podman ps`

Execute a command in a running container:
`podman exec -it containerid /bin/bash`

Display the logs of a container:
`podman logs containerid`


Save an image:
`podman save -o /path containerid`

Load an image:
`podman load -i /path`


Log out:
`podman logout`



Note that some of these parameters are explained in details in other sections of this documentation.



## Activate search

If not already present, add the follow lines in the same `config.toml` file.

```toml
[outputs]
home = [ "HTML", "RSS", "JSON"]
```

Learn theme uses the last improvement available in hugo version 20+ to generate a json index file ready to be consumed by lunr.js javascript search engine.

> Hugo generate lunrjs index.json at the root of public folder.
> When you build the site with `hugo server`, hugo generates it internally and of course it doesn’t show up in the filesystem

## Mermaid

The mermaid configuration parameters can also be set on a specific page. In this case, the global parameter would be overwritten by the local one.

> Example:
>
> Mermaid is globally disabled. By default it won't be loaded by any page.  
> On page "Architecture" you need a class diagram. You can set the mermaid parameters locally to only load mermaid on this page (not on the others).

You also can disable mermaid for specific pages while globally enabled.

## Home Button Configuration

If the `disableLandingPage` option is set to `false`, an Home button will appear
on the left menu. It is an alternative for clicking on the logo. To edit the
appearance, you will have to configure two parameters for the defined languages:

```toml
[Lanugages]
[Lanugages.en]
...
landingPageURL = "/en"
landingPageName = "<i class='fas fa-home'></i> Redirect to Home"
...
[Lanugages.fr]
...
landingPageURL = "/fr"
landingPageName = "<i class='fas fa-home'></i> Accueil"
...
```

If those params are not configured for a specific language, they will get their
default values:

```toml
landingPageURL = "/"
landingPageName = "<i class='fas fa-home'></i> Home"
```

The home button is going to looks like this:

![Default Home Button](/en/basics/configuration/images/home_button_defaults.jpg?width=100%)
