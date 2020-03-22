# covid-19-transmission-graphic

Translation automation for the fantastic GIF made by @siouxsiew, @xtotl and @thespinofftv.

As the original GIF is in english only, this repo helps to make rapid translations of it.

**People have to change their behaviour now** and I believe this GIF is a great explainer of what we have to do as communities.

## Original
![](https://thespinoff.co.nz/wp-content/uploads/2020/03/Covid-19-Transmission-graphic-01.gif)

## Released Translations

[**See the Releases**](https://gitlab.com/msutter/covid-19-transmission-graphic/-/releases)

## Contribute with a traduction of your own language

### Find the iso code of your language

* https://www.wordfast.net/?go=languages
* https://www.andiamo.co.uk/resources/iso-language-codes/

### Online with Gitlab in a browser

You can do everything in a browser like described in this video made for the first translation project (https://gitlab.com/msutter/covid-19-curves-graphic-social)

The procedure is the same as for this project.

* https://www.youtube.com/watch?v=-ThkrkFLY8Q

Note: please enable 'Allow commits from members who can merge to the target branch' when you create the merge request.

### Local on your workstation

If you have some git knowledges, here are the steps with a local dev environment.

For each language, there is a folder under the `languages` directory

1. First fork this repo and create a new branch named like the language iso code.

We make a translation for the romansh language here (rm-ch) as example. By the way romansh is the fourth official language in Switzerland, after german, french and italian.

```bash
git checkout -b rm-ch
```

2. For a new language, create a new folder and name it with the iso language code. Same name as the branch you've created in step 1.

```bash
mkdir languages/rm-ch
```

3. Copy the test.yaml file from an other language and translate the texts in the target language.

```bash
cp languages/en-ch/text.yaml languages/rm-ch
```

4. Commit and push your changes

```bash
git add .
git commit -m "Add translation for the Romansh language (rm-ch)"
git push --set-upstream origin rm-ch
```

5. Go to [Gitlab.com](https://gitlab.com/msutter/covid-19-transmission-graphic/-/branches) and open a merge request for your changes.

Once a merge request is started, a pipeline will build a version of your new GIF. You can see it in the artifacts of the `build_gif` pipeline job. (Job artifacts -> browse -> releases

6. Notify me when you're happy with your work and give me your twitter account to include it in the final release.

I would love to see a lot of translations getting in !

## Local usage

You can also generate GIF's from your workstation

From with the root of this repo run:

```
language=fr-ch
docker run --rm -ti -v $(pwd)/templates:/templates -v $(pwd)/languages:/languages -v $(pwd)/releases:/releases registry.gitlab.com/msutter/gimp-gif-translate /translate.sh -f templates/covid-19-transmission-graphic.xcf -p /translate-gif.py -l $language
```

This will generate a new GIF in the `releases` folder.

Note: You can also use the -a flag instead of -l to generate all releases.
