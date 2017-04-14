---
title: Fournisseurs de type
description: Fournisseurs de type
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 25697ef6-465e-4248-9de5-1d199d4a8b59
translationtype: Human Translation
ms.sourcegitcommit: 0a01ec92a90d99fafaacbd3f71f5177e5cf94a68
ms.openlocfilehash: e9e67e6531e0c1daad0c0d4a9f778670d5cb2263
ms.lasthandoff: 04/05/2017

---

# <a name="type-providers"></a>Fournisseurs de type

> [!NOTE]
Ce guide, basé sur F# 3.0, va être mis à jour.  Pour obtenir la liste la plus récente des fournisseurs de type multiplateformes, consultez [FSharp.Data](http://fsharp.github.io/FSharp.Data/).

Un fournisseur de type F# est un composant qui fournit des types, des propriétés et des méthodes à utiliser dans votre programme. Dans F# 3.0, les fournisseurs de type représentent sont une part importante de la prise en charge de la programmation riche en informations. L'objectif de la programmation riche en informations est de supprimer les obstacles à l'utilisation de diverses sources d'informations provenant d'Internet et présentes dans les environnements d'entreprises modernes. Un des obstacles significatifs réside dans le fait que pour inclure une source d'informations dans un programme, ces dernières doivent être représentées en tant que types, propriétés et méthodes. Ainsi, elles pourront être utilisées dans un environnement de langage de programmation. Écrire ces types manuellement est très long et difficile à gérer. Une alternative courante consiste à utiliser un générateur de code qui ajoute des fichiers au projet ; toutefois, les types classiques de génération du code ne s'intègrent pas correctement dans des modes exploratoires de programmation pris en charge par F#, étant donné que le code généré doit être remplacé chaque fois qu'une référence de service est définie.

Les types fournis par les fournisseurs de type F# sont généralement basés sur des sources d'informations externes. Par exemple, un fournisseur de type F# pour SQL fournit les types, les propriétés, les méthodes dont vous avez besoin pour travailler directement avec les tables de toute base de données SQL à laquelle vous avez accès. De même, un fournisseur de type pour les services Web WSDL fournit les types, les propriétés, les méthodes dont vous avez besoin pour travailler directement avec n'importe quel service Web WSDL.

L'ensemble de types, propriétés et méthodes fourni par un fournisseur de type F# peut dépendre des paramètres définis dans le code du programme. Par exemple, un fournisseur de type peut fournir des types différents selon une chaîne de connexion ou une URL de service. De cette façon, l'espace d'informations disponible par le biais d'une chaîne de connexion ou d'une URL est directement intégré à votre programme. Un fournisseur de type garantit également que le développement des groupes de types s'effectue uniquement à la demande ; autrement dit, ils sont développés si les types sont réellement référencés par votre programme. Cela permet l'intégration directe et à la demande d'espaces d'informations à grande échelle, tels que les marchés de données en ligne, de manière fortement typée.

F# contient plusieurs fournisseurs de type intégrés pour les services de données Internet et d'entreprise couramment utilisés. Ces fournisseurs de type offrent un accès simple et régulier aux bases de données relationnelles SQL et aux services basés sur le réseau OData et WSDL. Ils prennent également en charge l'utilisation des requêtes LINQ F# sur ces sources de données.

En cas de besoin, vous pouvez créer votre propre fournisseur de type personnalisé, ou référencer des fournisseurs de type créés par d'autres. Par exemple, supposez que votre organisation dispose d'un service de données fournissant un nombre important et croissant de jeux de données nommées, chacun avec son propre schéma stable de données. Vous pouvez choisir de créer un fournisseur de type qui lit les schémas et présente les derniers groupes de données disponibles au programmeur de manière fortement typée.


## <a name="related-topics"></a>Rubriques connexes


|Titre|Description|
|-----|-----------|
|[Procédure pas à pas : accès à une base de données SQL à l’aide des fournisseurs de type](accessing-a-sql-database.md)|Explique comment utiliser le fournisseur de type SqlDataConnection pour accéder aux tables et aux procédures stockées d’une base de données SQL en fonction d’une chaîne de connexion pour une connexion directe à une base de données. L'accès utilise un mappage LINQ to SQL.|
|[Procédure pas à pas : accès à une base de données SQL à l’aide des fournisseurs de type et des entités](accessing-a-sql-database-entities.md)|Explique comment utiliser le fournisseur de type SqlEntityConnection pour accéder aux tables et aux procédures stockées d’une base de données SQL en fonction d’une chaîne de connexion pour une connexion directe à une base de données. L'accès utilise un mappage LINQ to Entities. Cette méthode fonctionne avec n'importe quelle base de données (SQL Server est utilisé dans cet exemple).|
|[Procédure pas à pas : accès à un service OData à l’aide des fournisseurs de type](accessing-an-odata-service.md)|Explique comment utiliser le fournisseur de type ODataService pour accéder à un service OData d’une manière fortement typée, en fonction d’une URL de service.|
|[Procédure pas à pas : accès à un service web à l’aide des fournisseurs de type](accessing-a-web-service.md)|Explique comment utiliser le fournisseur de type WsdlService pour accéder à un service Web WSDL d’une manière fortement typée, en fonction d’une URL de service.|
|[Procédure pas à pas : génération de types F&#35; à partir d’un fichier DBML](generating-fsharp-types-from-dbml.md)|Explique comment utiliser le fournisseur de type DbmlFile pour accéder aux tables et aux procédures stockées d’une base de données SQL, en fonction d’un fichier DBML donnant une spécification de schéma de base de données LINQ to SQL.|
|[Procédure pas à pas : génération de types F&#35; à partir d’un fichier de schéma EDMX](generating-fsharp-types-from-edmx.md)|Explique comment utiliser le fournisseur de type EdmxFile pour accéder aux tables et aux procédures stockées d’une base de données SQL, en fonction d’un fichier EDMX donnant une spécification de schéma Entity Framework.|
|[Didacticiel : création d’un fournisseur de type](creating-a-type-provider.md)|Fournit des informations sur l’écriture de vos propres fournisseurs de type personnalisés.|
|[Sécurité du fournisseur de type](type-provider-security.md)|Fournit des informations sur les exigences en matière de sécurité lors du développement de fournisseurs de type.|
|[Résolution des problèmes liés aux fournisseurs de type](troubleshooting-type-providers.md)|Fournit des informations sur les problèmes courants qui peuvent survenir lors de l’utilisation des fournisseurs de type et inclut des suggestions de résolution.|

## <a name="see-also"></a>Voir aussi
[Informations de référence du langage F#](../../language-reference/index.md)

[Visual F#](../../index.md)
