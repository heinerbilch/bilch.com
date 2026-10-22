# bilch.eu

Quellprojekt des Blogs [https://bilch.eu](https://bilch.eu) – gebaut mit [JBake](http://jbake.org).

## Struktur

```
src/jbake/content      Seiten und Blogposts (Markdown)
src/jbake/templates    Freemarker-Templates
src/jbake/assets       statische Dateien inkl. CNAME (bilch.eu)
src/jbake/jbake.properties   Konfiguration, site.host=https://bilch.eu
```

## Bauen

    cd src/jbake
    jbake -b .

Der Output landet in `src/jbake/output`.

## Publizieren

Den Inhalt des Output-Ordners in das Repository [heinerbilch/heinerbilch.github.io](https://github.com/heinerbilch/heinerbilch.github.io) (Branch `master`) kopieren und pushen. GitHub Pages deployt automatisch auf https://bilch.eu.
