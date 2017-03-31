---
title: "Effectuer une sous-requête sur une opération de regroupement"
description: "Guide pratique pour effectuer une sous-requête sur une opération de regroupement."
keywords: .NET, .NET Core, C#
author: stevehoag
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: d75a588e-9b6f-4f37-b195-f99ec8503855
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 7c2c95479db10d81e748349e156f2314a6d4fccf
ms.lasthandoff: 03/13/2017

---
# <a name="perform-a-subquery-on-a-grouping-operation"></a>Effectuer une sous-requête sur une opération de regroupement

Cette rubrique présente deux façons de créer une requête qui organise les données sources en groupes et effectue ensuite une sous-requête sur chacun de ces groupes. Dans chaque exemple, la technique de base consiste à regrouper les éléments sources en utilisant une *continuation* nommée `newGroup`, puis en créant une sous-requête sur `newGroup`. Cette sous-requête est exécutée sur chaque groupe créé par la requête externe. Notez que, dans cet exemple particulier, le résultat final n’est pas un groupe, mais une séquence plate de types anonymes.  
  
 Pour plus d’informations sur les regroupements, consultez [group, clause](../language-reference/keywords/group-clause.md).  
  
 Pour plus d’informations sur les continuations, consultez [into](../language-reference/keywords/into.md). L’exemple suivant utilise une structure de données en mémoire comme source de données, mais les mêmes principes s’appliquent à tous les types de sources de données LINQ.  
  
## <a name="example"></a>Exemple 

 > [!NOTE]
 > Cet exemple contient des références aux objets définis dans l’exemple de code qui est présenté dans [Interroger une collection d’objets](query-a-collection-of-objects.md).

 [!code-cs[csProgGuideLINQ#23](../../../samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_1.cs)]  
   
## <a name="see-also"></a>Voir aussi  
 [Expressions de requête LINQ](index.md)
