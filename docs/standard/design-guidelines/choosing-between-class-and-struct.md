---
title: "Choix entre les classes et structs | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "indications de conception de bibliothèques de classes (.NET Framework), structures"
  - "indications de conception de bibliothèques de classes (.NET Framework), classes"
  - "structures (.NET Framework), par rapport aux classes"
  - "classes (.NET Framework), les règles de conception"
  - "Tapez les instructions de conception, structures"
  - "structures (.NET Framework), les règles de conception"
  - "classes (.NET Framework), par rapport à des structures"
  - "conception de type, classes"
ms.assetid: f8b8ec9b-0ba7-4dea-aadf-a93395cd804f
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# Choix entre les classes et structs
Une des décisions de conception de base qu'est confronté à chaque concepteur framework consiste à concevoir un type comme une classe \(type référence\) ou comme une structure \(type valeur\). Bien comprendre les différences de comportement entre les types référence et les types valeur est vitale pour rendre ce choix.  
  
 La différence entre les types référence et les types valeur que nous allons étudier le premier est que les types référence sont alloués sur le tas et garbage collection, tandis que les types valeur sont alloués sur la pile ou inline dans contenant des types et libérés lorsque la pile se déroule ou lorsque leur type contenant est libéré. Par conséquent, les allocations et désallocations de types valeur sont en général moins cher que les allocations et désallocations de types référence.  
  
 Ensuite, les tableaux de référence sont des types allouée hors ligne, ce qui signifie que le tableau d’éléments sont simplement les références aux instances du type de référence qui résident sur le tas. Les tableaux de types valeur sont alloués inline, ce qui signifie que les éléments du tableau sont les instances du type valeur réelles. Par conséquent, les allocations et désallocations de tableaux de types valeur sont beaucoup moins chers que les allocations et désallocations de tableaux de type référence. En outre, dans la majorité des cas de tableaux de type valeur présentent bien une meilleure localité de référence.  
  
 La différence suivante est liée à l’utilisation de la mémoire. Types valeur inclus lors de la conversion vers un type référence ou d’une des interfaces qu’ils implémentent. Ils obtiennent unboxed lors de la conversion vers le type de valeur. Étant donné que les zones sont des objets alloués sur le tas et le garbage collector, trop boxing et unboxing peut avoir un impact négatif sur le tas, le garbage collector et finalement les performances de l’application.  En revanche, pas de boxing se produit comme types référence sont convertis.  
  
 Ensuite, les affectations de type référence copier la référence, tandis que les affectations de type valeur copiez la valeur entière. Par conséquent, les affectations de types de référence de grande taille sont moins chères que les affectations de types de valeur volumineux.  
  
 Enfin, les types référence sont passés par référence, tandis que les types valeur sont passés par valeur. Modifications apportées à une instance d’un type référence affectent toutes les références pointant vers l’instance. Instances de types valeur sont copiés lorsqu’ils sont passés par valeur. Lorsqu’une instance d’un type valeur est modifiée, elle évidemment n’affecte pas un de ses copies. Étant donné que les copies ne sont pas explicitement créés par l’utilisateur mais sont créées implicitement lorsque les arguments sont transmis ou retournent les valeurs sont retournées, types valeur qui peuvent être modifiés peuvent prêter à confus pour de nombreux utilisateurs. Par conséquent, les types valeur doivent être immuables.  
  
 En règle générale, la plupart des types dans une infrastructure doit être des classes. Toutefois, il existe certaines situations dans lesquelles les caractéristiques d’un type valeur rendent plus appropriées utiliser les structures.  
  
 **✓ envisagez** définition d’un struct au lieu d’une classe si les instances du type sont petits et couramment gratuitement ou sont fréquemment incorporées dans d’autres objets.  
  
 **X éviter** définition d’un struct, sauf si le type possède toutes les caractéristiques suivantes :  
  
-   Il représente logiquement une seule valeur, semblable aux types primitifs \(`int`, `double`, etc..\).  
  
-   Il a une taille d’instance inférieure à 16 octets.  
  
-   Il est immuable.  
  
-   Il n’aura pas être boxed fréquemment.  
  
 Dans tous les autres cas, vous devez définir vos types en tant que classes.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Conception de type](../../../docs/standard/design-guidelines/type.md)   
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)