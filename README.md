# HackUTK Website

This website is built using [Hugo](http://gohugo.io), a static site generator. That means it contains template files in `layouts/` and content files in `content/`, and these two things get combined to generate the website's HTML.

## Development Information

To run the server locally, open up a terminal and run:

```
$ hugo server
```

Browse to `localhost:1313` on your web browser to see the site.

## /layouts

`layouts` contains snippets of HTML, for example here's `banner.html`:

```html
<section id="banner">
	<img class="logo" src="/images/logos/transparent_logo.png" />
	<p>The University of Tennessee's resident computer security organization.</p>
	<ul class="actions">
		<li><a href="https://goo.gl/forms/WBSZ9DwdjVdICwMf1" target="_blank" class="button">Join HackUTK</a></li>
		<li><a href="http://discord.hackutk.org/" target="_blank" class="button">Join our Discord</a></li>
		<li><a href="#sponsors" class="button">Our Sponsors</a></li>
	</ul>
	<ul class="actions">
		<li><a href="https://goo.gl/forms/KfmliuYvuiI49qtC3" class="button">Sign up for CTF</a></li>
	</ul>
</section>
```

Basically, in Hugo, you store these HTML snippets in `/layouts`, then whenever you want to use them, you call them like this in your HTML/Markdown files:

From `/content/_index.md`:

```html
{{ partial "banner.html" . }}
```

## Site Configuration Variables

If you want to use a variable in your HTML (doesn't work in Markdown), put it in `config.yaml` underneath `params:`. For example:

```yaml
params:
  ctf_signup_url: "https://goo.gl/forms/KfmliuYvuiI49qtC3"
```

Now, anytime you want to reference that variable in your HTML, call it like this:

```html
<li><a href="{{ .Site.Params.ctf_signup_url }}" class="button">Sign up for CTF</a></li>
```
