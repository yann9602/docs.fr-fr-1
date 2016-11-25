# <a name="using-the-cli-preview3-folder-and-sub-folders"></a>Utilisation du dossier cli-preview3 et des sous-dossiers

Ce dossier est le nœud de niveau supérieur qui correspond au dossier des outils, mais il contient des différences pour la version Release Preview 3 des outils .NET Core.

L’objectif de cette structure de dossiers parallèles distincte est de fournir un emplacement pour le contenu lié à la version Release Preview 3 qui peut être fusionné relativement facilement dans la structure principale lors d’un changement de version dans le site publié.

Le contenu sous ce nœud doit être un plus petit ensemble de documents qui représente les différences par rapport à la version Release LTS (Long Term Support) et à la version Release actuelle. 

## <a name="structure"></a>Structure

Deux cas justifient l’ajout de nouveau contenu pour cette version Release :

* Modifications apportées aux documents existants
    - Copiez le contenu existant dans un dossier parallèle sous cette structure. Apportez vos modifications et ajoutez le fichier modifié à la table des matières pour la version Release Preview 3.
* Nouveaux documents
    - Placez le nouveau document à l’emplacement approprié et ajoutez-le à la table des matières sous le nœud de la version Release Preview 3. 

Pour tous les fichiers de la version Release actuelle, ce qui suit doit être ajouté au début de la rubrique :

[!include[current release track](../includes/warning.md)]

Nous avons créé un extrait de code à inclure avec la syntaxe suivante :

```markdown
[!include[current release track](../../includes/warning.md)]
```

### <a name="link-instructions"></a>Instructions de liaison

Dans les deux cas, fournissez des liens depuis la version Release actuelle vers la page LTS (ou index.md parent) à des fins de navigation.
Envisagez de fournir des liens depuis la page LTS (ou index.md parent) vers la nouvelle page de contenu de la version Release actuelle.

## <a name="future-considerations"></a>Éléments futurs à prendre en considération

Notre objectif final est d’exposer différentes versions Release sous la forme de branches dans le [dépôt docs](https://github.com/dotnet/docs). En attendant, nous allons utiliser les différents dossiers de niveau supérieur pour chaque version Release actuelle. 

Le moment venu, nous pourrons fusionner chaque version Release actuelle dans le dossier [documents](../docs) principal, fusionner les nœuds de table des matières et procéder à des publications sous la forme d’un ensemble de documents séparé. Si nous sommes amenés à fusionner les modifications apportées à la version LTS d’un fichier et à la version Release actuelle d’un fichier, nous devrions pouvoir trouver ces modifications relativement facilement.


<!--HONumber=Nov16_HO3-->


