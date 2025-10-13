# Préparer votre dépôt

## Intention

Avant de vous lancer dans le développement, il est important de finaliser la configuration de votre dépôt. C'est l'intention de ce laboratoire.

## Objectif

* [ ] Invitez votre enseignant à collaborer sur votre dépôt

{% embed url="https://docs.github.com/en/account-and-profile/how-tos/setting-up-and-managing-your-personal-account-on-github/managing-access-to-your-personal-repositories/inviting-collaborators-to-a-personal-repository" %}

{% hint style="warning" %}
Ne travaillez pas sur votre branche "main". Cette dernière servira de modèle pour la suite du projet.
{% endhint %}

* [ ] Ouvrer une nouvelle branche "develop" en utilisant la commande suivante:

```git
git flow init
```

* [ ] Laissez tous les paramètres par défaut et validez !

```git
Which branch should be used for bringing forth production releases?
   - main
Branch name for production releases: [main] 
Branch name for "next release" development: [develop] 

How to name your supporting branch prefixes?
Feature branches? [feature/] 
Bugfix branches? [bugfix/] 
Release branches? [release/] 
Hotfix branches? [hotfix/] 
Support branches? [support/] 
Version tag prefix? [] 
Hooks and filters directory? [.../.git/hooks] 
```

* [ ] Vérifiez que vous êtes bien sur la branche "develop"

```
git branch
```

```
*  develop                                                                                           
  main
```

* [ ] Publiez la branche "develop" sur votre dépôt

```
git push --set-upstream origin develop
```
