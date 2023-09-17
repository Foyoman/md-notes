## leap-design-system
```sh
# release-v1.35.0
git pull
git merge formatting
git push
```

```sh
yarn release:patch
```

```sh
# staging
git pull
git merge release-v1.35.0
git push
```

- check chromatic

```sh
# master
git pull
git merge staging
git push
```

---
## nuxts: us, ca, uk
```sh
# staging
yarn add leap-design-system
```

- AccordionSplitFeature
- HeroLifestyleSplit
- HeroText
- LayoutSplitFeatureTextBox
- LayoutGridIconItem
- LayoutSplitFeatureInsert
- SplitFeature