# [Accessible Data and Code Site]()

## Site Theme (Hugo Blox)

Our site is made possible by [@GeorgeCushen](https://twitter.com/GeorgeCushen)'s [**Hugo Blox**](https://hugoblox.com/hugo-themes/) theme, [Hugo Research Group Theme](https://github.com/wowchemy/starter-hugo-research-group), previously known as Wowchemy and Hugo Academic.

### Automatically creating publication pages from BibTeX file

### Installing the [Hugo Academic CLI](https://github.com/GetRD/academic-file-converter)

```
# We use version 0.5.1 because of this issue:
# #https://github.com/GetRD/academic-file-converter/issues/107

pip3 install -U academic==0.5.1
```

### Automatically import citations from BibTeX file
```
# --compact Generate minimal markdown without comments or empty keys
# --normalize Normalize tags by converting them to lowercase and capitalizing the first letter (e.g. "sciEnCE" -> "Science")

academic import --bibtex content/bibliography/jupyter_site.bib --compact --overwrite --normalize
```

See [the documentation site](https://bootstrap.hugoblox.com/content/publications/#import-from-bibtex) for details.

## Importing blog posts from Jupyter Notebooks

```
academic import 'notebooks/*.ipynb' content/post/ --verbose
```