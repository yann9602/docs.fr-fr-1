---
title: "Regrouper des résultats par clés contiguës"
description: "Comment regrouper des résultats par clés contiguës."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: cbda9c08-151b-4c9e-82f7-c3d7f3dac66b
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f49b0e0dac7df20fc6e5015b9707208ee65a48d6
ms.lasthandoff: 03/13/2017

---
# <a name="group-results-by-contiguous-keys"></a>Regrouper des résultats par clés contiguës

L’exemple suivant montre comment regrouper des éléments dans des blocs représentant des sous-séquences de clés contiguës. Par exemple, supposons que vous disposiez de la séquence de paires clé-valeur suivante :  
  
|Clé|Valeur|  
|---------|-----------|  
|A|Nous|  
|A|pensons|  
|A|que|  
|B|Linq|  
|C|est|  
|A|vraiment|  
|B|chouette|  
|B|!|  
  
 Les groupes suivants seront créés dans cet ordre :  
  
1.  Nous, pensons, que  
  
2.  Linq  
  
3.  est  
  
4.  vraiment  
  
5.  chouette, !  
  
 La solution est implémentée comme une méthode d’extension thread-safe qui retourne ses résultats en continu. En d’autres termes, elle produit ses groupes à mesure qu’elle se déplace dans la séquence source. Contrairement aux opérateurs `group` ou `orderby`, elle peut commencer à retourner des groupes à l’appelant avant que l’intégralité de la séquence ait été lue.  
  
 La cohérence de thread est obtenue en effectuant une copie de chaque groupe ou bloc pendant l’itération de la séquence source, comme expliqué dans les commentaires du code source. Si la séquence source comporte une longue séquence d’éléments contigus, le common language runtime peut lever une exception <xref:System.OutOfMemoryException>.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre la méthode d’extension et le code client qui l’utilise.  
  
 [!code-cs[cscsrefContiguousGroups#1](../../../samples/snippets/csharp/concepts/linq/how-to-group-results-by-contiguous-keys_1.cs)]  
  
 Pour utiliser la méthode d’extension dans votre projet, copiez la classe statique `MyExtensions` dans un fichier de code source nouveau ou existant et, si nécessaire, ajoutez une directive `using` pour l’espace de noms dans lequel elle se trouve.  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions de requête LINQ](index.md)   
 
