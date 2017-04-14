---
title: "Common Language Runtime (CLR) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".NET Framework, Common Language Runtime"
  - "code, exécution"
  - "code, fonctionnalités runtime"
  - "Common Language Runtime"
  - "compiler le code source, fonctionnalités runtime"
  - "compilateurs de langages"
  - "code managé"
  - "données managées"
  - "métadonnées, fonctionnalités runtime"
  - "runtime"
  - "code source (exécution)"
ms.assetid: 059a624e-f7db-4134-ba9f-08b676050482
caps.latest.revision: 24
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 18
---
# Common Language Runtime (CLR)
Le .NET Framework fournit un environnement d'exécution, appelé le Common Language Runtime, qui exécute le code et offre des services qui simplifient le processus de développement.  
  
 Les compilateurs et les outils exposent le fonctionnement du Common Language Runtime et vous permettent d'écrire du code qui bénéficie de cet environnement d'exécution managée.  Le code que vous développez à l'aide d'un compilateur de langage ciblant le runtime est appelé code managé ; il tire parti de fonctionnalités telles que l'intégration interlangage, la gestion interlangage des exceptions, la sécurité améliorée, la prise en charge du versioning et du déploiement, un modèle simplifié de l'interaction des composants, ainsi que des services de débogage et de gestion de profils.  
  
> [!WARNING]
>  Les compilateurs et les outils peuvent générer une sortie que le Common Language Runtime peut consommer parce que le système de type, le format des métadonnées et l'environnement d'exécution \(système d'exécution virtuel\) sont tous définis par une norme publique, la spécification CLI \(Common Language Infrastructure\) ECMA.  Pour plus d'informations, voir [Spécifications CLI \(Common Language Infrastructure\) et C\# ECMA](http://go.microsoft.com/fwlink/?LinkId=99212).  
  
 Pour permettre au runtime de fournir des services au code managé, les compilateurs de langage doivent générer des métadonnées qui décrivent les types, les membres et les références de votre code.  Les métadonnées sont stockées avec le code ; chaque fichier exécutable portable \(PE\) chargeable du Common Language Runtime contient des métadonnées.  Le runtime utilise les métadonnées pour rechercher et charger des classes, placer des instances en mémoire, résoudre des appels de méthode, générer un code natif, appliquer la sécurité et définir les limites du contexte d'exécution.  
  
 Le runtime gère automatiquement la disposition des objets et manage les références aux objets, les libérant quand ils ne sont plus utilisés.  Les objets dont la durée de vie est managée de cette façon sont appelés données managées.  Le garbage collection élimine les fuites de mémoire ainsi que d'autres erreurs de programmation courantes.  Si votre code est managé, vous pouvez utiliser des données managées, des données non managées, ou à la fois des données managées et non managées dans votre application .NET Framework.  Dans la mesure où les compilateurs de langage fournissent leurs propres types, tels que des types primitifs, vous ne pouvez pas toujours savoir \(ou avoir besoin de savoir\) si vos données sont managées.  
  
 Le Common Language Runtime facilite la conception de composants et d'applications dont les objets interagissent entre les langages.  Les objets écrits dans des langages différents peuvent communiquer les uns avec les autres, et leurs comportements peuvent être fortement intégrés.  Par exemple, vous pouvez définir une classe puis utiliser un langage différent pour dériver une classe de votre classe d'origine ou appeler une méthode pour la classe d'origine.  Vous pouvez également passer une instance d'une classe à une méthode d'une classe écrite dans un autre langage.  Cette intégration interlangage n'est possible que parce que les outils et les compilateurs de langage ciblant le runtime utilisent un système de type commun défini par le runtime, et qu'ils suivent les règles établies par le runtime en matière de définition de nouveaux types, ainsi que de création, d'utilisation, de persistance de types et de liaison avec ceux\-ci.  
  
 Au sein de leurs métadonnées, tous les composants managés comportent des informations relatives aux composants et aux ressources pour lesquels ils ont été générés.  Le runtime exploite ces informations pour s'assurer que votre composant ou application possède les versions spécifiées de tous les éléments dont il a besoin, ce qui rend votre code moins enclin aux arrêts provoqués par une dépendance sans correspondance.  Les informations d'inscription et les données d'état ne sont plus stockées dans le Registre où il peut être difficile de les implanter et de les gérer.  Au lieu de cela, les informations relatives aux types que vous définissez \(et leurs dépendances\) sont stockées avec le code en tant que métadonnées, rendant les tâches de réplication et de suppression de composants beaucoup moins compliquées.  
  
 Les outils et les compilateurs de langage exposent le fonctionnement du runtime selon des modes qui se veulent utiles et intuitifs pour les développeurs.  Cela signifie que certaines fonctionnalités du runtime peuvent se faire remarquer davantage dans un environnement que dans un autre.  Les fonctionnalités du runtime dépend des compilateurs de langage ou des outils utilisés.  Par exemple, si vous êtes un développeur Visual Basic, vous pouvez remarquer qu'avec le Common Language Runtime, le langage Visual Basic dispose davantage de fonctionnalités orientées objet qu'avant.  Le runtime fournit les avantages suivants :  
  
-   Amélioration des performances.  
  
-   Possibilité d'utiliser facilement des composants développés dans d'autres langages.  
  
-   Types extensibles fournis par une bibliothèque de classes.  
  
-   Fonctionnalités de langage telles que l'héritage, les interfaces et la surcharge pour la programmation orientée objet.  
  
-   Prise en charge du modèle de thread libre explicite qui permet la création d'applications évolutives multithread.  
  
-   Prise en charge de la gestion structurée des exceptions.  
  
-   Prise en charge des attributs personnalisés.  
  
-   Garbage collection.  
  
-   Utilisation des délégués plutôt que des pointeurs fonction pour une sécurité de type et une sécurité accrues.  Pour plus d'informations sur les délégués, consultez [Système de type commun](../../docs/standard/base-types/common-type-system.md).  
  
## Versions du Common Language Runtime  
 Le numéro de version du .NET Framework ne correspond pas nécessairement au numéro de version du CLR qu'il contient.  Le tableau suivant illustre la corrélation entre les deux numéros de version.  
  
|Version du .NET Framework|Inclut la version CLR|  
|-------------------------------|---------------------------|  
|1.0|1.0|  
|1.1|1.1|  
|2.0|2.0|  
|3.0|2.0|  
|3.5|2.0|  
|4|4|  
|4.5 \(y compris 4.5.1 et 4.5.2\)|4|  
  
## Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Processus d'exécution managée](../../docs/standard/managed-execution-process.md)|Décrit les étapes nécessaires pour tirer parti du Common Language Runtime.|  
|[Gestion automatique de la mémoire](../../docs/standard/automatic-memory-management.md)|Explique comment le « garbage collector » alloue et libère la mémoire.|  
|[NIB: Overview of the .NET Framework](http://msdn.microsoft.com/fr-fr/ea38ac1e-92af-4d1b-8db1-e8a5ea10ed85)|Décrit les concepts fondamentaux du .NET Framework, tels que le système de type commun \(CTS, Common Type System\), l'interopérabilité interlangage, l'exécution managée, les domaines d'application et les assemblys.|  
|[Système de type commun](../../docs/standard/base-types/common-type-system.md)|Décrit la manière dont les types sont déclarés, utilisés et managés dans le runtime à l'appui de l'intégration interlangage.|  
  
## Voir aussi  
 [Versions et dépendances](../../docs/framework/migration-guide/versions-and-dependencies.md)