---
title: Noms d'espaces de noms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], conflicts
- names [.NET Framework], namespaces
- type names, conflicts
- namespaces [.NET Framework], names
- names [.NET Framework], type names
ms.assetid: a49058d2-0276-43a7-9502-04adddf857b2
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4fc0cb9183fde33887a3e84bb30cc3f79892586e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="names-of-namespaces"></a>Noms d'espaces de noms
Comme avec les autres instructions d’affectation de noms, l’objectif lorsque vous nommez des espaces de noms consiste à créer suffisamment claire pour le programmeur immédiatement savoir ce que le contenu de l’espace de noms est susceptible d’être à l’aide de l’infrastructure. Le modèle suivant spécifie la règle générale pour nommer les espaces de noms :  
  
 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`  
  
 Voici quelques exemples :  
  
 `Fabrikam.Math`  
 `Litware.Security`  
  
 **✓ FAIRE** faites précéder les noms d’espace de noms avec un nom de société pour empêcher les espaces de noms provenant de différentes sociétés de ne pas avoir le même nom.  
  
 **✓ FAIRE** utiliser un nom de produit indépendant de la version stable au deuxième niveau d’un espace de noms.  
  
 **X ne sont pas** utiliser des hiérarchies d’organisation comme base pour les noms dans les hiérarchies de l’espace de noms, étant donné que les noms de groupe au sein des entreprises ont tendance à être de courte durée de vie. Organiser la hiérarchie d’espaces de noms autour des groupes des technologies connexes.  
  
 **✓ FAIRE** utilisent la casse Pascal et des composants de l’espace de noms distinct avec des périodes (par exemple, `Microsoft.Office.PowerPoint`). Si votre marque utilise une casse non traditionnel, vous devez suivre la casse définie par votre marque, même s’il diffère de casse de l’espace de noms normal.  
  
 **✓ Envisagez** à l’aide de noms au pluriel, le cas échéant.  
  
 Par exemple, utilisez `System.Collections` au lieu de `System.Collection`. Les marques et les acronymes sont toutefois des exceptions à cette règle. Par exemple, utilisez `System.IO` au lieu de `System.IOs`.  
  
 **X ne sont pas** utiliser le même nom pour un espace de noms et un type dans cet espace de noms.  
  
 Par exemple, n’utilisez pas `Debug` comme un espace de noms nommer et puis fournissent également une classe nommée `Debug` dans le même espace de noms. Plusieurs compilateurs exigent de tels types qualifiés complets.  
  
### <a name="namespaces-and-type-name-conflicts"></a>Espaces de noms et le nom de Type est en conflit  
 **X ne sont pas** présentent des noms de type générique comme `Element`, `Node`, `Log`, et `Message`.  
  
 Il est fort probable que cela entraîne le nom de type est en conflit en commun des scénarios. Vous devez qualifier les noms de type générique (`FormElement`, `XmlNode`, `EventLog`, `SoapMessage`).  
  
 Il existe des recommandations spécifiques pour éviter les conflits de nom de type pour différentes catégories d’espaces de noms.  
  
-   **Noms de modèle d’application**  
  
     Espaces de noms appartenant à un modèle d’application unique sont très souvent utilisés ensemble, mais ils sont presque jamais avec les espaces de noms des autres modèles d’application. Par exemple, le <xref:System.Windows.Forms?displayProperty=nameWithType> espace de noms est très rarement utilisée conjointement avec la <xref:System.Web.UI?displayProperty=nameWithType> espace de noms. Voici une liste connue modèle espace de noms de groupes d’applications :  
  
     `System.Windows*`   
     `System.Web.UI*`  
  
     **X ne sont pas** donner le même nom aux types dans les espaces de noms dans un modèle d’application unique.  
  
     Par exemple, n’ajoutez pas d’un type nommé `Page` à la <xref:System.Web.UI.Adapters?displayProperty=nameWithType> espace de noms, étant donné que la <xref:System.Web.UI?displayProperty=nameWithType> espace de noms contient déjà un type nommé `Page`.  
  
-   **Espaces de noms infrastructure**  
  
     Ce groupe contient des espaces de noms qui sont rarement importés pendant le développement d’applications courantes. Par exemple, `.Design` espaces de noms sont utilisés principalement lorsque les outils de développement de programmation. Éviter les conflits avec les types dans ces espaces de noms n’est pas critique.  
  
-   **Espaces de noms principaux**  
  
     Espaces de noms principaux incluent tous les `System` espaces de noms, à l’exclusion des espaces de noms des modèles d’application et les espaces de noms d’Infrastructure. Espaces de noms principaux incluent, entre autres, `System`, `System.IO`, `System.Xml`, et `System.Net`.  
  
     **X ne sont pas** permettent de types de noms qui sont en conflit avec un type dans les espaces de noms de base.  
  
     Par exemple, n’utilisez jamais `Stream` comme nom de type. Elle serait en conflit avec <xref:System.IO.Stream?displayProperty=nameWithType>, une très courants de type.  
  
-   **Groupes d’espace de noms de technologie**  
  
     Cette catégorie comprend tous les espaces de noms avec les deux premiers nœuds d’espace de noms même `(<Company>.<Technology>*`), tel que `Microsoft.Build.Utilities` et `Microsoft.Build.Tasks`. Il est important que les types appartenant à une technologie unique ne sont pas en conflit entre eux.  
  
     **X ne sont pas** affecter des noms de type qui sont en conflit avec d’autres types au sein d’une seule technologie.  
  
     **X ne sont pas** présentent des conflits de nom de type entre les types dans les espaces de noms de technologie et un espace de noms de modèle d’application (à moins que la technologie n’est pas destinée à être utilisée avec le modèle d’application).  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi  
 [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)  
 [Affectation de noms](../../../docs/standard/design-guidelines/naming-guidelines.md)
