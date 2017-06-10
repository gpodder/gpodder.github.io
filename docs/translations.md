The translations of gPodder are managed in Git for now; previously we have been using Transifex, but since it can't integrate directly with Git anymore, it's easier for us to accept translations via pull requests.

### Applications

This is a selection of translation-editing software that you can use to open and edit the **.po** files that you download from Transifex:

-   [poedit](http://www.poedit.net/) (recommended)
-   [KBabel](http://kbabel.kde.org/)
-   [gtranslator](http://gtranslator.sourceforge.net/)
-   [Lokalize](http://userbase.kde.org/Lokalize/)
-   [Virtaal](http://translate.sourceforge.net/wiki/virtaal/)

### Missing plural header

Recent development of GPodder (v.2.1) includes Gettext plural forms.

PO headers needs to be checked for plural support for your language, e.g. for spanish:

`"Plural-Forms:` `nplurals=2;` `plural=(n` `!=` `1);\n"`

i.e. two forms, singular used for one only, should be included.

See [Gettext Manual](http://www.gnu.org/software/hello/manual/gettext/Plural-forms.html) and search for the plural formula related to your language.

New languages should take POT file and initialize it, e.g a spanish PO could be generated via:

`msginit` `--locale=es` `--input=gpodder.master.messages.pot`

Without this plural declaration no tabs for plural should be shown in Poedit or other applications, hence the need for it.

### Testing your translation

If the language you translate for is the language set in your system/session, all you need to do in your [Git checkout](run-from-git.md) is run `make` `messages` in your source folder (which will compile the translations to be usable by gettext), followed by `make` `test`, which will run gPodder from the source checkout folder.

### Testing translations with different system language

Thanks to Silvio Sisto for the initial idea of testing the language this way.

**Problem**:

-   You have your system running in, say, English and want to test your translation into, say, Spanish.

**Solution**:

-   Check if the command `sudo` `dpkg-reconfigure` `locales` already generates the files for `es_ES.UTF-8` (or similiar). If it does, you can skip the next step.
-   If `es_ES.UTF-8` has not been generated, install Spanish language support via `sudo` `aptitude` `install` `language-support-es`. This will install the whole language support for Spanish for all apps
-   In your [Git checkout](run-from-git.md) run:

    ```
    make messages
    export LANG=es_ES.UTF-8
    make test
    ```

-   Because you have entered `export` `LANG=es_ES.UTF-8` in an interactive shell, the rest of the system will not be affected, and closing down that session will also forget the language setting for this session.
-   If you don't need the Spanish translation files anymore, and because you have installed with aptitude, it will remove the dependencies when uninstalled: `sudo` `aptitude` `remove` `language-support-es`. This frees up the space taken by `langugage-support-es` + its dependencies (as of writing this guide, that's 66MB)
