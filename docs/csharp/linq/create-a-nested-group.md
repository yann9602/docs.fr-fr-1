---
title: "Créer un groupe imbriqué"
description: "Indique comment créer un groupe imbriqué."
keywords: .NET, .NET Core, C#
author: stevehoag
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ff2c0c00ab23346cbaa3ba7c36a0cba25e03b89b
ms.lasthandoff: 03/13/2017

---
# <a name="create-a-nested-group"></a>Créer un groupe imbriqué

L’exemple suivant montre comment créer des groupes imbriqués dans une expression de requête LINQ. Chaque groupe créé en fonction de l’année/du niveau d’étude est ensuite encore subdivisé en groupes en fonction des noms des individus.  
  
## <a name="example"></a>Exemple

 > [!NOTE]
 > Cet exemple contient des références aux objets définis dans l’exemple de code présenté dans [Interroger une collection d’objets](query-a-collection-of-objects.md). 

 [!code-cs[csProgGuideLINQ#24](../../../samples/snippets/csharp/concepts/linq/how-to-create-a-nested-group_1.cs)]  
  
 Notez que trois boucles `foreach` imbriquées sont nécessaires pour effectuer une itération sur les éléments internes d’un groupe imbriqué.  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions de requête LINQ](index.md)
