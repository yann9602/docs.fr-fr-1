---
title: "Créer un groupe imbriqué"
description: "Indique comment créer un groupe imbriqué."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.openlocfilehash: 232aa46d975d7c338bbc776e3867f2e566601fde
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="create-a-nested-group"></a>Créer un groupe imbriqué

L’exemple suivant montre comment créer des groupes imbriqués dans une expression de requête LINQ. Chaque groupe créé en fonction de l’année/du niveau d’étude est ensuite encore subdivisé en groupes en fonction des noms des individus.  
  
## <a name="example"></a>Exemple

 > [!NOTE]
 > Cet exemple contient des références aux objets définis dans l’exemple de code qui est présenté dans [Interroger une collection d’objets](query-a-collection-of-objects.md). 

 [!code-csharp[csProgGuideLINQ#24](../../../samples/snippets/csharp/concepts/linq/how-to-create-a-nested-group_1.cs)]  
  
 Notez que trois boucles `foreach` imbriquées sont nécessaires pour effectuer une itération sur les éléments internes d’un groupe imbriqué.  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions de requête LINQ](index.md)
