---
title: "Documentation de référence sur project.json"
description: "Documentation de référence sur project.json"
keywords: .NET, .NET Core, project.json
author: aL3891
ms.author: mairaw
ms.date: 09/30/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 3aef32bd-ee2a-4e24-80f8-a2b615e0336d
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: ce3dbad938c01fd0f9d79cefb29884be986b8e1f

---

# <a name="projectjson-reference"></a>Documentation de référence sur project.json

Le fichier project.json est utilisé dans les projets .NET Core pour définir des métadonnées de projet, des informations de compilation et des dépendances. Cette rubrique répertorie toutes les propriétés que vous pouvez définir dans votre fichier project.json.

> [!NOTE]
> Dans une prochaine version, les outils .NET Core vont passer de projets basés sur project.json à des projets basés sur MSBuild. Il est toujours recommandé d’utiliser les fichiers project.json pour les nouveaux projets .NET Core. Vous aurez l’occasion de convertir votre projet en projet MSBuild lorsque les outils seront sortis.
>
> Pour plus d’informations, consultez [Changes to project.json](https://blogs.msdn.microsoft.com/dotnet/2016/05/23/changes-to-project-json/) sur le blog .NET, ainsi que la rubrique [Création de projets .NET Core à l’aide de MSBuild](../tutorials/target-dotnetcore-with-msbuild.md).

## <a name="overview"></a>Vue d'ensemble

```
{
    "name": String,
    "version": String,
    "description": String,
    "copyright": String,
    "title": String,
    "entryPoint": String,
    "testRunner": String,
    "authors": String[],
    "language": String,
    "embedInteropTypes": Boolean,
    "preprocess": String or String[],
    "shared": String or String[],
    "dependencies": Object {
        version: String,
        type: String,
        target: String,
        include: String,
        exclude: String,
        suppressParent: String
    },
    "tools": Object,
    "scripts": Object,
    "buildOptions": Object {
        "define": String[],
        "nowarn": String[],
        "additionalArguments": String[],
        "warningsAsErrors": Boolean,
        "allowUnsafe": Boolean,
        "emitEntryPoint": Boolean,
        "optimize": Boolean,
        "platform": String,
        "languageVersion": String,
        "keyFile": String,
        "delaySign": Boolean,
        "publicSign": Boolean,
        "debugType": String,
        "xmlDoc": Boolean,
        "preserveCompilationContext": Boolean,
        "outputName": String,
        "compilerName": String,
        "compile": Object {
            "include": String or String[],
            "exclude": String or String[],
            "includeFiles": String or String[],
            "excludeFiles": String or String[],
            "builtIns": Object,
            "mappings": Object
        },
        "embed": Object {
            "include": String or String[],
            "exclude": String or String[],
            "includeFiles": String or String[],
            "excludeFiles": String or String[],
            "builtIns": Object,
            "mappings": Object
        },
        "copyToOutput": Object {
            "include": String or String[],
            "exclude": String or String[],
            "includeFiles": String or String[],
            "excludeFiles": String or String[],
            "builtIns": Object,
            "mappings": Object
        }
    },
    "publishOptions": Object {
        "include": String or String[],
        "exclude": String or String[],
        "includeFiles": String or String[],
        "excludeFiles": String or String[],
        "builtIns": Object,
        "mappings": Object
    },
    "runtimeOptions": Object {
        "configProperties": Object {
            "System.GC.Server": Boolean,
            "System.GC.Concurrent": Boolean,
            "System.GC.RetainVM": Boolean,
            "System.Threading.ThreadPool.MinThreads": Integer,
            "System.Threading.ThreadPool.MaxThreads": Integer
        },
        "framework": Object {
            "name": String,
            "version": String,
        },
        "applyPatches": Boolean
    },
    "packOptions": Object {
        "summary": String,
        "tags": String[],
        "owners": String[],
        "releaseNotes": String,
        "iconUrl": String,
        "projectUrl": String,
        "licenseUrl": String,
        "requireLicenseAcceptance": Boolean,
        "repository": Object {
            "type": String,
            "url": String
        },
        "files": Object {
            "include": String or String[],
            "exclude": String or String[],
            "includeFiles": String or String[],
            "excludeFiles": String or String[],
            "builtIns": Object,
            "mappings": Object
        }
    },
    "analyzerOptions": Object {
        "languageId": String
    },
    "configurations": Object,
    "frameworks": Object {
        "dependencies": Object {
            version: String,
            type: String,
            target: String,
            include: String,
            exclude: String,
            suppressParent: String
        },        
        "frameworkAssemblies": Object,
        "wrappedProject": String,
        "bin": Object {
            assembly: String
        }
    },
    "runtimes": Object,
    "userSecretsId": String
}
```

## <a name="name"></a>name
Type : chaîne

Nom du projet, utilisé pour le nom de l’assembly, ainsi que le nom du package. Le nom du dossier de niveau supérieur est utilisé si cette propriété n’est pas spécifiée.

Exemple :

```json
{
    "name": "MyLibrary"
}
```

## <a name="version"></a>version
Type : chaîne

La version [Semver](http://semver.org/spec/v1.0.0.html) du projet, également utilisée pour le package NuGet.

Exemple :

```json
{
    "version": "1.0.0-*"
}
```

## <a name="description"></a>description
Type : chaîne

Description détaillée du projet. Utilisé dans les propriétés des assemblys.

Exemple :

```json
{
    "description": "This is my library and it's really great!"
}
```

## <a name="copyright"></a>copyright
Type : chaîne

Informations de copyright du projet. Utilisé dans les propriétés des assemblys.

Exemple :

```json
{
    "copyright": "Fabrikam 2016"
}
```

## <a name="title"></a>titre
Type : chaîne

Nom convivial du projet. Peut contenir des espaces et des caractères spéciaux non autorisés si vous utilisez la propriété `name`. Utilisé dans les propriétés des assemblys.

Exemple :

```json
{
    "title": "My Library"
}
```

## <a name="entrypoint"></a>entryPoint
Type : chaîne

Méthode de point d’entrée pour le projet. `Main` par défaut.

Par exemple :

```json
{
    "entryPoint": "ADifferentMethod"
}
```
    
## <a name="testrunner"></a>testRunner
Type : chaîne

Nom du Test Runner (par exemple, [NUnit](http://nunit.org/) ou [xUnit](http://xunit.github.io/)) à utiliser avec ce projet. En définissant cette chaîne, vous marquez également le projet comme un projet de test.

Exemple :

```json
{
    "testRunner": "NUnit"
}
```

## <a name="authors"></a>authors
Type : String[]

Tableau de chaînes avec le nom des auteurs du projet.

Exemple :

```json
{
    "authors": ["Anne", "Bob"]
}
```

## <a name="language"></a>language
Type : chaîne

Langue utilisée pour ce projet. Correspond à l’argument du compilateur « neutral-language ».

Exemple :

```json
{
    "language": "en-US"
}
```

## <a name="embedinteroptypes"></a>embedInteropTypes
Type : booléen

`true` pour incorporer les types COM Interop dans l’assembly ; sinon, `false`. 

Par exemple :

```json
{
    "embedInteropTypes": true
}
```

## <a name="preprocess"></a>preprocess
Type : String ou String[] avec modèle de globbing

Spécifie les fichiers à inclure dans le prétraitement.

Exemple :

```json
{
    "preprocess": "compiler/preprocess/**/*.cs"
}
```

## <a name="shared"></a>partagés
Type : String ou String[] avec modèle de globbing

Spécifie les fichiers à partager. Utilisé pour l’exportation de la bibliothèque.

Exemple :

```json
{
    "shared": "shared/**/*.cs"
}
```

## <a name="dependencies"></a>dépendances
Type : object

Objet qui définit les dépendances de package du projet. Chaque clé de cet objet correspond au nom d’un package, et chaque valeur contient des informations de version.
Pour plus d’informations, consultez l’article sur la [résolution des dépendances](https://docs.nuget.org/ndocs/consume-packages/dependency-resolution#dependency-resolution-in-nuget-3-x) sur le site de la documentation NuGet.

Exemple :

```json
    "dependencies": {
        "System.Reflection.Metadata": "1.3.0",
        "Microsoft.Extensions.JsonParser.Sources": {
          "type": "build",
          "version": "1.0.0-rc2-20221"
        },
        "Microsoft.Extensions.HashCodeCombiner.Sources": {
          "type": "build",
          "version": "1.1.0-alpha1-21456"
        },
        "Microsoft.Extensions.DependencyModel": "1.0.0-*"
    }
```

### <a name="version"></a>version
Type : chaîne

Spécifie la version ou la plage de versions de la dépendance. Utilisez le caractère générique \* pour spécifier une [version de dépendance flottante](https://docs.nuget.org/ndocs/consume-packages/dependency-resolution#floating-versions).

Exemple :

```json
"dependencies": { 
    "Newtonsoft.Json": { 
        "version": "9.0.1" 
    }
}
```

### <a name="type"></a>type
Type : chaîne

Spécifie le type de la dépendance. Peut avoir l’une des valeurs suivantes : `default`, `build` ou `platform`. La valeur par défaut est `default`.

`build` est connu comme une dépendance de développement et sert uniquement au moment de la génération. Cela signifie que le package ne doit pas être publié ni ajouté en tant que dépendance dans le fichier de sortie `.nupkg`. Son effet est le même que si vous définissiez [supressParent](#supressparent) sur `all`.

`platform` référence le SDK partagé. Pour plus d’informations, consultez la section « Déploiement d’un déploiement dépendant du framework avec des dépendances tierces » dans la rubrique [Déploiement d’applications .NET Core](../deploying/index.md).

Par exemple :

```json
 "dependencies": {
   "Microsoft.NETCore.App": {
     "type": "platform",
     "version": "1.0.0"
   }
 }
```

### <a name="target"></a>target
Type : chaîne

Restreint la dépendance de sorte qu’elle ne corresponde qu’à un `project` ou un `package`.

### <a name="include"></a>include
Type : chaîne

Inclut des parties des packages de dépendances. Il peut utiliser un ou plusieurs des indicateurs suivants : `all`, `runtime`, `compile`, `build`, `contentFiles`, `native`, `analyzers` ou `none`.
Pour définir plusieurs indicateurs, utilisez une liste délimitée par des virgules.
Pour plus d’informations, consultez la spécification concernant la [gestion des ressources des packages de dépendances](https://github.com/NuGet/Home/wiki/%5BSpec%5D-Managing-dependency-package-assets) dans le dépôt NuGet.

Exemple :

```json
{
  "dependencies": {
    "packageA": {
      "version": "1.0.0",
      "include": "runtime"
    }
  }
}
```

### <a name="exclude"></a>exclude
Type : chaîne

Exclut des parties des packages de dépendances. Il peut s’agir d’un ou de plusieurs des indicateurs suivants : `all`, `runtime`, `compile`, `build`, `contentFiles`, `native`, `analyzers` ou `none`.
Pour définir plusieurs indicateurs, utilisez une liste délimitée par des virgules.
Pour plus d’informations, consultez la spécification concernant la [gestion des ressources des packages de dépendances](https://github.com/NuGet/Home/wiki/%5BSpec%5D-Managing-dependency-package-assets) dans le dépôt NuGet.

Exemple :

```json
{
  "dependencies": {
    "packageA": {
      "version": "1.0.0",
      "exclude": "contentFiles"
    }
  }
}
```

### <a name="supressparent"></a>supressParent
Type : chaîne

Définit des exclusions supplémentaires pour les consommateurs du projet. Il peut s’agir de l’un des indicateurs suivants : `all`, `runtime`, `compile`, `build`, `contentFiles`, `native`, `analyzers` ou `none`.
Pour plus d’informations, consultez la spécification concernant la [gestion des ressources des packages de dépendances](https://github.com/NuGet/Home/wiki/%5BSpec%5D-Managing-dependency-package-assets) dans le dépôt NuGet.

```json
{
  "dependencies": {
    "packageA": {
      "version": "1.0.0",
      "suppressParent": "compile"
    }
  }
}
```

## <a name="tools"></a>outils
Type : object

Objet qui définit les dépendances de packages qui sont utilisées en tant qu’outils pour le projet actuel, et non en tant que références. Les packages définis ici sont disponibles dans les scripts qui s’exécutent pendant le processus de génération. Toutefois, ils ne sont pas accessibles au code du projet. Les outils peuvent inclure des générateurs de code ou des outils post-génération qui effectuent des tâches liées à la compression.

Exemple :

```json
{
    "tools": {
    "MyObfuscator": "1.2.4"
    }
}
```

## <a name="scripts"></a>scripts
Type : object

Objet qui définit les scripts exécutés pendant le processus de génération. Chaque clé de cet objet identifie l’emplacement de la build où le script doit être exécuté. Chaque valeur est soit une chaîne contenant le script à exécuter, soit un tableau de chaînes contenant les scripts classés dans l’ordre de leur exécution.
Les événements pris en charge sont :
* precompile
* postcompile
* prepublish
* postpublish

Exemple :

```json
{
    "scripts": {
        "precompile": "generateCode.cmd",
        "postcompile": [ "obfuscate.cmd", "removeTempFiles.cmd" ]
    }
}
```

## <a name="buildoptions"></a>buildOptions
Type : object

Objet dont les propriétés contrôlent divers aspects de la compilation. Les propriétés valides sont répertoriées ci-dessous. Peut également être spécifié par framework cible, comme décrit dans la [section concernant les frameworks](#frameworks).

Exemple :

```json
    "buildOptions": {
      "allowUnsafe": true,
      "emitEntryPoint": true
    }
```

### <a name="define"></a>define
Type : String[]

Liste de définitions, telles que « DEBUG » ou « TRACE », pouvant être utilisées dans la compilation conditionnelle du code.

Exemple :

```json
{
    "buildOptions": {
        "define": ["TEST", "OTHERCONDITION"]
    }
}
```

### <a name="nowarn"></a>nowarn
Type : String[]

Liste des avertissements à ignorer.

Par exemple :

```json
{
    "buildOptions": {
        "nowarn": ["CS0168", "CS0219"]
    }
}
```

Il ignore les avertissements `The variable 'var' is assigned but its value is never used` et `The variable 'var' is assigned but its value is never used`

### <a name="additionalarguments"></a>additionalArguments
Type : String[]

Liste des arguments supplémentaires qui sont passés au compilateur.

Exemple :

```json
{
    "buildOptions": {
        "additionalArguments": ["/parallel", "/nostdlib"]
    }
}
```

### <a name="warningsaserrors"></a>warningsAsErrors
Type : booléen

`true` pour traiter les avertissements comme des erreurs ; sinon, `false`. La valeur par défaut est `false`.

Exemple :

```json
{
    "buildOptions": {
        "warningsAsErrors": true
    }
}
```

### <a name="allowunsafe"></a>allowUnsafe
Type : booléen

`true` pour autoriser le code unsafe dans ce projet ; sinon, `false`. La valeur par défaut est `false`.

Exemple :

```json
{
    "buildOptions": {
        "allowUnsafe": true
    }
}
```

### <a name="emitentrypoint"></a>emitEntryPoint
Type : booléen

`true` pour créer un fichier exécutable ; `false` pour générer une bibliothèque. La valeur par défaut est `false`.

Exemple :

```json
{
    "buildOptions": {
        "emitEntryPoint": true
    }
}
```

### <a name="optimize"></a>optimize
Type : booléen

`true` pour permettre au compilateur d’optimiser le code du projet ; sinon, `false`. La valeur par défaut est `false`.

Exemple :

```json
{
    "buildOptions": {
        "optimize": true
    }
}
```

### <a name="platform"></a>platform
Type : chaîne

Nom de la plateforme cible, par exemple AnyCpu, x86 ou x64.

Exemple :

```json
{
    "buildOptions": {
        "platform": "x64"
    }
}
```

### <a name="languageversion"></a>languageVersion
Type : chaîne

Version du langage utilisé par le compilateur : ISO-1, ISO-2, 3, 4, 5, 6 ou Par défaut.

Exemple :

```json
{
    "buildOptions": {
        "languageVersion": "5"
    }
}
```

### <a name="keyfile"></a>keyFile
Type : chaîne

Chemin du fichier de clé utilisé pour la signature de cet assembly.

Exemple :

```json
{
    "buildOptions": {
        "keyFile": "../keyfile.snk"
    }
}
```

### <a name="delaysign"></a>delaySign
Type : booléen

`true` pour différer la signature ; sinon, `false`. La valeur par défaut est `false`.

Exemple :

```json
{
    "buildOptions": {
        "delaySign": true
    }
}
```

### <a name="publicsign"></a>publicSign
Type : booléen

`true` pour activer la signature de l’assembly obtenu ; sinon, `false`. La valeur par défaut est `false`.

Exemple :

```json
{
    "buildOptions": {
        "publicSign": true
    }
}
```

### <a name="debugtype"></a>debugType
Type : chaîne

Indique le type du fichier de symboles (fichier PDB) à générer. Les options sont « portable » (pour les projets .NET Core) ou « full » (pour les fichiers PDB Windows traditionnels).

Exemple :

```json
{
    "buildOptions": {
        "debugType": "portable"
    }
}
```

### <a name="xmldoc"></a>xmlDoc
Type : booléen

`true` pour générer la documentation XML à partir des commentaires à trois barres obliques dans le code source ; sinon, `false`. La valeur par défaut est `false`.

Exemple :

```json
{
    "buildOptions": {
        "xmlDoc": true
    }
}
```

### <a name="preservecompilationcontext"></a>preserveCompilationContext
Type : booléen

`true` pour conserver les assemblys de référence et autres données de contexte afin de permettre la compilation du runtime ; sinon, `false`. La valeur par défaut est `false`.

Exemple :

```json
{
    "buildOptions": {
        "preserveCompilationContext": true
    }
}
```

### <a name="outputname"></a>outputName
Type : chaîne

Modifie le nom du fichier de sortie. 

Exemple :

```json
{
    "buildOptions": {
        "outputName": "MyApp"
    }
}
```

### <a name="compilername"></a>compilerName
Type : chaîne

Nom du compilateur utilisé pour ce projet. `csc` par défaut. Actuellement, `csc` (compilateur C#) et `fsc` (compilateur F#) sont pris en charge.
 
Exemple :

```json
{
    "compilerName": "fsc"
}
```
    
### <a name="compile"></a>compile
Type : object

Objet qui contient les propriétés de configuration de la compilation.

#### <a name="include"></a>include
Type : String ou String[] avec modèle de globbing.

Spécifie les fichiers à inclure dans la génération. Les modèles sont inclus dans le dossier du projet. Par défaut, aucun.

Exemple :

```json
{
    "include":["wwwroot", "Views"]
}
```

#### <a name="exclude"></a>exclude
Type : String ou String[] avec modèle de globbing.

Spécifie les fichiers à exclure de la génération. Les modèles d’exclusion ont une priorité plus élevée que les modèles d’inclusion. Par conséquent, un fichier trouvé dans les deux sera exclu. Les modèles sont inclus dans le dossier du projet. Par défaut, aucun.

Exemple :

```json
{
    "exclude": ["bin/**", "obj/**"]
}
```

#### <a name="includefiles"></a>includeFiles

Type : String ou String[] avec modèle de globbing.

Liste de chemins de fichiers à inclure. Les chemins sont inclus dans le dossier du projet. Cette liste a une priorité plus élevée que les modèles de globbing include et exclude. Par conséquent, un fichier listé ici et dans le modèle de globbing exclude sera quand même inclus. Par défaut, aucun.

Exemple :

```json
{
    "includeFiles": []
}
```

#### <a name="excludefiles"></a>excludeFiles

Type : String ou String[] avec modèle de globbing.

Liste des chemins de fichiers à exclure. Les chemins sont inclus dans le dossier du projet. Cette liste a une priorité plus élevée que les modèles de globbing et que les chemins include. Par conséquent, un fichier trouvé dans les deux sera exclu. Par défaut, aucun.

Exemple :

```json
{
    "excludeFiles":[],
}
```

#### <a name="builtins"></a>builtIns

Type : object

Valeurs par défaut fournies par le système. Il peut avoir des modèles de globbing `include` et `exclude` fusionnés avec les valeurs correspondantes des propriétés `include` et `exclude`.

Exemple :

```json
{
    "builtIns":{}
}
```

#### <a name="mappings"></a>mappages
Type : object

Les clés de l’objet représentent les chemins de destination dans la disposition de la sortie.

Les valeurs sont soit une chaîne, soit un objet représentant le chemin source des fichiers à inclure.  La représentation de l’objet peut avoir ses propres sections `include`, `exclude`, `includeFiles` et `excludeFiles`.

Exemple de chaîne :

```json
{
    "mappings": {
        "dest/path": "./src/path"
    }
}
```

Exemple d’objet :

```json
{
    "mappings": {
        "dest/path":{
            "include":"./src/path"
        }
    }
}
```

### <a name="embed"></a>embed
Type : object

Objet qui contient les propriétés de configuration de la compilation.

#### <a name="include"></a>include
Type : String ou String[] avec modèle de globbing.

```json
{
    "include":["wwwroot", "Views"]
}
```

#### <a name="exclude"></a>exclude
Type : String ou String[] avec modèle de globbing.

Spécifie les fichiers à exclure de la génération.

Exemple :

```json
{
    "exclude": ["bin/**", "obj/**"]
}
```

#### <a name="includefiles"></a>includeFiles

Type : String ou String[] avec modèle de globbing.

```json
{
    "includeFiles":[],
}
```

#### <a name="excludefiles"></a>excludeFiles

Type : String ou String[] avec modèle de globbing.

```json
{
    "excludeFiles":[],
}
```

#### <a name="builtins"></a>builtIns
Type : object

```json
{
    "builtIns":{}
}
```

#### <a name="mappings"></a>mappages
Type : object

Les clés de l’objet représentent les chemins de destination dans la disposition de la sortie.

Les valeurs sont soit une chaîne, soit un objet représentant le chemin source des fichiers à inclure.  La représentation de l’objet peut avoir ses propres sections `include`, `exclude`, `includeFiles` et `excludeFiles`.

Exemple de chaîne :

```json
{
    "mappings": {
        "dest/path": "./src/path"
    }
}
```

Exemple d’objet :

```json
{
    "mappings": {
        "dest/path":{
            "include":"./src/path"
        }
    }
}
```

### <a name="copytooutput"></a>copyToOutput
Type : object

Objet qui contient les propriétés de configuration de la compilation.

#### <a name="include"></a>include
Type : String ou String[] avec modèle de globbing.

```json
{
    "include":["wwwroot", "Views"]
}
```

#### <a name="exclude"></a>exclude
Type : String ou String[] avec modèle de globbing.

Spécifie les fichiers à exclure de la génération.

Exemple :

```json
{
    "exclude": ["bin/**", "obj/**"]
}
```

#### <a name="includefiles"></a>includeFiles

Type : String ou String[] avec modèle de globbing.

```json
{
    "includeFiles":[],
}
```

#### <a name="excludefiles"></a>excludeFiles

Type : String ou String[] avec modèle de globbing.

```json
{
    "excludeFiles":[],
}
```

#### <a name="builtins"></a>builtIns
Type : object

```json
{
    "builtIns":{}
}
```

#### <a name="mappings"></a>mappages
Type : object

Les clés de l’objet représentent les chemins de destination dans la disposition de la sortie.

Les valeurs sont soit une chaîne, soit un objet représentant le chemin source des fichiers à inclure.  La représentation de l’objet peut avoir ses propres sections `include`, `exclude`, `includeFiles` et `excludeFiles`.

Exemple de chaîne :

```json
{
    "mappings": {
        "dest/path": "./src/path"
    }
}
```

Exemple d’objet :

```json
{
    "mappings": {
        "dest/path":{
            "include":"./src/path"
        }
    }
}
```

## <a name="publishoptions"></a>publishOptions
Type : object

Objet qui contient les propriétés de configuration de la compilation.

### <a name="include"></a>include
Type : String ou String[] avec modèle de globbing.

```json
{
    "include":["wwwroot", "Views"]
}
```

### <a name="exclude"></a>exclude
Type : String ou String[] avec modèle de globbing.

Spécifie les fichiers à exclure de la génération.

Exemple :

```json
{
    "exclude": ["bin/**", "obj/**"]
}
```

### <a name="includefiles"></a>includeFiles

Type : String ou String[] avec modèle de globbing.

```json
{
    "includeFiles":[],
}
```

### <a name="excludefiles"></a>excludeFiles

Type : String ou String[] avec modèle de globbing.

```json
{
    "excludeFiles":[],
}
```

### <a name="builtins"></a>builtIns
Type : object

```json
{
    "builtIns":{}
}
```

### <a name="mappings"></a>mappages
Type : object

Les clés de l’objet représentent les chemins de destination dans la disposition de la sortie.

Les valeurs sont soit une chaîne, soit un objet représentant le chemin source des fichiers à inclure.  La représentation de l’objet peut avoir ses propres sections `include`, `exclude`, `includeFiles` et `excludeFiles`.

Exemple de chaîne :

```json
{
    "mappings": {
        "dest/file": "./src/file",
        "dest/folder/": "./src/folder/**/*"
    }
}
```

Exemple d’objet :

```json
{
    "mappings": {
        "dest/file":{
            "include":"./src/file"
        },
        "dest/folder/":{
            "include":"./src/folder/**/*"
        }
    }
}
```

## <a name="runtimeoptions"></a>runtimeOptions
Type : object

Spécifie les paramètres à fournir au runtime pendant l’initialisation.

### <a name="configproperties"></a>configProperties
Type : object

Contient les propriétés de configuration du runtime et du framework.

#### <a name="systemgcserver"></a>System.GC.Server
Type : booléen

`true` pour activer le garbage collection du serveur ; sinon, `false`. La valeur par défaut est `false`.

Exemple :

```json
{
    "runtimeOptions": {
        "configProperties": {
            "System.GC.Server": true
        }
    }
}
```

#### <a name="systemgcconcurrent"></a>System.GC.Concurrent
Type : booléen

`true` pour activer le garbage collection simultané ; sinon, `false`. La valeur par défaut est `false`.

Exemple :

```json
{
    "runtimeOptions": {
        "configProperties": {
            "System.GC.Concurrent": true
        }
    }
}
```

#### <a name="systemgcretainvm"></a>System.GC.RetainVM
Type : booléen

`true` pour placer les segments qui doivent être supprimés dans une liste d’attente pour une utilisation ultérieure, au lieu de les réintégrer au système d’exploitation ; sinon, `false`.
La valeur par défaut est `false`.

Exemple :

```json
{
    "runtimeOptions": {
        "configProperties": {
            "System.GC.RetainVM": true
        }
    }
}
```

#### <a name="systemthreadingthreadpoolminthreads"></a>System.Threading.ThreadPool.MinThreads
Type : entier

Remplace le nombre minimal de threads pour le pool de travail ThreadPool.

```json
{
    "runtimeOptions": {
        "configProperties": {
            "System.Threading.ThreadPool.MinThreads": 4
        }
    }
}
```

#### <a name="systemthreadingthreadpoolmaxthreads"></a>System.Threading.ThreadPool.MaxThreads
Type : entier

Remplace le nombre maximal de threads pour le pool de travail ThreadPool.

```json
{
    "runtimeOptions": {
        "configProperties": {
            "System.Threading.ThreadPool.MaxThreads": 25
        }
    }
}
```

### <a name="framework"></a>framework
Type : object

Contient les propriétés du framework partagé à utiliser lors de l’activation de l’application. La présence de cette section indique que l’application est une application portable conçue pour utiliser un framework redistribuable partagé.

#### <a name="name"></a>name
Type : chaîne

Nom du framework partagé.

```json
{
    "runtimeOptions": {
        "framework": {
            "name": "Microsoft.DotNetCore"
        }
    }
}
```

#### <a name="version"></a>version
Type : chaîne

Version du framework partagé.

```json
{
    "runtimeOptions": {
        "framework": {
            "version": "1.0.1"
        }
    }
}
```

### <a name="applypatches"></a>applyPatches
Type : booléen

`true` pour utiliser le framework ayant la même version ou une version ultérieure dont la seule différence se situe dans le champ de correctif `SemVer`. `false` pour que l’hôte utilise exactement la même version de framework. La valeur par défaut est `true`.

```json
{
    "runtimeOptions": {
        "applyPatches": false
    }
}
```

## <a name="packoptions"></a>packOptions
Type : object

Définit les options relatives à l’empaquetage de la sortie du projet dans un package NuGet.

### <a name="summary"></a>résumé
Type : chaîne

Description brève du projet.

Exemple :

```json
{
    "packOptions": {
        "summary": "This is my library."
    }
}
```

### <a name="tags"></a>étiquettes
Type : String[]

Un tableau de chaînes contenant les balises du projet, utilisé pour la recherche dans NuGet.

Exemple :

```json
{
    "packOptions": {
        "tags": ["hyperscale", "cats"]
    }
}
```

### <a name="owners"></a>owners
Type : String[]

Tableau de chaînes contenant le nom des propriétaires du projet.

Exemple :

```json
{
    "packOptions": {
        "owners": ["Fabrikam", "Microsoft"]
    }
}
```

### <a name="releasenotes"></a>releaseNotes
Type : chaîne

Notes de publication du projet.

Exemple :

```json
{
    "packOptions": {
        "releaseNotes": "Initial version, implemented flimflams."
    }
}
```

### <a name="iconurl"></a>iconUrl
Type : chaîne

URL d’une icône qui sera utilisée à plusieurs emplacements, tels que l’Explorateur de package.

Exemple :

```json
{
    "packOptions": {
        "iconUrl": "http://www.mylibrary.gov/favicon.ico"
    }
}
```

### <a name="projecturl"></a>projectUrl
Type : chaîne

URL de la page d’accueil du projet.

Exemple :

```json
{
    "packOptions": {
        "projectUrl": "http://www.mylibrary.gov"
    }
}
```

### <a name="licenseurl"></a>licenseUrl
Type : chaîne

URL de la licence utilisée par le projet.

Exemple :

```json
{
    "packOptions": {
        "licenseUrl": "http://www.mylibrary.gov/licence"
    }
}
```

### <a name="requirelicenseacceptance"></a>requireLicenseAcceptance
Type : booléen

`true` pour que l’invite accepte la licence de package pendant l’installation du package à afficher ; sinon, `false`. Utilisé uniquement pour les packages NuGet ; ignoré pour les autres utilisations. La valeur par défaut est `false`.

Exemple :

```json
{
    "packOptions": {
        "requireLicenseAcceptance": true
    }
}
```
   
### <a name="repository"></a>dépôt
Type : object

Contient des informations sur le dépôt où se trouve le projet.

#### <a name="type"></a>type
Type : chaîne

Type du dépôt. La valeur par défaut est « git ».

Exemple :

```json
{
    "packOptions": {
        "repository": {
            "type": "git"
        }
    }
}
```

#### <a name="url"></a>url
Type : chaîne

URL du dépôt où se trouve le projet.

Exemple :

```json
{
    "packOptions": {
        "repository": {
            "url": "http://github.com/dotnet/corefx"
        }
    }
}
```

### <a name="files"></a>fichiers 
Type : object

#### <a name="include"></a>include
Type : String ou String[] avec modèle de globbing.

```json
{
    "include":["wwwroot", "Views"]
}
```

#### <a name="exclude"></a>exclude
Type : String ou String[] avec modèle de globbing.

Spécifie les fichiers à exclure de la génération.

Exemple :

```json
{
    "exclude": ["bin/**", "obj/**"]
}
```

#### <a name="includefiles"></a>includeFiles

Type : String ou String[] avec modèle de globbing.

```json
{
    "includeFiles":[]
}
```

#### <a name="excludefiles"></a>excludeFiles

Type : String ou String[] avec modèle de globbing.

```json
{
    "excludeFiles":[]
}
```

#### <a name="builtins"></a>builtIns
Type : object

```json
{
    "builtIns":{}
}
```

#### <a name="mappings"></a>mappages
Type : object

Les clés de l’objet représentent les chemins de destination dans la disposition de la sortie.

Les valeurs sont soit une chaîne, soit un objet représentant le chemin source des fichiers à inclure.  La représentation de l’objet peut avoir ses propres sections `include`, `exclude`, `includeFiles` et `excludeFiles`. 

Exemple de chaîne :

```json
{
    "mappings": {
        "dest/path": "./src/path"
    }
}
```

Exemple d’objet :

```json
{
    "mappings": {
        "dest/path":{
            "include":"./src/path"
        }
    }
}
```

## <a name="analyzeroptions"></a>analyzerOptions
Type : object

Objet avec des propriétés utilisées par les analyseurs de code.

Exemple :

```json
{
    "analyzerOptions": { }
}
```

### <a name="languageid"></a>languageId
Type : chaîne

ID du langage à analyser. « cs » correspond à C#, « vb » correspond à Visual Basic et « fs » correspond à F#.

Exemple :

```json
"analyzerOptions": {
    "languageId": "vb"
}
```

## <a name="configurations"></a>configurations
Type : object

Objet dont les propriétés définissent différentes configurations pour ce projet, par exemple Debug et Release. Chaque valeur est un objet qui peut contenir un objet `buildOptions` avec des options spécifiques pour cette configuration.

Exemple :

```json
"configurations": {
    "Release": {
        "buildOptions": {
            "allowUnsafe": false
        }
    }
}
```

## <a name="frameworks"></a>frameworks
Type : object

Spécifie les frameworks pris en charge par ce projet, tels que .NET Framework ou Universal Windows Platform (UWP). Doit être un moniker valide du Framework cible. Chaque valeur est un objet qui peut contenir des informations spécifiques à ce framework, telles que `buildOptions`, `analyzerOptions`, `dependencies`, ainsi que des propriétés dans les sections suivantes.

Exemple :

```json
"frameworks": {
    "netcoreapp1.0": {
        "buildOptions": {
            "define": ["FOO", "BIZ"]
        }
    }
}
```

### <a name="dependencies"></a>dépendances
Type : object

Dépendances spécifiques à ce framework. Utile dans les scénarios où vous ne pouvez pas spécifier une dépendance au niveau du package sur toutes les cibles. Cela peut être dû au fait qu’une cible ne dispose pas d’une prise en charge intégrée, ou qu’elle nécessite une version de dépendance différente de celle des autres cibles. Pour afficher la liste des autres propriétés de ce nœud, consultez la section [dependencies](#dependencies).

Exemple :

```json
    "frameworks": {
        "netstandard1.5": {
        "dependencies": {
            "Microsoft.Extensions.JsonParser.Sources": "1.0.0-rc2-20221"
        }
    }
}
```

### <a name="frameworkassemblies"></a>frameworkAssemblies
Type : object

Similaire aux dépendances, mais contient des références aux assemblys du GAC qui ne sont pas des packages NuGet. Peut également spécifier la version à utiliser, ainsi que le type de dépendance. Utilisé lorsque vous ciblez des cibles de .NET Framework et de la bibliothèque de classes portables. Vous pouvez uniquement créer un projet avec cet objet spécifié sur Windows.

Exemple :

```json
"frameworks": {
    "net451": {
        "frameworkAssemblies": {
            "System.Runtime": {
                "type": "build",
                "version": "4.0.0"
            }
        }
    }
}
```

### <a name="wrappedproject"></a>wrappedProject
Type : chaîne

Spécifie l’emplacement du projet de dépendance. 

Exemple :

```json
"frameworks": {
    "net451": {
        "wrappedProject": "MyProject.csproj"
    }
}
```

### <a name="bin"></a>bin
Type : object

Utilisé pour encapsuler un fichier DLL. Vous pouvez référencer et générer un package contenant cette DLL. 

Il contient une propriété String, `assembly`, dont la valeur est le chemin de l’assembly.   

Exemple :

```json
"frameworks": {
    "netcoreapp1.0": {
        "bin": {
            "assembly": "c:/otherProject/otherdll.dll"
        }
    }
}
```

## <a name="runtimes"></a>runtimes
Type : object

Liste des [identificateurs de runtime](../rid-catalog.md) pris en charge par le projet (utilisée lors de la publication de [déploiements autonomes](../deploying/index.md#self-contained-deployments-scd)).

Exemple :

```json
"runtimes": {
    "win7-x64": {},
    "win8-x64": {},
    "win81-x64": {},
    "win10-x64": {},
    "osx.10.11-x64": {},
    "ubuntu.16.04-x64": {}
}
```

## <a name="usersecretsid"></a>userSecretsId
Type : chaîne

Spécifie un identificateur de secret utilisateur à utiliser au moment du développement. Pour plus d’informations, consultez [Stockage sécurisé des secrets d’application lors du développement](https://docs.asp.net/en/latest/security/app-secrets.html).

Exemple :

```json
{
    "userSecretsId": "aspnet-WebApp1-c23d27a4-eb88-4b18-9b77-2a93f3b15119"
}
```



<!--HONumber=Nov16_HO3-->


