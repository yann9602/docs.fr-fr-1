---
title: "Créer un groupe imbriqué"
description: "Indique comment créer un groupe imbriqué."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 361ac1f224c6eef292fcf8434c7e465c9448b19c
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

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

