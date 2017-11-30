---
title: "Collections génériques dans le .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- generics [.NET Framework], collections
- generic collections [.NET Framework]
ms.assetid: 5b646751-6ab7-465c-916c-b1a76aefa9f5
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 94da20072f793e137b0b7545c1a658ed20537a7f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="generic-collections-in-the-net-framework"></a>Collections génériques dans le .NET Framework
Cette rubrique donne une vue d'ensemble des classes de collections génériques et d'autres types génériques dans le .NET Framework.  
  
## <a name="generic-collections-in-the-net-framework"></a>Collections génériques dans le .NET Framework  
 Le .NET Framework fournit plusieurs classes de collection génériques dans les espaces de noms <xref:System.Collections.Generic> et <xref:System.Collections.ObjectModel>. Pour plus d’informations sur ces classes, consultez [utilisé Types de collections couramment](../../../docs/standard/collections/commonly-used-collection-types.md).  
  
### <a name="systemcollectionsgeneric"></a>System.Collections.Generic  
 La plupart des types de collections génériques sont des équivalents directs de types non génériques. <xref:System.Collections.Generic.Dictionary%602> est une version générique de <xref:System.Collections.Hashtable> ; elle utilise la structure générique <xref:System.Collections.Generic.KeyValuePair%602> pour l'énumération, au lieu de <xref:System.Collections.DictionaryEntry>.  
  
 <xref:System.Collections.Generic.List%601> est une version générique de <xref:System.Collections.ArrayList>. Il existe des classes génériques <xref:System.Collections.Generic.Queue%601> et <xref:System.Collections.Generic.Stack%601> qui correspondent aux versions non génériques.  
  
 Il existe des versions génériques et non génériques de <xref:System.Collections.Generic.SortedList%602>. Les deux versions sont des hybrides d'un dictionnaire et une liste. La classe générique <xref:System.Collections.Generic.SortedDictionary%602> est un dictionnaire pur et n'a pas de contrepartie non générique.  
  
 La classe générique <xref:System.Collections.Generic.LinkedList%601> est une véritable liste liée. Il n'a pas de contrepartie non générique.  
  
### <a name="systemcollectionsobjectmodel"></a>System.Collections.ObjectModel  
 La classe générique <xref:System.Collections.ObjectModel.Collection%601> fournit une classe de base pour dériver vos propres types de collections génériques. La classe <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> offre un moyen facile de produire une collection en lecture seule à partir de n'importe quel type implémentant l'interface générique <xref:System.Collections.Generic.IList%601>. La classe générique <xref:System.Collections.ObjectModel.KeyedCollection%602> fournit un moyen de stocker des objets qui contiennent leurs propres clés.  
  
## <a name="other-generic-types"></a>Autres types génériques  
 La structure générique <xref:System.Nullable%601> vous permet d'utiliser des types valeur comme si la valeur `null` pouvait leur être affectée. Ceci peut être utile quand vous travaillez avec des requêtes de base de données, où des champs contenant des types valeur peuvent être manquants. Le paramètre de type générique peut être n'importe quel type valeur.  
  
> [!NOTE]
>  En C#, il n'est pas nécessaire d'utiliser <xref:System.Nullable%601> explicitement, car le langage a une syntaxe pour les types Nullable.  
  
 La structure générique <xref:System.ArraySegment%601> offre un moyen de délimiter une plage d'éléments dans un tableau unidimensionnel de base zéro, de n'importe quel type. Le paramètre de type générique est le type des éléments du tableau.  
  
 Le délégué générique <xref:System.EventHandler%601> élimine le besoin de déclarer un type de délégué pour gérer les événements, si votre événement respecte le modèle de gestion des événements utilisé par le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Par exemple, supposons que vous avez créé une classe `MyEventArgs` dérivée de <xref:System.EventArgs>, pour stocker les données de votre événement. Vous pouvez ensuite déclarer l'événement comme suit :  
  
 [!code-cpp[Conceptual.Generics.Overview#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.generics.overview/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Generics.Overview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.generics.overview/cs/source2.cs#7)]
 [!code-vb[Conceptual.Generics.Overview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.generics.overview/vb/source2.vb#7)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
 <xref:System.Collections.ObjectModel?displayProperty=nameWithType>  
 [Génériques](../../../docs/standard/generics/index.md)  
 [Délégués génériques pour la manipulation de tableaux et de listes](../../../docs/standard/generics/delegates-for-manipulating-arrays-and-lists.md)  
 [Interfaces génériques](../../../docs/standard/generics/interfaces.md)
