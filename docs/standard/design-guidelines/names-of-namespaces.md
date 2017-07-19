---
title: "Noms d’espaces de noms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "noms (.NET Framework), les conflits"
  - "noms d’espaces de noms [.NET Framework]"
  - "noms de types, les conflits"
  - "espaces de noms (.NET Framework), noms"
  - "noms (.NET Framework), noms de types"
ms.assetid: a49058d2-0276-43a7-9502-04adddf857b2
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# Noms d’espaces de noms
Comme avec les autres instructions d’affectation de noms, l’objectif lorsque vous nommez des espaces de noms consiste à créer suffisamment claire pour le programmeur immédiatement savoir ce que le contenu de l’espace de noms est susceptible d’être à l’aide de l’infrastructure. Le modèle suivant spécifie la règle générale pour les noms des espaces de noms :  
  
 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`  
  
 Voici quelques exemples :  
  
 `Fabrikam.Math`   
 `Litware.Security`  
  
 **✓ faire** préfixe d’espace de noms avec un nom de société pour éviter les espaces de noms provenant de différentes sociétés d’avoir le même nom.  
  
 **✓ faire** utiliser un nom de produit indépendant de la version stable au deuxième niveau de l’espace de noms.  
  
 **X ne pas** utiliser des hiérarchies d’organisation comme base pour les noms de hiérarchies d’espace de noms, étant donné que les noms de groupes au sein d’entreprises ont tendance à changer. Organiser la hiérarchie d’espaces de noms autour des groupes des technologies connexes.  
  
 **✓ faire** utiliser la casse Pascal et des composants de l’espace de noms séparé par des points \(par exemple, `Microsoft.Office.PowerPoint`\). Si votre marque utilise une casse non traditionnel, vous devez suivre la casse définie par votre marque, même s’il diffère de casse de l’espace de noms normale.  
  
 **✓ envisagez** à l’aide de noms au pluriel, le cas échéant.  
  
 Par exemple, utilisez `System.Collections` au lieu de `System.Collection`. Marques et les acronymes sont toutefois des exceptions à cette règle. Par exemple, utilisez `System.IO` au lieu de `System.IOs`.  
  
 **X ne pas** utiliser le même nom pour un espace de noms et un type dans cet espace de noms.  
  
 Par exemple, n’utilisez pas `Debug` comme un espace de noms nom et ensuite fournir également une classe nommée `Debug` dans le même espace de noms. Plusieurs compilateurs exigent que ces types soient complets.  
  
### Espaces de noms et les conflits de nom de Type  
 **X ne pas** introduisent des noms de type générique comme `Element`, `Node`, `Log`, et `Message`.  
  
 Il est fort probable que cela permettra au nom de type est en conflit en commun des scénarios. Vous devez qualifier les noms de type générique \(`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`\).  
  
 Il existe des recommandations spécifiques pour éviter les conflits de nom de type pour différentes catégories d’espaces de noms.  
  
-   **Noms de modèle d’application**  
  
     Espaces de noms appartenant à un même modèle d’application sont très souvent utilisés ensemble, mais ils sont presque jamais avec les espaces de noms des autres modèles d’application. Par exemple, le <xref:System.Windows.Forms?displayProperty=fullName> espace de noms est très rarement utilisée conjointement avec la <xref:System.Web.UI?displayProperty=fullName> espace de noms. Voici une liste de groupes d’espace de noms connu application modèle :  
  
     `System.Windows*`   
     `System.Web.UI*`  
  
     **X ne pas** attribuer le même nom aux types dans les espaces de noms dans un modèle d’application unique.  
  
     Par exemple, n’ajoutez pas un type nommé `Page` à la <xref:System.Web.UI.Adapters?displayProperty=fullName> espace de noms, car le <xref:System.Web.UI?displayProperty=fullName> espace de noms contient déjà un type nommé `Page`.  
  
-   **Espaces de noms infrastructure**  
  
     Ce groupe contient des espaces de noms qui sont rarement importés au cours du développement des applications courantes. Par exemple, `.Design` espaces de noms sont principalement utilisés lors des outils de développement de programmation. Éviter les conflits avec les types dans ces espaces de noms n’est pas critique.  
  
-   **Espaces de noms principaux**  
  
     Espaces de noms principaux incluent tous `System` espaces de noms, à l’exclusion des espaces de noms des modèles d’application et les espaces de noms d’Infrastructure. Espaces de noms principaux incluent, entre autres, `System`, `System.IO`, `System.Xml`, et `System.Net`.  
  
     **X ne pas** donnent types de noms qui seraient en conflit avec un type dans les espaces de noms principaux.  
  
     Par exemple, n’utilisez jamais `Stream` comme nom de type. Elle serait en conflit avec <xref:System.IO.Stream?displayProperty=fullName>, un très couramment utilisés type.  
  
-   **Groupes d’espace de noms de technologies**  
  
     Cette catégorie comprend tous les espaces de noms avec les deux premiers nœuds d’espace de noms même `(<Company>.<Technology>*`\), tel que `Microsoft.Build.Utilities` et `Microsoft.Build.Tasks`. Il est important que types appartenant à une seule technologie n’entrent pas en conflit entre eux.  
  
     **X ne pas** affecter des noms de types qui entrent en conflit avec d’autres types au sein d’une seule technologie.  
  
     **X ne pas** introduire des conflits de nom de type entre les types dans les espaces de noms de technologie et un espace de noms de modèle d’application \(à moins que la technologie n’est pas destinée à être utilisée avec le modèle d’application\).  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [Framework Design Guidelines : Conventions, langages et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison\-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## Voir aussi  
 [Instructions de conception d’infrastructure](../../../docs/standard/design-guidelines/index.md)   
 [Indications concernant l'attribution d'un nom](../../../docs/standard/design-guidelines/naming-guidelines.md)